# 🚀 Guia Rápido: Configurar Agente IA no n8n com Z-API

## ✅ O Que Você Vai Precisar

### Z-API
- **Instance ID** (encontre no painel da Z-API)
- **Token** (encontre no painel da Z-API)

### OpenAI
- **API Key** (crie em https://platform.openai.com/api-keys)

---

## 📋 Passo a Passo Simplificado

### **1. Verificar Chave OpenAI**

Primeiro, vamos verificar se sua chave OpenAI está funcionando:

1. Acesse: https://platform.openai.com/api-keys
2. Verifique se a chave que você tem está ativa
3. Se necessário, crie uma nova chave
4. **IMPORTANTE:** Verifique se você tem créditos na conta OpenAI

### **2. Importar Template no n8n**

1. No n8n, vá em **Workflows**
2. Clique em **"Create workflow"**
3. No menu superior, clique nos 3 pontinhos e depois em **"Import from URL"**
4. Cole esta URL:
```
https://raw.githubusercontent.com/rodrigolopesto/n8n-ai-agent-templates/main/agente-atendimento-zapi.json
```
5. Clique em **Import**

### **3. Configurar Credencial OpenAI**

1. No n8n, vá em **Credentials** (menu lateral)
2. Clique em **"Create credential"**
3. Busque por **"OpenAI"** e selecione
4. Cole sua **API Key** da OpenAI
5. Clique em **"Save"**

### **4. Configurar Webhook Z-API**

#### No n8n:

1. No workflow, clique no nó **"Webhook Z-API"** (primeiro nó)
2. Copie a **Production URL** que aparece
   - Exemplo: `http://SEU_IP:5678/webhook/webhook-zapi`

#### Na Z-API:

1. Acesse: https://api.z-api.io/instances
2. Clique na sua instância
3. Vá em **"Webhooks"**
4. No campo **"Mensagens Recebidas"** ou **"on-message-received"**, cole a URL que você copiou do n8n
5. Clique em **"Salvar"**

### **5. Configurar Nó de Envio Z-API**

No workflow do n8n:

1. Encontre o nó **"Enviar Resposta Z-API"** ou **"HTTP Request"** que envia mensagens
2. Clique nele
3. Na URL, substitua pelos seus dados:
```
https://api.z-api.io/instances/SEU_INSTANCE_ID/token/SEU_TOKEN/send-text
```

**Exemplo:**
```
https://api.z-api.io/instances/3E7A4AFC12F4D081CBC1BEF0AADBDFFC/token/72E99550A0E5769E395E78DB/send-text
```

### **6. Ativar o Workflow**

1. No canto superior direito, clique no botão **"Inactive"** para mudar para **"Active"**
2. O workflow agora está rodando!

---

## 🧪 Testar o Agente

1. Envie uma mensagem para o WhatsApp conectado na Z-API
2. Aguarde alguns segundos
3. Você deve receber uma resposta automática da IA!

---

## 🎨 Personalizar o Agente

### Mudar o Comportamento da IA

1. No workflow, encontre o nó **"Prompt do Agente"** ou **"Prompt Template"**
2. Clique nele
3. Edite o texto para personalizar:

**Exemplo para Vendas:**
```
Você é um assistente de vendas da [SUA EMPRESA].

Seu objetivo é:
- Apresentar nossos produtos de forma persuasiva
- Coletar nome, telefone e email do cliente
- Responder dúvidas sobre preços
- Agendar reuniões

Produtos:
1. [Produto A] - R$ X
2. [Produto B] - R$ Y

Seja educado, proativo e não invasivo.
```

**Exemplo para Suporte:**
```
Você é um assistente de suporte técnico da [SUA EMPRESA].

Seu objetivo é:
- Resolver problemas comuns dos clientes
- Coletar informações sobre o problema
- Encaminhar para humano se necessário

Problemas comuns:
- Esqueci minha senha
- Produto não funciona
- Como fazer [ação]

Seja paciente e técnico, mas use linguagem simples.
```

**Exemplo para Atendimento Geral:**
```
Você é um assistente virtual inteligente e prestativo.

Seu objetivo é:
- Responder perguntas de forma clara e objetiva
- Ser educado e profissional
- Manter conversas naturais e contextualizadas
- Ajudar o cliente da melhor forma possível

Nome do cliente: {{ $json.name }}
Mensagem: {{ $json.message }}

Responda de forma amigável e útil. Mantenha as respostas concisas (máximo 3 parágrafos).
```

---

## 🐛 Problemas Comuns

### "Não recebo mensagens no n8n"

✅ Verifique se a URL do webhook está correta na Z-API  
✅ Use a **Production URL**, não a Test URL  
✅ Confirme se o workflow está **Active**

### "OpenAI dá erro"

✅ Verifique se sua chave está correta  
✅ Confirme se você tem créditos na conta OpenAI  
✅ Teste a chave em: https://platform.openai.com/playground

### "Z-API não envia resposta"

✅ Verifique se o Instance ID e Token estão corretos  
✅ Confirme se o WhatsApp está conectado na Z-API  
✅ Teste enviando uma mensagem manualmente pela API da Z-API

---

## 💡 Dicas Importantes

1. **Custos:**
   - OpenAI cobra por token usado (geralmente centavos por conversa)
   - Z-API tem plano gratuito limitado

2. **Performance:**
   - Use `gpt-4o-mini` para respostas mais rápidas e baratas
   - Limite a memória de conversa para economizar tokens

3. **Segurança:**
   - Nunca compartilhe suas chaves de API
   - Use variáveis de ambiente quando possível
   - Não publique credenciais no GitHub

---

## 📞 Precisa de Ajuda?

- **Documentação Z-API:** https://docs.z-api.io/
- **Documentação OpenAI:** https://platform.openai.com/docs
- **Comunidade n8n:** https://community.n8n.io/
- **Repositório GitHub:** https://github.com/rodrigolopesto/n8n-ai-agent-templates

---

**Desenvolvido por Manus AI Assistant** 🤖
