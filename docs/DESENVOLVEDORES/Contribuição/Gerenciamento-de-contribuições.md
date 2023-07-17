

O projeto tem um conselho de gestão do que deve ou não ser priorizado.
Esse conjunto de desenvolvedores é formado por pessoas com experiência no código e no produto.
Com o tempo, você também poderá ajudar ingressando no conselho de administração.


## **Processo de desenvolvimento do projeto**

- Registro de uma [Issue](https://github.com/rodrigor/tracy-api/issues) 

        Uma vez registrada, a issue pode receber comentários de outras pessoas para detalhar
        e melhorar a descrição da nova solicitação de aprimoramento, novo recurso ou bug a ser
        resolvido.
        Qualquer pessoa pode assumir uma issue em aberto e implementar sua solução.


- Atribuição de uma [Issue](https://github.com/rodrigor/tracy-api/issues)
          
         Na página de issue, você terá a lista completa de issues do projeto e, ao clicar em uma issue,
         você pode atribuí-la a si mesmo em "Responsáveis". Assim, ela se tornará sua responsabilidade de desenvolvimento.
         Siga as diretrizes sobre como criar uma branch e fazer um pull request.

- Criando branch

        Para iniciar o desenvolvimento, é necessário criar uma branch. Existem, por padrão,
        três tipos de branches: hot, feat e bugfix:
         - hot -> hotfix: Prefixo de branch para mudanças rápidas e pequenas no código;
         - feat -> feature: Prefixo de branch para novas funcionalidades ou melhorias;
         - bugfix -> Prefixo de branch para correção de bugs no código.
        Conhecendo os prefixos para cada tipo de tarefa, preencha o sufixo do nome da branch
        com "/#", seguido pelo número da tarefa.
         Exemplo: "hot/#xxxx", "feat/#yyyy", "bugfix/#zzzz".

- Fazendo Pull Request

        Depois de implementar sua solução, você deve criar um Pull Request para que sua contribuição seja revisada e incorporada ao projeto principal. Siga os passos abaixo:
        
        1. Certifique-se de ter feito o commit de todas as alterações relevantes na sua branch.
        2. Acesse a página do repositório no GitHub.
        3. Clique na aba "Pull Requests".
        4. Clique no botão "New Pull Request".
        5. Selecione a sua branch como "base branch" e a branch principal do projeto como "compare branch".
        6. Revise as alterações propostas e forneça uma descrição clara do que foi feito.
        7. Caso necessário, mencione as tarefas ou problemas relacionados ao Pull Request.
        8. Clique em "Create Pull Request" para criar o Pull Request.
        9. Aguarde a revisão dos colaboradores do projeto.
        10. Durante o processo de revisão, esteja aberto a comentários e sugestões de melhorias.
        11. Se necessário, faça as alterações solicitadas e atualize o Pull Request.
        12. Uma vez que o Pull Request seja aprovado, ele será mesclado (merged) à branch principal do projeto.

        Lembre-se de manter uma comunicação clara e respeitosa durante todo o processo de revisão e colaboração. Seja receptivo aos feedbacks e esteja disposto a colaborar com outros membros da equipe.



## **Iniciando o desenvolvimento**



Para iniciar o desenvolvimento, é necessário criar uma branch. Por padrão, existem dois tipos de branches: feature e bugfix:

feature: Prefixo de branch para novas funcionalidades ou melhorias.
Nova funcionalidade: Uma nova função para a API que ainda não existe.
Melhoria: Melhoria de uma função já existente ou parte do código.
bugfix: Prefixo de branch que corrige um bug no código.
Sabendo dos prefixos para cada tipo de issue, preencha o sufixo do nome da branch com "/" seguido do número da Issue.

Exemplo: "feature/xxxx", "bugfix/yyyy".

Criando uma branch via terminal:

`git checkout -b <nome da branch>` : Esse comando cria a branch com o nome fornecido (não utilizar os "<>") e também troca para a branch atual de uso.


## **Criando issue**

Se você encontrou algum bug ou quer sugerir alguma funcionalidade, você pode criar uma issue nesse Link:  [Issue](https://github.com/rodrigor/tracy-api/issues).

Para criar uma nova Issue, você pode seguir os seguintes passos, todos os passos a seguir começam ao acessar a aba de [Issues](https://github.com/rodrigor/tracy-api/issues), ou já no template de [New issue](https://github.com/rodrigor/tracy-api/issues/new) do repositório.

Dentro do template de New issue, no input de "Title", escreva brevemente o que a nova issue deve fazer, e então no input de "Leave a comment", faça uma descrição mais detalhada sobre como a issue deve ser executada/implementada. Após as especificações da nova issue, ao lado direito existem alguns complementos importantes:

- Em "Assignees" você pode escolher a pessoa responsável para a execução da issue, caso o objetivo seja apenas deixar a issue registrada, não precisa atribuir, caso queira pegar uma issue, siga para seção atribuindo uma issue.
  
- Em "Labels" você define que tipo de feature e característica essa issue possui, como "bug", para uma issue referente a um bug no sistema, "documentation" issue que mexe com algum arquivo referente a documentação do projeto, "enhancement", para issue referente a uma nova feature ou melhoria para o sistema, existem várias labels e Issue podem receber várias labels e não são obrigatórias para a criação de uma.
Após esses passos a sua issue está pronta para ser criada, clique em "Submit new issue" e receba a nova issue com um "#" seguido de um valor numérico, um identificador para a issue, e este identificador será utilizado no comentário do seu Pull Request para ser feito o link entre a issue e o Pull Request.


## **Atribuindo uma issue**

Para atribuir uma issue, você precisa acessar a aba de Issues, ao selecionar uma issue, ela será aberta e poderá receber atribuição(ões) ao clicar em "Assignees", então selecionar quem deverá fazer parte do desenvolvimento dessa issue. Lembrando que em Assignees, não serão as mesmas pessoas que irão revisar o seu Pull Request.

## **Submetendo contribuições**

Ao concluir a sua contribuição é hora de fazer o famoso Pull Request, onde ele será revisado pela comunidade e então, se tudo estiver de acordo com as expectativas dos revisores, o Pull Request será aceito. Mas para isso, é preciso seguir alguns passos primeiro, é preciso preparar os arquivos que serão adicionados para o commit e consequentemente para o Pull Request/Revisão, com os seguintes passos no terminal:

- `git add "<nome do arquivo>"` ou `git add .`  : Esse comando adiciona o arquivo mencionado ou todos os arquivos salvos e modificados ao Stage, também conhecido como Index ou Staging Area. O Stage é o lugar onde os arquivos estão sendo preparados para o commit.
  
- `git commit -m "<mensagem do commit>"` : Com esse comando, você transfere seus arquivos para o diretório local do git com uma mensagem sobre o commit. É muito importante que essa mensagem contenha informações sobre as alterações feitas e referência à issue associada à contribuição. A mensagem do commit deve conter uma referência à issue, que é feita através de # seguido do número de identificação da issue no GitHub, seguido de uma breve descrição do que foi feito.
  
- `git push` : Com o git push, os arquivos serão enviados para o repositório na nuvem do GitHub. É possível que solicite suas credenciais, informe-as e continue o procedimento. Caso a branch ainda não exista no repositório do GitHub, será exibida uma mensagem no terminal para publicar a branch. Copie a mensagem e execute-a para enviar suas alterações. No repositório do GitHub do projeto, ao estar logado com as mesmas credenciais, será exibida uma mensagem informando que existe um Pull Request a ser solicitado.


## **Contribuindo com o código**

Para contribuição de código, temos 3 categorias para uma issue:

- Nova funcionalidade: São acréscimos de novas funções ou recursos que ainda não existem no projeto, e possuem como título da branch "feature".
  
- Melhoria: São mudanças em funções ou recursos que já existem no projeto, possuindo o título de branch "feature".
 
- Bug: Os bugs são divididos em dois tipos: críticos e não críticos, ambos com o título de branch "bugfix".
  
- Críticos: Afetam gravemente alguma funcionalidade importante do sistema, o que torna a aplicação inutilizável ou de difícil acesso.
  Não críticos: São bugs que causam apenas um leve incômodo na aplicação, não impactando significativamente a funcionalidade.


## **Contribuindo com a documentação**

A documentação de um software está sempre sujeita a mudanças de acordo com as novas funcionalidades que são desenvolvidas. Portanto, atualizações são necessárias para manter a integridade entre os desenvolvedores e os usuários da ferramenta. Contribuir com a documentação é importante para garantir que o software e a documentação estejam sempre alinhados. Consulte a Documentação para mais informações.

Outros arquivos, como o README, Código de Conduta e este guia de contribuições, podem receber novas alterações caso sejam necessárias. Abra uma issue e comece a contribuir agora mesmo.




<!-- Contribution Management
The project has a management board that determines what should or should not be prioritized. This group of developers consists of individuals with experience in both the code and the product. Over time, you can also contribute by joining the management board.

Project Development Process
Registration of an Issue:

Once an issue is registered, it can receive comments from other individuals to provide more details and improve the description of the new enhancement request, feature, or bug that needs to be addressed. Anyone can take up an open issue and implement their solution.

Assignment of an Issue:

On the issue page, you will find a complete backlog of the project. By clicking on an issue, you can assign it to yourself under "Assignees." This makes it your responsibility for development. Follow the guidelines on how to create a branch and submit a pull request.

Creating a Branch:

To start development, it is necessary to create a branch. By default, there are three types of branches: hot, feat, and bugfix:

hot -> hotfix: Branch prefix for quick and small code changes;
feat -> feature: Branch prefix for new features or improvements;
bugfix -> Branch prefix for fixing code bugs.
Understanding the prefixes for each issue type, complete the branch name suffix with "/#", followed by the issue number.
Example: "hot/#xxxx", "feat/#yyyy", "bugfix/#zzzz".
Making a Pull Request:

After implementing your solution, you should create a Pull Request for your contribution to be reviewed and incorporated into the main project. Follow the steps below:

Ensure that you have committed all relevant changes to your branch.
Access the repository page on GitHub.
Click on the "Pull Requests" tab.
Click the "New Pull Request" button.
Select your branch as the "base branch" and the main project branch as the "compare branch".
Review the proposed changes and provide a clear description of what has been done.
If necessary, mention any tasks or issues related to the Pull Request.
Click "Create Pull Request" to create the Pull Request.
Wait for the project contributors to review your changes.
During the review process, be open to comments and suggestions for improvements.
If requested, make the necessary changes and update the Pull Request.
Once the Pull Request is approved, it will be merged into the main project branch.
Remember to maintain clear and respectful communication throughout the review and collaboration process. Be receptive to feedback and be willing to collaborate with other team members. -->