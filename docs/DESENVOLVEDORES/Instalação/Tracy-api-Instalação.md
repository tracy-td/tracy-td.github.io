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

- Clone os repositórios tracy-api da branch tracy_ees.
- Crie o banco de dados no Postgres e nomeie-o como tracytd.
- Vá para src > main > resources e crie um arquivo chamado "application-dev.yml".
- Cole o seguinte código dentro do arquivo:

        spring:
            datasource:
                url: jdbc:postgresql://localhost:5432/tracytd username: postgres
                password: tuasenha (substituir pela senha do
                postgres)

- No arquivo docker-compose.yml, troque as senhas pela do seu postgres.
- Crie um arquivo .env e digite nele "TRACY_API_VERSION="1.0.0"".
- No arquivo tracyApplication.java substituir o código "env.TRACY_API_VERSION" por "TRACY_API_VERSION".
- Executar o comando `mvn clean install` no terminal da sua IDE.
- Quando terminar, rodar `mvn -N io.takari:maven:wrapper` no terminal.
- Por fim,`docker-compose up --build` , que fará a api funcionar.
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
      
In the file docker-compose.yml, change the passwords for your own
Create a file .env and write "TRACY_API_VERSION="1.0.0"" on it
In the file tracyApplication.java change the piece of code "env.TRACY_API_VERSION" fora "TRACY_API_VERSION".
Execute the command mvn clean install in your IDE's terminal.
When its finished, run mvn -N io.takari:maven:wrapper in the terminal
At last, docker-compose up --build, which will make the api work

 

How to get help?
You should access the Discord channel where you will have access to the developers working on the project, as well as other people who are using Tracy in their companies. -->