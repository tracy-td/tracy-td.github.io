# Como configurar Jira com Tracy

## **Criando webhook no Jira** 

* Após efetuar o login, vá na engrenagem de configurações e clique em "Sistema".

* Desça na aba esquerda da página até chegar na área "Avançados", assim clique em "WebHooks".

* Selecione "Criar um webhook".

* Na URL do seu webhook, para testes foi usado a plataforma "ngrok", para usar essa plataforma inicie ela com o seguinte comando "docker run --net=host -it ngrok/ngrok http 9090", copie a URL externa que aparecerá no output do comando. No final a URL do webhook deve seguir o padrão: **URL externa do ngrok**/api/v1/jira-webhook/**Seu token do Tracy**.

* Em "itens" selecione **criado**, **atualizado** e **excluído**, após isso pode finalizar criando seu webhook.

---

## **Criando um Custom Field** 

* Após efetuar o login, vá na engrenagem de configurações e clique em "Itens".

* Desça na aba esquerda da página até chegar na área "Campos", assim clique em "Campos personalizados".

* Selecione "Criar campo personalizado" e escolha a opção "Botões de escolha (radio buttons)".

* Como recomendação colocar o nome do campo de "Technical Debt".

* Adicione as opções de "sim" e "não" e crie seu campo.

* Clique em atualizar.

* Procure por seu campo e selecione ele.

* Vá em "editar detalhes".

* Clique na URL da página e copie o id do custom field que aparecerá como no exemplo: **"id=XXXXX"**.

---

## **Vincule a Custom Field ao seu projeto no Jira** 

* Acesse o seu projeto.

* Desça na aba esquerda da página e clique em "Configurações do projeto".

* Desça de novo na aba esquerda da página e clique em "Tipos de item".

* Selecione o item "Task".

* Desça na aba da direita da página até "Campos sugeridos", procure por sua custom field, arraste ela para "Campos de descrição" e salve a alteração.

---

## **Vincule a Custom Field ao seu Tracy**

* Após efetuar o login, clique no menu no canto superior esquerdo.

* Selecione "Settings" e depois "Admin Settings".

* Vá na aba "Integretions".

* Cole no campo "Technical Debt Custom Field Code" o id da sua custom field que representa uma technical debt.

---

## **Criando sua task no Jira**

Agora, não se esqueça de sempre que criar uma task no jira que seja uma technical debt marque ela como "sim".