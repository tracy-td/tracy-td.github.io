# Instalação - Tracy API

## **Requisitos**

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
## **Tutorial de instalação**
&nbsp;

<!-- - Be sure that you already installed all the requirements, and after that, follow the steps below. -->
- Tenha certeza que você já instalou todos os requisitos e, depois disso, siga os passos abaixo. 

---

<!-- ## First Step: Backend -->
## **Primeiro Passo: Backend**
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
