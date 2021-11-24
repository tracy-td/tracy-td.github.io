#Testes unitários com mock para as classes de serviços

Serão demonstradas neste guia de teste, as 4 funções de um CRUD e exceção, para que assim, seja possivel que se tenha
uma ideia basica de como continuar com a implementação de testes.

Um teste é composto por 3 fazes, preparação, execução e validação.
- Preparação: nessa etapa é criado todos os argumentos necessários e configurações para que o teste possa representar o mais próximo do cenario real;
- Execução: aqui onde se utiliza os argumentos produzidos na preparação e executamos o metodo do serviço a qual queremos testar;
- Validação: a fase mais importante de um teste, onde ocorre todas as verificações da execução do teste e se ocorreu como esperado;

Para testarmos um serviço vamos começar criando a classe de teste, caso a classe de teste não exista.
A nomeclatura da classe de teste deve seguir um padrão "{nome da classe do serviço}" + "Test",
por exemplo: "TechnicalDebtServiceTest", o local em que esse arquivo deve está é no path do 
projeto em "src/test/java/org/{nome_do_projeto}" dentro de um diretório que o serviço faça parte, para o exemplo em questão
o diretório é "technicalDebt", resultando no seguinte path: "src/test/java/org/tracy/technicaldebt", logo após adicionamos a anotação @Tag("Service") e 
@ExtendWith(MockitoExtension.class) em cima do "public class".

![](resources\TechnicalDebtServiceTest_01.png)

Agora precisamos pegar os atributos da classe de serviço para a qual os testes devem ser feitos e passar como atributos da classe teste,
os atributos que forem outros serviços e repositórios, devem receber a anotação @Mock.

![](resources\TechnicalDebtServiceTest_02.png)

Após todos os atributos necessários para a classe de serviço estiverem "mockados" deve ser injetado todos os mocks em uma 
instância do serviço, isso pode ser feito atraves da anotação @InjectMocks ou através de um metodo de construção anotado por um @Beforeach, damos 
preferencia ao @InjectMocks.

![](resources\TechnicalDebtServiceTest_03.png)

Com todos as dependências injetadas no serviço para ser testado, partimos para criação do teste unitário, na mesma classe, 
iniciamos o método de teste com uma nomeclatura a qual deve de forma mais clara possivel identificar a validação do teste. 
Todos os testes devem ter como retorno o tipo void, e uma anotação obrigatória @Test e uma opcinal @DisplayName (pode haver outras anotações opcionais), 
a anotação @Test marca o metodo como teste, fazendo com que o testrunner execute os métodos anotados, além de poder executar cada um isoladamente. 
Já o @DisplayName dá uma titulo ao teste, para que na interface seja visto com mais detalhes o que o teste se propõem a fazer, 
nesta anotação você pode escrever em qualquer lingua, desde que fique claro e compatível.

Como primeiro exemplo, será testado a criação de uma TechnicalDebt, então, para o nome do metodo de teste algo parecido com 
"shouldSaveTechnicalDebt", com o retorno void e duas anotações, no DisplayName evidenciando a validação do teste:

![](resources\TechnicalDebtServiceTest_04.png)

Agora vamos para a primeira etapa do teste, a preparação, aqui vamos olhar para o fluxo metodo "save" do serviço "TechnicalDebtService" 
e criar as entidades e configurações que precisaremos para a segunda e terceira etapa.

No metodo save, vemos dois parametros "TechnicalDebt" e "Feedback", os quais precisamos então cria-los na preparação do teste, a primeira etapa. 
Então, em uma breve analise notamos que precisamos mockar o retorno do saveAndFlush() do repositório "technicalDebtRepository" (linha 110). 
Para o teste em questão é necessário mockar outros comportamentos de outras classes (serviços e repositórios), mas para esse guia não ficar extenso não serão detalhados.

![](resources\TechnicalDebtServiceTest_06.png)

Na primeira etapa criamos os objetos e configuramos os retornos mocks dos atributos anotados com @Mock através do 
metodo "when()" do Mockito seguido de um ".return()" com o objeto simulado no retorno real do método da classe mockada, mas primeiro, precisamos construir esses 
retornos, e para facilitar a contrução de tais objetos utilizamos os métodos estáticos, builders, para poupar tempo e linhas de código. 
Na linha 148 o comportamento do repositório é simulado, utilizando o "when()", note que é preciso especificar qual método a classe mockada está chamando e 
passar como parâmetro a classe que o método espera, e no ".return()", a simulação do retorno, o objeto technicalDebt. 

![](resources\TechnicalDebtServiceTest_05.png)

Com as entidades criadas e retornos simulados como esperado, continuamos para a segunda etapa do teste, a execução, bem simples, 
apenas chamamos o método a qual queremos testar e passamos seus devidos parâmetros (linha 153).

![](resources\TechnicalDebtServiceTest_07.png)

Depois da preparação e execução, chegou a vez da validação dos resultados, em alguns casos, é preciso saber como o objeto chegou ao 
repositório/serviço, momento que o objeto chega no parâmetro do método, e para isso é necessário a criação de objetos do tipo ArgumentCaptor, ele 
é capaz de capturar os objetos que são passados por parâmetros e é usado em conjunto com o método "verify()", o método verify, 
verifica as ocorrências das chamadas aos métodos da classe que foram utilizados durante a execução do teste, que por padrão é "times(1)", 
uma ocorrência daquele objeto, segundo parâmetro do método verify(), em seguida utilizasse o "." mas o método que deseja verificar a 
ocorrência, que para esse exemplo vamos focar no "saveAndFlush()", linha 158, que é passado como parametro um ArgumentCaptor do tipo TechnicalDebt, 
que é justamento a classe que chega para ser salva no repositório.

![](resources\TechnicalDebtServiceTest_08.png)

Builders são os metodos que fazem instância da classe e que você pode alterar os campos enquanto chama o método, como na linha 142 onde o campo "id" está sendo setado com o valor 1L. 
Os builders ficam no path referente aos testes, em: "src/test/java/org/tracy/builders". Builders podem possuir outros builders para facilitar a sua construção, mas cuidado para não gerar recursão entre eles.

![](resources\ConfigItemBuilder.png)
