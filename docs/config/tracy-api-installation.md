# Instalação - Tracy API

## Requisitos

Para construir e executar a aplicação, você precisa de:

- [Java Jre 8](https://www.oracle.com/java/technologies/javase-jre8-downloads.html)
- [Java JDK 11](https://www.oracle.com/java/technologies/javase-jdk11-downloads.html)
- [PostgresSQL 11.5](https://www.enterprisedb.com/downloads/postgres-postgresql-downloads)
- [Git](https://git-scm.com/downloads)
- [Intellij IDE](https://www.jetbrains.com/pt-br/idea/download/#section=windows)  (Para uso com a parte de back end)
- [Vs Code IDE](https://code.visualstudio.com/download)  (Se desejar usar na parte de front end. Caso contrário, o intelijj pode ser usado também)
- [Maven](https://maven.apache.org/download.cgi)  (Baixe o arquivo Bynary.zip)
- CMD ou Windows Powershell

---

<!-- ## Installation Tutorial -->
## Tutorial de instalação
&nbsp;

<!-- - Be sure that you already installed all the requirements, and after that, follow the steps below. -->
- Tenha certeza que você já instalou todos os requisitos e, depois disso, siga os passos abaixo. 

---

<!-- ## First Step: Backend -->
## Primeiro Passo: Backend

---

<!-- - Clone the repositories `tracy-api` and `tracy-text-processor`. (In case of problems using the git bash function you can use the cmd to do this)
- Run `mvn clean install`
- Create the postgres database, and name it tracytd
- Open the API Rest code in Intellij. Go to src > main> resources and create an archive named "application-dev.yml".
- Paste inside this archive the following code: -->

- Clonar os repositórios (Em caso de problemas usando o git bash, tentar pelo terminal cmd).
- Execute `mvn clean install`
- Criar o banco de dados no postgres nomeado tracytd
- Abrir o código da api no Intellij. Dentro dos arquivos da api rest, criar um arquivo nomeado application-dev.yml (Caminho src > main > resources)
- Colar dentro do arquivo o seguinte código:


        spring:
        datasource:
        url: jdbc:postgresql://localhost:5432/tracytd
        username: postgres
        password: tuasenha (substituir pela senha do postgres)

<!-- - Execute the command "mvn clean install in the intellij" terminal.
- In intellij, go to the menu "Add configuration", and create a new one by clicking the "+" signal on left top. Choose the category "Application".
- In the following menu, complete the field with this instructions: -->

- Executar o comando `mvn clean install` no terminal do intellij.
- No intellij, ir até o menu Add Configuration, adicionar uma nova configuração (sinal + no canto superior esquerdo), selecionando a opção "application"
- No menu seguinte, complete os campos com essas instruções:

        name: "tracy-api"

        main class: procure a classe "tracy application"

     

<!-- - In the field "Modify options", chose the option "Add vm options", and in the field with the same name, paste the following code: -->
- No campo "Modify options", escolha a opção "Add vm options", e no campo com o mesmo nome, cole o seguinte código:

        -Dspring.profiles.active=dev

<!-- - After that, click apply and ok. If the field "Add configuration" didn't change automatically, change it to the new configuration.
- Run the project! -->
- Depois disso, clique em aplicar e ok. Se o campo "Add configuration" não mudar automaticamente, mude ele para a nova configuração.
- Rode o projeto!
&nbsp;


<!-- ## Second Step: Front End -->
## Segundo passo: Front End

---

<!-- - Clone the repositorie tracy-front. (In case of problems using the git bash function you can use the cmd to do this)
- Open the project with Vs Code and execute the comand "npm i". It wil take a few minutes to execute.
- After that finishes, execute the command "ng s". It will last a little longer.
- After it's done, open your browser and go to "localhost: 4200"
- Put the login "admin@tracytd.org", and the password "rootadmin"
- It's Done! -->

- Clone o repositório tracy-front. (Em caso de problemas com a funcionalidade do git bash você pode usar o cmd para fazer isso)
- Abra o projeto com o Vs Code e execute o comando `npm i`. Isso vai levar alguns minutos para executar.
- Após o término, execute o comando `ng s`. Isso vai demorar um pouco mais.
- Depois que terminar, abra seu navegador e vá para "localhost: 4200"
- Coloque o login "admin@tracytd.org", e a senha  "rootadmin"
- Está pronto!

<!-- ## How to get help? -->
## Como conseguir ajuda?

<!-- You should access the [Discord](https://discord.gg/AwaqbGPRkd) channel where you will have access to the developers working on the project, as well as other people who are using Tracy in their companies. -->

Você deverá acessar o canal do [Discord](https://discord.gg/AwaqbGPRkd), onde terá acesso aos desenvolvedores trabalhando no projeto, assim como outras pessoas que estão usando Tracy em suas empresas.

<!-- ## Handling Contributions -->
## Gerenciamento de contribuições

<!-- The project has a management board of what should or should not be prioritized.
This set of developers is made up of people with experience in the code and the product.
In time, you will be able to help by joining the management board as well. -->

O projeto tem um conselho de gestão do que deve ou não ser priorizado.
Esse conjunto de desenvolvedores é formado por pessoas com experiência no código e no produto.
Com o tempo, você também poderá ajudar ingressando no conselho de administração.



<!-- ## Project Development Process -->
## Processo de desenvolvimento do projeto

<!-- - Registration of an issue; -->
- Registro de uma edição (issue);

        Once registered, the issue can receive comments from other people, to detail
        and improve the description of the new enhancement request, new feature or bug to
        be solved.
        Anyone can take up an open issue and implement their solution.

        Uma vez registrada, a edição pode receber comentários de outras pessoas, para detalhar
        e melhorar a descrição da nova solicitação de aprimoramento, novo recurso ou bug para 
        ser resolvido.
        Qualquer um pode assumir um problema aberto e implementar sua solução.

<!-- - Atribution of [Issue](https://github.com/rodrigor/tracy-api/issues); -->
- Atribuição de uma [Edição](https://github.com/rodrigor/tracy-api/issues);
        
        In Issues you will have the entire backlog of the project, and by clicking on an issue, you can assign it,
        in "Assigness". So, it will be your development responsibility. follow the
        guidelines on how to create a branch and make a pull request.

        Em edições você terá todo os registros acumulados do projeto e, clicando em uma edição, você pode atribuir
        ela em "Atribuir". Então, ela será sua responsabilidade de desenvolvimento. Siga as orientações
        sobre como criar uma branch e fazer uma solicitação. (Pull request).

<!-- - Creating branch; -->
- Criando branch;

        To start development it is necessary to create a branch. There are, by default,
        three types of branches: hot, feat and bugfix:
         - hot -> hotfix: Branch prefix for quick and small code change;
         - feat -> feature: Branch prefix for new feature or improvement;
         - bugfix -> Branch prefix that fixes some bug in code.
        Knowing the prefixes for each issue type, fill in the branch name suffix
        with "/#", followed by the Issue number.
           Example: "hot/#xxxx", "feat/#yyyy", "bugfix/#zzzz".

        Para começar o desenvolvimento é necessário criar uma branch. Aqui estão, por padrão,
        três tipos de branch: hot, feat e bugfix:
         - hot -> hotfix: Prefico de branch para pequenas e rápidas mudanãs de código.
         - feat -> feature: Prefixo de branch para nova funcionalidade ou aprimoramento.
         - bugfix -> Prefixo de branch que conserta algum tipo de bug no código.
        Conhecendo os prefixos para cada tipo de edição, complete o sufixo do nome da branch
        com "/#", seguido do número da edição.
           Exemplo: "hot/#xxxx", "feat/#yyyy", "bugfix/#zzzz".

- Fazendo Pull Request;

          Após implementar sua solução é hora de fazer o Pull Request...