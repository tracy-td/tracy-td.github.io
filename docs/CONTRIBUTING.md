# Contribuindo
 
## Índice:
- [Iniciando](#iniciando)
- [Obtendo ajuda](#obtendo-ajuda)
- [Começando a contribuir](#comeando-a-contribuir)
- [Iniciando o desnvolvimento](#iniciando-o-desenvolvimento)
- [Criando uma issue](#criando-issue)
- [Atribuindo uma issue](#atribuindo-uma-issue)
- [Submetendo contribuições](#submentendo-contribuies)
- [Contribuindo com o código](#contribuindo-com-o-cdigo)
- [Contribuindo com a documentação](#contribuindo-com-a-documentao)
- [Implementação dos testes](#implementao-dos-testes)
 
## Iniciando
 
Aconselhamos que após a leitura desse arquivo, você de uma olhada nas issues iniciais do projeto, e siga os exemplos de
como contribuir com o código.
 
## Obtendo ajuda
 
A comunidade de contribuições da Tracy-TD possui um canal de comunicação no [Discord](https://discord.gg/AwaqbGPRkd), assim
novos integrantes podem tirar suas dúvidas e interagir com outros membros.
 
## Começando a contribuir
 
Para você que é iniciante, sugerimos que pegue uma issue simples, para começar a se familiarizar com o projeto, as issue
para os iniciantes se encontram neste link (COLOCAR O LINK), essas issues possuem a Labels "good first issue".
 
## Iniciando o desenvolvimento
 
Para iniciar o desenvolvimento é necessário criar uma branch, existe como padrão,
dois tipos de branchs,  feature e bugfix:
 
- feature: Prefixo de branch para nova funcionalidade ou melhoria;
 - Nova funcionalidade: Uma nova função para a API a qual ainda não existe;
 - Melhoria: Melhoria de uma função já existente ou parte do código.
- bugfix: Prefixo de branch que corrige algum bug em código.
 
Sabendo dos prefixos de cada tipo de issue, preencha o sufixo do nome da branch
com "/" seguido do número da Issue.
 
Exemplo: "feature/xxxx", "bugfix/yyyy".
 
Criando uma branch via terminal:
- git checkout - b \<nome da branch>
 - Esse comando cria a branch com o nome passado no parâmetro (não utilizar os "<>") e ainda troca para branch atual de uso.
 
## Criando issue
 
Se você encontrou algum bug ou quer sugerir alguma funcionalidade, você pode criar uma issue nesse LINK (botar o link)
 
Para criar uma nova Issue, você pode seguir os seguintes passos, todos os passos a seguir começam ao acessar a aba de
[Issues](https://github.com/rodrigor/tracy-api/issues), ou já no template de [New issue](https://github.com/rodrigor/tracy-api/issues/new) do repositório:
 
Dentro do template de New issue, no input de "Title", escreva brevemente o que a nova issue deve fazer, e então no input
de "Leave a comment", faça uma descrição mais detalhada sobre como a issue deve ser executada/implementada. Após as especificações
da nova issue, ao lado direito existem alguns complementos importantes:
- Em "Assignees" você pode escolher a pessoa responsável para a execução da issue, caso o objetivo seja apenas deixar a issue registrada, não precisa atribuir, caso queira pegar uma issue, siga para seção [atribuindo uma issue](#atribuindo-uma-issue).
- Em "Labels" você define que tipo de feature e característica essa issue possui, como "bug", para uma issue referente a um bug no sistema, "documentation" issue que mexe com algum arquivo referente a documentação do projeto, "enhancement", para issue referente a uma nova feature ou melhoria para o sistema, existem várias labels e Issue podem receber várias labels e não são obrigatórias para a criação de uma.
 
Após esses passos a sua issue está pronta para ser criada, clique em "Submite new issue" e receba a nova issue com um "#" seguido de um valor numérico, um identificador para a issue, e este identificador será utilizado no comentário do seu Pull Request para ser feito o link entre a issue e o Pull Request.
 
## Atribuindo uma issue
 
Para atribuir uma issue, você precisa acessar a aba de [Issues](https://github.com/rodrigor/tracy-api/issues), ao selecionar uma issue,
ela será aberta e poderá receber atribuição(ões) ao clicar em "Assignees", então selecionar quem deverá fazer parte do desenvolvimento dessa issue.
Lembrando que em Assigness, não serão as mesmas pessoas que irão revisar o seu [Pull Request](#fazendo-pull-request).
 
## Submetendo contribuições
 
Ao concluir a sua contribuição é hora de fazer o famoso Pull Request, onde ele será revisado pela comunidade e então,
se tudo estiver de acordo com as expectativas dos revisores, o Pull Request será aceito. Mas para isso, é preciso seguir alguns passos
primeiro, é preciso preparar os arquivos que serão adicionados para o commit e consequentemente para o Pull Request/Revisão, com os seguintes passos no terminal:
 
- ```git add "{nome do arquivo}" ``` ou ```git add .```, que adiciona o arquivo mencionado ou todos os arquivos salvos e
modificados ao Stage, também pode ser chamado de Index ou Staging Area:
 - O Staging Area é um lugar onde os arquivos estão sendo preparados para o commit.
- ```git commit -m "{mensagem do commit}"```, com esse comando você transfere seus arquivos para o diretório local do git com uma mensagem sobre o commit, muito importante que essa mensagem contenha informações sobre as alterações feitas e referência issue associada a contribuição:
 - A mensagem do commit deve conter uma referência a issue, essa referência é feita através de ```#``` seguido do número de
identificação da issue no github, seguido de uma breve descrição do que foi feito.
- ```git push```, com o git push, os arquivos serão enviados para o repositório da nuvem do github:
 - É possível que peça suas credenciais, informe elas e continue o procedimento;
 - Caso a branch ainda não exista no repositório do github, será exibido uma mensagem para no terminal para publicar a branch,
copie a mensagem e execute para subir suas alterações;
 - No repositório do github do projeto, ao estar logado com as credenciais iguais as informadas, será exibido uma mensagem informado que
existe um Pull Request para ser solicitado...
 
## Contribuindo com o código
 
Para contribuição de código temos 3 categorias para uma issue:
- Nova funcionalidade, são acréscimos de novas funções ou recursos que ainda não existem no projeto, e possui como título da branch "feature".
- Melhoria, são mudanças em funções ou recursos que já existem no projeto, possuindo o título de branch "feature".
- Bug, os bugs são divididos em dois, críticos e não críticos, ambos possuem o título de branch "bugfix":
 - Críticos, afetam gravemente alguma funcionalidade importante do sistema, o que torna a aplicação inutilizável ou de difícil acesso.
 - Não críticos, são os bugs que causam apenas um leve incômodo na aplicação, onde não chegam a causar tanto impacto na funcionalidade.
 
## Contribuindo com a documentação
 
A documentação de um software sempre muda de acordo com as novas funcionalidades que são desenvolvidas, desta forma,
atualizações são necessárias para que o software e documentação estejam sempre alinhados, essa é um tipo de contribuição
importante para manter a integridade entre os desenvolvedores e quem faz uso da ferramenta. Veja a documentação aqui.(COLOCAR LINK)
 
Outros arquivos como o README, Código de conduta e o este guia de contribuições podem receber novas alterações se forem
necessárias, abra uma issue e comece a contribuir agora mesmo.
 
## Implementação dos testes
 
Para a contribuição de teste, a um [Guia de teste](test-guia.md) para auxiliar na implementação dos mesmos.
 

