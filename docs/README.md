
# Tracy API

Primeiramente, muito obrigado por estar aqui, é um enorme prazer te-lo como colaborador da Tracy-TD. O projeto é uma ferramenta de gerência de dívidas técnicas orientada a negócios.
Através da ferramenta é possível registrar dívidas, monitorá-las, priorizá-las usando critérios técnicos e critérios ligados ao negócio da organização.
Este projeto é útil pois permite a gerência de dívidas técnincas.
///REVIEW/// O projeto possui integrações com outras plataformas, como o gitlab, redmine.... acrescentar as outras....

## Tabelas de conteúdos
- [Tecnologias utilizadas](#tecnologias-utilizadas)
- [Como rodar a aplicação](#como-rodar-a-aplicao)
- [Como conseguir ajuda](#como-conseguir-ajuda)
- [Lidando com as contribuições](#lidando-com-as-contribuies)
- [Processo de desenvolvimento do projeto](#processo-de-desenvolvimento-do-projeto)
- [Coordenador do projeto](#coordenador-do-projeto)

## Tecnologias utilizadas

Importante que tenha tais tecnologias instaladas no seu ambiente de desenvolvimento.

- [Spring Boot](https://docs.spring.io/spring-boot/docs/current/reference/htmlsingle/)
- [Java JDK 12](https://www.oracle.com/technetwork/java/javase/downloads/jdk12-downloads-5295953.html)
- [Maven](https://maven.apache.org/)
- [Lombok](https://projectlombok.org/)
- [PostgreSQL](https://www.postgresql.org/)


## Como rodar a aplicação

O projeto utiliza uma lib específica de processamento de texto, **tracy-text-processor**. É possivel que você não tenha acesso ao repositório, solicite acesso no canal do [Discord](https://discord.gg/AwaqbGPRkd).

Faça o clone da biblioteca [Tracy Text Processor](https://github.com/tracy-td/tracy-text-processor)

```bash
  $ git clone https://github.com/tracy-td/tracy-text-processor.git
```

Com o maven instalado execute os seguintes comandos dentro do diretorio da lib. Caso não tenha o maven, siga esse [tutorial](https://dicasdejava.com.br/como-instalar-o-maven-no-windows/).

```bash
  $ mvn compile && mvn package && mvn install
```

Com o Postgress instalado e rodando (por padrão é em localhost:5432), crie o banco de dados **tracytd**, lembresse de alterar o que for necessário em **application-dev.yml**, como senha e/ou nome do banco.

- application-dev.yml:

      spring:
        datasource:
          url: jdbc:postgresql://localhost:5432/tracytd
          username: postgres
          password: a


Configure VM Options com **-Dspring.profiles.active=dev** para aplicação subir com as configurações do **application-dev.yml**.

Em seguida, contribua com o projeto! Sugira novas funcionalidades e reporte bugs que identificar.

## Como conseguir ajuda

Você deve acessar o canal do [Discord](https://discord.gg/AwaqbGPRkd) onde terá acesso aos desenvolvedores que estão atuando no projeto, bem como outras pessoas que estão utilizando Tracy em suas empresas.

## Lidando com as contribuições

O projeto possui um board de gerência do que deve ou não ser priorizado.
Este conjunto de desenvolvedores é formado por pessoas com experiências no código e no produto.
Com o tempo, você poderá ajudar também participando do board de gerenciamento.

### Processo de desenvolvimento do projeto

- Registro de uma issue;

            Uma vez cadastrada, a issue pode receber comentários de outras pessoas, para detalhar
          e melhorar a descrição da nova solicitação de melhoria, nova funcionalidade ou bug a 
          ser resolvido.
            Qualquer pessoa pode assumir uma issue aberta e implementar sua solução.

- Atribuição de [Issue](https://github.com/rodrigor/tracy-api/issues);

            Em Issues terá todo o backlog do projeto, ao clicar em uma issue poderar atribui-la
          em "Assigness", então ela estará por sua responsabilidade de desenvolvimento. Siga as 
          orientações de como criar uma branch e fazer pull request.

- Criando branch;

            Para iniciar o desenvolvimento é necessário criar uma branch, existe como padrão, 
          três tipos de branchs, hot, feat, bugfix: 
             - hot -> hotfix: Prefixo de branch para mudança rárpida e pequena em código;
             - feat -> feature: Prefixo de branch para nova funcionalidade ou melhoria;
             - bugfix: Prefixo de branch que corrige algum bug em código.
            Sabendo dos prefixos de cada tipo de issue, prenche o sufixo do nome da branch 
          com "/#" seguido do número da Issue.
                Exemplo: "hot/#xxxx", "feat/#yyyy", "bugfix/#zzzz".

- Fazendo Pull Request;

          Após implementar sua solução é hora de fazer o Pull Request...


## Coordenador do projeto
* [**Rodrigo Rebouças de Almeida**](http://rodrigor.com)
