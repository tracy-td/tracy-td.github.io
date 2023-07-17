# Testes unitários com Mock para as classes de serviços.

Serão demonstradas neste guia de teste, as 4 funções de um CRUD e exceção, para que assim, seja possível que se tenha
uma ideia básica de como continuar com a implementação de testes.

Um teste é composto por 3 fases: Preparação, Execução e Validação.

 * Preparação: nessa etapa é criado todos os argumentos necessários e configurações para que o teste possa representar o mais próximo do cenário real;
* Execução: aqui onde se utiliza os argumentos produzidos na preparação e executamos o metodo do serviço a qual queremos testar;
* Validação: a fase mais importante de um teste, onde ocorre todas as verificações da execução do teste e se ocorreu como esperado;

Para testarmos um serviço, vamos começar criando a classe de teste, caso a classe de teste não exista.
A nomenclatura da classe de teste deve seguir um padrão <mark>"{nome da classe do serviço}" + "Test"</mark>,
por exemplo: <mark>"TechnicalDebtServiceTest"</mark>.  
O local em que esse arquivo deve está é no path do projeto em <mark>"src/test/java/org/{nome_do_projeto}"</mark> dentro de um diretório que o serviço faça parte, para o exemplo em questão o diretório é "technicalDebt", resultando no seguinte path: "src/test/java/org/tracy/technicaldebt", logo após adicionamos a anotação @Tag("Service") e
@ExtendWith(MockitoExtension.class) em cima do "public class".

```
@Tag("Service")
@ExtendWith(MockitoExtension.class)
public class TechnicalDebtServiceTest {

}
```
Agora precisamos pegar os atributos da classe de serviço para a qual os testes devem ser feitos e passar como atributos da classe teste, os atributos que forem outros serviços e repositórios, devem receber a anotação <mark>@Mock.</mark>

```
@Tag("Service")
@ExtendWith(MockitoExtension.class)
public class TechnicalDebtServiceTest {

   @Mock
   private ITAssetService assetService;

   @Mock
   private BusinessProcessService businessProcessService;

   @Mock
   private BusinessMetricService businessMetricService;
  
   ...
}
```

Após todos os atributos necessários para a classe de serviço estiverem "mockados" deve ser injetado todos os mocks em uma
instância do serviço, isso pode ser feito através da anotação <mark>@InjectMocks</mark> ou através de um método de construção anotado por um <mark>@Beforeach</mark>, damos preferência ao <mark>@InjectMocks.</mark>

```
@Tag("Service")
@ExtendWith(MockitoExtension.class)
public class TechnicalDebtServiceTest {

   @Mock
   private ITAssetService assetService;

   @Mock
   private BusinessProcessService businessProcessService;

   @Mock
   private BusinessMetricService businessMetricService;
  
   ...
  
   @Mock
   private BusinessCanvasService businessCanvasService;

   @InjectMocks
   private TechnicalDebtService technicalDebtService;
  
}
```

Com todos as dependências injetadas no serviço para ser testado, partimos para criação do teste unitário, na mesma classe.
Iniciamos o método de teste com uma nomenclatura a qual deve de forma mais clara possível identificar a validação do teste.  

Todos os testes devem ter como retorno o tipo void, e uma anotação obrigatória <mark>@Test</mark> e uma opcional @DisplayName (pode haver outras anotações opcionais), a anotação @Test marca o método como teste, fazendo com que o testrunner execute os métodos anotados, além de poder executar cada um isoladamente.
Já o @DisplayName dá uma título ao teste, para que na interface seja visto com mais detalhes o que o teste se propõem a fazer,
nesta anotação você pode escrever em qualquer língua, desde que fique claro e compatível.

Como primeiro exemplo, será testado a criação de uma TechnicalDebt, então, para o nome do método de teste algo parecido com
"shouldSaveTechnicalDebt", com o retorno void e duas anotações, no DisplayName evidenciando a validação do teste:

```
   @Test
   @DisplayName("Deve salvar uma divida tecnica")
   void shouldSaveTechnicalDebt() {
  
   }
```

Agora vamos para a primeira etapa do teste, a preparação, aqui vamos olhar para o fluxo método "save" do serviço "TechnicalDebtService"
e criar as entidades e configurações que precisaremos para a segunda e terceira etapa.

No método save, vemos dois parâmetros "TechnicalDebt" e "Feedback", os quais precisamos então criá-los na preparação do teste, a primeira etapa.
Então, em uma breve análise notamos que precisamos mockar o retorno do saveAndFlush() do repositório "technicalDebtRepository".
Para o teste em questão é necessário mockar outros comportamentos de outras classes (serviços e repositórios), mas para esse guia não ficar extenso não serão detalhados.

```
   @Transactional
   public TechnicalDebt save(TechnicalDebt technicalDebt, Feedback feedback) {
      initializeLists(technicalDebt);

      if(technicalDebt.getBusinessPriority() == null){
           technicalDebt.setBusinessPriority(BusinessPriorityValue.UNDEFINED.value);
       }
       if(technicalDebt.getIssue() != null && technicalDebt.getIssue().getAssignedTo() != null){
           technicalDebt.setAssignedTo(technicalDebt.getAssignedTo());
       }

      List<TechnicalDebtImpact> impactsToChange = technicalDebt.getTechnicalDebtImpacts();
       technicalDebt.setTechnicalDebtImpacts(new LinkedList<>());
       TechnicalDebt technicalDebtAfterSave = this.technicalDebtRepository.saveAndFlush(technicalDebt);
       persistTechImpacts(technicalDebt);
       updateTechnicalDebtImpacts(technicalDebtAfterSave, impactsToChange);
       updateAndSaveBusinessPriority(technicalDebtAfterSave, "TD_CREATE", feedback);
       this.technicalDebtRepository.flush();

       return technicalDebtAfterSave;
   }
```

Na primeira etapa criamos os objetos e configuramos os retornos mocks dos atributos anotados com <mark>@Mock</mark> através do
método "when()" do Mockito seguido de um ".return()" com o objeto simulado no retorno real do método da classe mockada, mas primeiro, precisamos construir esses
retornos, e para facilitar a construção de tais objetos utilizamos os métodos estáticos, builders, para poupar tempo e linhas de código.
Na linha 148 o comportamento do repositório é simulado, utilizando o "when()", note que é preciso especificar qual método a classe mockada está chamando e
passar como parâmetro a classe que o método espera, e no ".return()", a simulação do retorno, o objeto technicalDebt.

```
   @Test
   @DisplayName("Deve salvar uma dívida técnica")
   void shouldSaveTechnicalDebt() {

       ConfigItem configItemReturn = createConfigItem().id(1L).build();
       TechnicalDebt technicalDebt = createTechnicalDebt().build();
       Feedback feedback = createFeedBack().build();
       PriorityCanvas priorityCanvas = createPriorityCanvas().build();

       when(configItemService.findById(anyLong())).thenReturn(configItemReturn);
       when(technicalDebtRepository.saveAndFlush(any(TechnicalDebt.class))).thenReturn(technicalDebt);
       when(technicalDebtRepository.save(any(TechnicalDebt.class))).thenReturn(technicalDebt);
       when(priorityCanvasRepository.findAllByOrganizationId(anyLong()))
               .thenReturn(Collections.singletonList(priorityCanvas));
              
   }
```

Com as entidades criadas e retornos simulados como esperado, continuamos para a segunda etapa do teste, a execução, bem simples,
apenas chamamos o método a qual queremos testar e passamos seus devidos parâmetros.

```
   @Test
   @DisplayName("Deve salvar uma dívida técnica")
   void shouldSaveTechnicalDebt() {
  
       ...
      
       when(configItemService.findById(anyLong())).thenReturn(configItemReturn);
       when(technicalDebtRepository.saveAndFlush(any(TechnicalDebt.class))).thenReturn(technicalDebt);
       when(technicalDebtRepository.save(any(TechnicalDebt.class))).thenReturn(technicalDebt);
       when(priorityCanvasRepository.findAllByOrganizationId(anyLong()))
               .thenReturn(Collections.singletonList(priorityCanvas));

       technicalDebtService.save(technicalDebt, feedback);

       ArgumentCaptor<TechnicalDebt> technicalDebtArgumentCaptor = ArgumentCaptor.forClass(TechnicalDebt.class);
       ArgumentCaptor<PriorityLog> priorityLogArgumentCaptor = ArgumentCaptor.forClass(PriorityLog.class);

```
Depois da preparação e execução, chegou a vez da validação dos resultados, em alguns casos, é preciso saber como o objeto chegou ao
repositório/serviço, momento que o objeto é passado por parâmetro do método, e para isso é necessário a criação de objetos do tipo <mark>ArgumentCaptor</mark>, ele é capaz de capturar os objetos nos parâmetros e é usado em conjunto com o método "verify()". 

 O método verify verifica as ocorrências das chamadas aos métodos da classe que foram utilizados durante a execução do teste, que por padrão é "times(1)", uma ocorrência do método da instância, o times é o segundo parâmetro do método verify(), em seguida utiliza-se o "." mas o método que deseja verificar a ocorrência, que para esse exemplo vamos focar no "saveAndFlush()", linha 158, que é passado como parâmetro um ArgumentCaptor do tipo <mark>TechnicalDebt</mark>, que é justamente a classe que chega para ser salva no repositório.  
 
  Com o método "capture()" do ArgumentCaptor para capturar o valor e depois utilizamos o
método "getValue()" para pegar o valor capturado e armazenar em uma variável, essa variável será utilizado para verificação dos campos.

```
       ArgumentCaptor<TechnicalDebt> technicalDebtArgumentCaptor = ArgumentCaptor.forClass(TechnicalDebt.class);
       ArgumentCaptor<PriorityLog> priorityLogArgumentCaptor = ArgumentCaptor.forClass(PriorityLog.class);

       verify(technicalDebtRepository).saveAndFlush(technicalDebtArgumentCaptor.capture());
       TechnicalDebt beforeSaveTechnicalDebt = technicalDebtArgumentCaptor.getValue();
       verify(impactService).saveAll(any());
       verify(technicalDebtRepository).save(technicalDebtArgumentCaptor.capture());
       TechnicalDebt afterSaveTechnicalDebt = technicalDebtArgumentCaptor.getValue();
       verify(logRepository).save(priorityLogArgumentCaptor.capture());
       PriorityLog priorityLog = priorityLogArgumentCaptor.getValue();
```

A verificação dos campos é feita através dos assertions, aqui se compara os valores atuais dos valores esperados,
dessa maneira validando campo a campo. É importante que todos os campos sejam validados, pois, durante o fluxo é possível que
algum valor seja alterado, e essa alteração possa ser parte do fluxo ou um bug gerado, é aqui que está a importância do teste unitário,
ele garante que para aquele fluxo o comportamento seja o esperado.

```
   @Test
   @DisplayName("Deve salvar uma divida tecnica")
   void shouldSaveTechnicalDebt() {
      
       ...
      
       verify(technicalDebtRepository).saveAndFlush(technicalDebtArgumentCaptor.capture());
       TechnicalDebt beforeSaveTechnicalDebt = technicalDebtArgumentCaptor.getValue();
       verify(impactService).saveAll(any());
       verify(technicalDebtRepository).save(technicalDebtArgumentCaptor.capture());
       TechnicalDebt afterSaveTechnicalDebt = technicalDebtArgumentCaptor.getValue();
       verify(logRepository).save(priorityLogArgumentCaptor.capture());
       PriorityLog priorityLog = priorityLogArgumentCaptor.getValue();
      
       assertAll("beforeSaveTechnicalDebt",
               () -> assertThat(beforeSaveTechnicalDebt.getName(), is(technicalDebt.getName())),
               () -> assertThat(beforeSaveTechnicalDebt.getDescription(), is(technicalDebt.getDescription())),
               () -> assertThat(beforeSaveTechnicalDebt.getBusinessPriority(), is(technicalDebt.getBusinessPriority())),
               () -> assertThat(beforeSaveTechnicalDebt.getTechnicalPriority(), is(technicalDebt.getTechnicalPriority())),
               () -> assertThat(beforeSaveTechnicalDebt.getCheckedByUser(), is(technicalDebt.getCheckedByUser())),
               () -> assertThat(beforeSaveTechnicalDebt.getEnabled(), is(technicalDebt.getEnabled())),
               () -> assertThat(beforeSaveTechnicalDebt.getType(), is(technicalDebt.getType()))
       );
      
       assertAll("afterSaveTechnicalDebt",
               () -> assertThat(afterSaveTechnicalDebt.getTechnicalPriority(), is(technicalDebt.getTechnicalPriority())),
               () -> assertThat(afterSaveTechnicalDebt.getName(), is(technicalDebt.getName())),
               () -> assertThat(afterSaveTechnicalDebt.getDescription(), is(technicalDebt.getDescription())),
               () -> assertThat(afterSaveTechnicalDebt.getBusinessPriority(), is(technicalDebt.getBusinessPriority())),
               () -> assertThat(afterSaveTechnicalDebt.getTechnicalPriority(), is(technicalDebt.getTechnicalPriority())),
               () -> assertThat(afterSaveTechnicalDebt.getCheckedByUser(), is(technicalDebt.getCheckedByUser())),
               () -> assertThat(afterSaveTechnicalDebt.getEnabled(), is(technicalDebt.getEnabled())),
               () -> assertThat(afterSaveTechnicalDebt.getType(), is(technicalDebt.getType()))
       );
      
       assertAll("priorityLog",
               () -> assertThat(priorityLog.getTrigger(), is("TD_CREATE")),
               () -> assertThat(priorityLog.getTdType(), is("TechnicalDebtType Name")),
               () -> assertThat(priorityLog.getOldBusinessPriority(), is(1000)),
               () -> assertThat(priorityLog.getNewBusinessPriority(), is(100)),
               () -> assertThat(priorityLog.getOldTechnicalPriority(), is(1000)),
               () -> assertThat(priorityLog.getNewTechnicalPriority(), is(1000)),
               () -> assertThat(priorityLog.getComment(), is("FeedBack Comment")),
               () -> assertFalse(priorityLog.getPrioritizedByImpact()),
               () -> assertFalse(priorityLog.getPrioritizedByEffort()),
               () -> assertFalse(priorityLog.getPrioritizedByType()),
               () -> assertFalse(priorityLog.getPrioritizedByAge())
       );
   }
```


<mark>Builders</mark> são os métodos que fazem instância da classe e que você pode alterar os campos enquanto chama o método, como na linha 142 onde o campo "id" está sendo setado com o valor 1L.
Os builders ficam no path referente aos testes, em: "src/test/java/org/tracy/builders". Builders podem possuir outros builders para facilitar a sua construção, mas cuidado para não gerar recursão entre eles.

```
public class ConfigItemBuilder {

   public static ConfigItem.Builder createConfigItem() {
       return ConfigItem.builder()
               .id(1L)
               .name("ConfigItem Name")
               .description("ConfigItem Description")
               .type(createConfigItemType().build())
               .status(Status.OPERATIONAL)
               .children(Collections.singletonList(createConfigItemChildren().build()))
               .organization(createOrganization().build())
               .affectedITAssets(Collections.singletonList(createITAsset().build()))
               .teams(Collections.singletonList(createTeam().build()));
   }
}
```
