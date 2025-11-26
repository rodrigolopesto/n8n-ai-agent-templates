# 🤖 Guia de Instalação: Agente de Atendimento IA com Z-API + n8n

Este guia vai te ajudar a configurar um agente de atendimento completo usando Z-API, n8n e OpenAI. 

## 🎯 Funcionalidades do Template

- **Recepção de Mensagens**: Recebe mensagens do WhatsApp via Z-API.
- **Inteligência Artificial**: Usa OpenAI (GPT-4o-mini) para entender e gerar respostas.
- **Memória de Conversa**: Mantém o contexto das últimas 10 interações com cada usuário.
- **Envio de Respostas**: Envia a resposta da IA de volta para o usuário no WhatsApp.

---

## 📋 Pré-requisitos

Antes de começar, você vai precisar de:

1.  **Conta na Z-API**: Com uma instância criada e o celular conectado.
    -   Seu `Instance ID`
    -   Seu `Token`
2.  **Conta na OpenAI**: Com uma chave de API (`API Key`).
3.  **n8n instalado**: Sua instância do n8n já está pronta na VPS!

---

## 🔧 Passo a Passo da Configuração

### **Passo 1: Importar o Template no n8n**

1.  **Copie o conteúdo** do arquivo `agente-atendimento-zapi.json` que preparei para você.
2.  No seu n8n, vá para a tela de **Workflows**.
3.  Clique em **"Add workflow"** e depois em **"Import from file"** ou **"Import from clipboard"**.
4.  Cole o conteúdo do JSON e clique em **Import**.

O workflow aparecerá na sua tela.

### **Passo 2: Configurar Variáveis de Ambiente no n8n**

Para manter suas chaves seguras, vamos usar variáveis de ambiente.

1.  No seu n8n, vá em **Settings > Environment Variables**.
2.  Clique em **"Add variable"** e adicione as seguintes variáveis:

| Chave              | Valor                                  | Descrição                     |
| ------------------ | -------------------------------------- | ------------------------------- |
| `ZAPI_INSTANCE_ID` | `SEU_INSTANCE_ID_DA_ZAPI`              | ID da sua instância na Z-API.   |
| `ZAPI_TOKEN`       | `SEU_TOKEN_DA_ZAPI`                    | Token da sua instância na Z-API.|

Salve as alterações.

### **Passo 3: Configurar Credenciais do OpenAI**

1.  No n8n, vá em **Credentials > Add credential**.
2.  Procure por **"OpenAI API"** e selecione.
3.  No campo **"API Key"**, cole a sua chave da API da OpenAI.
4.  Dê um nome para a credencial (ex: `Minha OpenAI`) e salve.
5.  No workflow, clique no nó **"OpenAI Chat"**, selecione a credencial que você acabou de criar no campo **"Credential for OpenAI API"**.

### **Passo 4: Configurar o Webhook na Z-API**

Agora, precisamos dizer para a Z-API para onde enviar as mensagens recebidas.

1.  No workflow do n8n, encontre o nó **"Webhook Z-API"**.
2.  Copie a URL do webhook. Ela terá o formato:
    -   **Test URL**: `http://SEU_IP:5678/webhook-test/....`
    -   **Production URL**: `http://SEU_IP:5678/webhook/....`
    > **Use a URL de Produção (Production URL)!**

3.  Vá para o painel da sua instância na **Z-API**.
4.  Procure pela seção **"Webhooks"**.
5.  No campo **"Mensagens Recebidas (on-message-received)"**, cole a **Production URL** que você copiou do n8n.
6.  Salve as configurações na Z-API.

### **Passo 5: Ativar o Workflow**

1.  Volte para o n8n.
2.  No canto superior direito, ative o workflow clicando no botão **"Active"**.

**Pronto! Seu agente de atendimento está funcionando!** 🎉

---

## 🧪 Como Testar

1.  Envie uma mensagem de qualquer número para o WhatsApp que você conectou na Z-API.
2.  Aguarde alguns segundos.
3.  Você deverá receber uma resposta gerada pela IA!

---

## 🐛 Solução de Problemas

-   **Não recebi resposta**: 
    -   Verifique os logs de execução no n8n para ver se há erros.
    -   Confirme se a URL do webhook na Z-API está correta (use a de produção).
    -   Verifique se suas credenciais da OpenAI e as variáveis da Z-API estão corretas.

-   **Erro no nó OpenAI**: 
    -   Verifique se sua chave da API da OpenAI é válida e se você tem créditos na sua conta.

-   **Erro no nó Z-API**: 
    -   Confirme se o `Instance ID` e o `Token` estão corretos nas variáveis de ambiente do n8n.

---

Qualquer dúvida, é só me chamar!
