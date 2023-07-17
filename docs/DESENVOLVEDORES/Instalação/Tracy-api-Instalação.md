# Instalação - Tracy API

## **Requisitos**

Para construir e executar a aplicação, você precisa dos seguintes requisitos:

- [Java Jre 8](https://www.oracle.com/java/technologies/javase-jre8-downloads.html)
- [Java JDK 11](https://www.oracle.com/java/technologies/javase-jdk11-downloads.html)
- [PostgresSQL 11.5](https://www.enterprisedb.com/downloads/postgres-postgresql-downloads)
- [Git](https://git-scm.com/downloads)
- [Intellij IDE](https://www.jetbrains.com/pt-br/idea/download/#section=windows)  (Para uso com a parte de back end)
- [Vs Code IDE](https://code.visualstudio.com/download)  (Se desejar usar na parte de front end. Caso contrário, o intelijj pode ser usado também)
- [Maven](https://maven.apache.org/download.cgi)  (Baixe o arquivo Bynary.zip)
- CMD ou Windows Powershell

---

## **Tutorial de instalação**
&nbsp;

- Certifique-se de ter instalado todos os requisitos e, em seguida, siga as etapas abaixo. 

---

## **Primeiro Passo: Backend**
---

- Clone os repositórios tracy-api e traExecute mvn clean install
- Execute `mvn clean install`
- Crie o banco de dados no  Postgres e nomeie-o como tracytd
- Abra o código da API Rest no Intellij. Vá para src > main > resources e crie um arquivo chamado "application-dev.yml".
- Cole o seguinte código dentro do arquivo:


        spring:
        datasource:
        url: jdbc:postgresql://localhost:5432/tracytd
        username: postgres
        password: tuasenha (substituir pela senha do postgres)

- Executar o comando `mvn clean install` no terminal do intellij.
- No Intellij, vá para o menu "Add Configuration" e crie uma nova configuração clicando no sinal "+" no canto superior esquerdo. Escolha a categoria "Application".
- No menu seguinte, complete os campos com essas instruções:

        name: "tracy-api"

        main class: procure a classe "tracy application"

     
- No campo "Modify options", escolha a opção "Add vm options", e no campo com o mesmo nome, cole o seguinte código:

        -Dspring.profiles.active=dev

-Apos isso, no campo Environment variables cole o seguinte código : 

        env.TRACY_API_VERSION=SNAPSHOT

- Depois disso, clique em aplicar e ok. Se o campo "Add configuration" não mudar automaticamente, mude ele para a nova configuração.
- Rode o projeto!
&nbsp;


## **Como conseguir ajuda?**

Você deverá acessar o canal do [Discord](https://discord.gg/AwaqbGPRkd), onde terá acesso aos desenvolvedores trabalhando no projeto, assim como outras pessoas que estão usando Tracy em suas empresas.



<!-- Installation - Tracy API
Requirements
To build and run the application, you need the following requirements:

- [Java Jre 8](https://www.oracle.com/java/technologies/javase-jre8-downloads.html)
- [Java JDK 11](https://www.oracle.com/java/technologies/javase-jdk11-downloads.html)
- [PostgresSQL 11.5](https://www.enterprisedb.com/downloads/postgres-postgresql-downloads)
- [Git](https://git-scm.com/downloads)
- [Intellij IDE](https://www.jetbrains.com/pt-br/idea/download/#section=windows)  (Para uso com a parte de back end)
- [Vs Code IDE](https://code.visualstudio.com/download)  (Se desejar usar na parte de front end. Caso contrário, o intelijj pode ser usado também)
- [Maven](https://maven.apache.org/download.cgi)  (Baixe o arquivo Bynary.zip)
- CMD ou Windows Powershell

Make sure you have installed all the requirements, and then follow the steps below.
First Step: Backend
Clone the tracy-api and tracy-text-processor repositories. (In case of problems using the git bash function, you can use the cmd to do this)

Run mvn clean install

Create the Postgres database and name it tracytd

Open the API Rest code in Intellij. Go to src > main > resources and create a file named application-dev.yml.

Paste the following code inside the file:

yaml
Copy code
  spring:
    datasource:
      url: jdbc:postgresql://localhost:5432/tracytd
      username: postgres
      password: yourpassword (replace with the password of the postgres)
Execute the command mvn clean install in the Intellij terminal.

In Intellij, go to the "Add Configuration" menu and create a new configuration by clicking the "+" sign in the top left corner. Choose the "Application" category.

In the next menu, complete the fields with these instructions:

arduino
Copy code
  name: "tracy-api"

  main class: find the "tracy application" class
In the "Modify options" field, choose the "Add vm options" option, and in the field with the same name, paste the following code:

Copy code
  -Dspring.profiles.active=dev
After that, click apply and ok. If the "Add configuration" field doesn't change automatically, change it to the new configuration.

Run the project!
 

How to get help?
You should access the Discord channel where you will have access to the developers working on the project, as well as other people who are using Tracy in their companies. -->