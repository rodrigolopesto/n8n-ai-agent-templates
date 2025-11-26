# 🤖 Templates de Agente de Atendimento IA para n8n

Templates prontos para criar agentes de atendimento inteligentes usando n8n, integrados com WhatsApp e OpenAI.

## 📦 Templates Disponíveis

### 1. **Agente de Atendimento Z-API** ⭐ Recomendado

Template completo de agente de atendimento com IA usando Z-API (solução brasileira).

**Funcionalidades:**
- ✅ Recebe mensagens do WhatsApp via Z-API
- ✅ Processa com OpenAI GPT-4o-mini
- ✅ Mantém memória de conversa (10 interações)
- ✅ Responde automaticamente no WhatsApp
- ✅ Personalização completa do comportamento da IA

**Arquivos:**
- `agente-atendimento-zapi.json` - Template do workflow
- `GUIA_CONFIGURACAO_ZAPI.md` - Guia completo de instalação

---

## 🚀 Como Usar

### Requisitos

1. **n8n instalado** (use nosso [instalador automático](https://github.com/rodrigolopesto/n8n-installer))
2. **Conta na Z-API** com instância criada
3. **Chave de API da OpenAI**

### Instalação Rápida

1. **Baixe o template:**
```bash
wget https://raw.githubusercontent.com/rodrigolopesto/n8n-ai-agent-templates/main/agente-atendimento-zapi.json
```

2. **Importe no n8n:**
   - Vá em **Workflows** → **Import from file**
   - Selecione o arquivo baixado

3. **Configure as credenciais:**
   - Siga o [Guia de Configuração](GUIA_CONFIGURACAO_ZAPI.md)

---

## 📚 Documentação

### Guias Disponíveis

- [📖 Guia Completo de Configuração Z-API](GUIA_CONFIGURACAO_ZAPI.md)

### Vídeos Tutoriais

Em breve!

---

## 🎯 Casos de Uso

Este template é perfeito para:

- **Atendimento ao Cliente** - Responder dúvidas frequentes automaticamente
- **Vendas** - Qualificar leads e agendar reuniões
- **Suporte Técnico** - Resolver problemas comuns
- **Agendamentos** - Marcar consultas e compromissos
- **FAQ Inteligente** - Base de conhecimento conversacional

---

## 🔧 Personalização

### Modificar o Comportamento da IA

Edite o nó **"Prompt do Agente"** no workflow para mudar:

- Tom de voz (formal, casual, técnico)
- Objetivo do atendimento
- Informações específicas do seu negócio
- Regras de comportamento

**Exemplo de prompt personalizado:**

```
Você é um assistente de vendas da empresa XYZ.

Seu objetivo é:
- Apresentar nossos produtos de forma persuasiva
- Coletar informações de contato do cliente
- Agendar demonstrações
- Responder dúvidas sobre preços e condições

Produtos disponíveis:
1. Produto A - R$ 100
2. Produto B - R$ 200
3. Produto C - R$ 300

Seja educado, proativo e não invasivo.
```

### Adicionar Funcionalidades

Você pode expandir o template adicionando:

- **Banco de dados** - Salvar conversas e leads
- **CRM** - Integrar com Pipedrive, HubSpot, etc.
- **Agendamento** - Conectar com Google Calendar
- **Pagamentos** - Integrar com Stripe, Mercado Pago
- **Remarketing** - Sistema de follow-up automático

---

## 🛡️ Boas Práticas

### Segurança

- ✅ Use variáveis de ambiente para chaves de API
- ✅ Nunca exponha suas credenciais no código
- ✅ Configure HTTPS se usar em produção

### Performance

- ✅ Limite o tamanho da memória de conversa (padrão: 10)
- ✅ Use modelos mais leves para respostas rápidas (gpt-4o-mini)
- ✅ Configure timeout adequado nos nós HTTP

### Custos

- 💰 OpenAI cobra por token usado
- 💰 Z-API tem planos pagos após o período gratuito
- 💡 Monitore o uso para evitar surpresas

---

## 🐛 Solução de Problemas

### Webhook não recebe mensagens

1. Verifique se a URL do webhook está correta na Z-API
2. Use a **Production URL**, não a Test URL
3. Confirme se o workflow está **ativo** no n8n

### Erro de autenticação OpenAI

1. Verifique se a chave de API está correta
2. Confirme se você tem créditos na conta OpenAI
3. Teste a chave em: https://platform.openai.com/api-keys

### Resposta lenta ou timeout

1. Reduza o `maxTokens` no nó OpenAI (padrão: 500)
2. Use um modelo mais rápido (gpt-4o-mini)
3. Aumente o timeout do nó HTTP Request

---

## 📞 Suporte

- **Issues**: Abra uma issue neste repositório
- **Comunidade n8n**: [community.n8n.io](https://community.n8n.io/)
- **Documentação Z-API**: [docs.z-api.io](https://docs.z-api.io/)
- **Documentação OpenAI**: [platform.openai.com/docs](https://platform.openai.com/docs)

---

## 📝 Licença

Este projeto é fornecido "como está", sem garantias. Use por sua conta e risco.

---

## 🙏 Créditos

**Desenvolvido com ❤️ por Manus AI Assistant**

Baseado nas melhores práticas da comunidade n8n e feedback de usuários reais.

---

## 🔗 Links Úteis

- [Instalador n8n para Ubuntu](https://github.com/rodrigolopesto/n8n-installer)
- [Documentação oficial n8n](https://docs.n8n.io/)
- [Templates da comunidade n8n](https://n8n.io/workflows/)
- [Z-API](https://www.z-api.io/)
- [OpenAI Platform](https://platform.openai.com/)
