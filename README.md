# Identificador de Propostas com IA

Automação no **n8n** que monitora e-mails novos no Gmail, qualifica leads com IA e organiza tudo de forma inteligente.

### O que o workflow faz
- Verifica a caixa de entrada do Gmail a cada 5 minutos.
- Filtra e-mails com palavras-chave no assunto (lead, proposta, orçamento, negócio, etc.).
- Usa IA (Groq + Llama 3.3) para classificar o lead como **quente** (intenção de compra imediata) ou **frio** (apenas informação).
- Salva os leads qualificados em Google Sheets (planilhas separadas para quente/frio).
- Envia follow-up automático (para quente) ou alerta no Slack (para frio não respondido em 3 dias).

### Tecnologias utilizadas
- n8n (core da automação)
- Gmail (leitura de e-mails novos)
- Groq (IA para qualificação)
- Google Sheets (log e CRM simples)
- Slack (alertas para follow-up)

### Como usar / importar
1. Importe o arquivo `Identificador de Propostas com IA.json` no seu n8n.
2. Configure as credenciais reais:
   - Gmail OAuth2 (para ler e-mails)
   - Groq API (para IA)
   - Slack OAuth2 (para alertas)
   - Google Sheets OAuth2 (para log)
3. Substitua os placeholders:
   - `YOUR_GOOGLE_SHEETS_ID`: ID da sua planilha Google Sheets
   - `YOUR_SLACK_CHANNEL_ID`: ID do canal Slack para alertas
4. Ative o workflow e teste enviando e-mails com palavras-chave no assunto.

### Observações importantes
- O workflow roda a cada 5 minutos (pode ajustar o polling para economizar quota).
- Só processa e-mails novos/não lidos (evita duplicatas).
- Para produção 24/7: Hospede o n8n em VPS (ex: AWS, Railway) com auto-restart.
