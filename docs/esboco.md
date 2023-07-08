# ESBOÇO DE REGRAS TRACY

Este documento é um rascunho. As regras migrarão para a documentação oficial em breve.

## **Integração com o Jira.**

### Ciclo de vida

  - O Jira envia um push para o endpoint de Tracy a cada alteração nas issues do projeto.
    - TODO: Informar a configuração do endpoint (em que eventos o endpoint deve ser chamado?)
    *  

  * issueJira é uma issue no Jira.
  * Quando o campo customizado "Technical Debt" é marcado com valor `sim`:
    * Tracy receberá o push e criará uma nova issue, que será exibida na lista de issues.
    * O usuário pode importar esta issue em uma nova dívida técnica.
     * a nova dívida técnica está relacionada à issue da qual foi importada. Tracy monitorará as mudanças de estado desta issue e atualizará o estado de Tracy.
    * Quando a issueJira, muda de estado, a dívida também muda de estado.
     * TODO: informar a equivalência de estados entre as issues do Jira e das dívidas em Tracy.
    * Quando uma issueJira é apagada, se uma dívida já tiver sido criada a partir desta issue, a relação da dívida com esta issue é desfeita, MAS A DÍVIDA, EM TRACY, NÃO É APAGADA!
     * O ID da issueJira que está registrada na dívida é apagada. 
  * Criar um 