
# ScriptIAHelpForZabbix

Este script permite que o Zabbix envie alertas para a API Gemini (Google AI), solicitando sugestões de causas e soluções para incidentes detectados. Ele gera respostas concisas com possíveis causas, comandos de depuração e medidas preventivas.

## 📌 Requisitos

- Zabbix 6.0 ou superior
- Chave de API válida da [API Gemini](https://ai.google.dev/)
- Acesso à internet para chamadas HTTP

## ⚙️ Parâmetros obrigatórios

O script espera os seguintes parâmetros no campo `value` do webhook (em formato JSON):

```json
{
  "alert_subject": "{TRIGGER.NAME}",
  "ip_address": "{HOST.IP}",
  "api_key": "SUA_CHAVE_GEMINI"
}
```

## 🔤 Parâmetro opcional

- `language`: Define o idioma da resposta (ex: `"English"`, `"Português"`, `"pt-BR"`). Se não for definido, o script sugerirá que o usuário forneça esse parâmetro.

## 🧠 O que o script faz

1. **Validação**: Verifica se os parâmetros obrigatórios estão presentes e não vazios.
2. **Formatação**: Cria uma mensagem com detalhes do alerta e solicita uma resposta concisa da API Gemini.
3. **Requisição**: Envia a mensagem para a API Gemini e processa a resposta.
4. **Sugestão de idioma**: Se o parâmetro `language` não for fornecido, adiciona uma dica para o usuário incluir esse parâmetro.

## 🛠️ Exemplo de uso no Zabbix

Configure um webhook no Zabbix com o seguinte conteúdo no campo `value`:

```json
{
  "alert_subject": "{TRIGGER.NAME}",
  "ip_address": "{HOST.IP}",
  "api_key": "SUA_CHAVE_GEMINI",
  "language": "Português"
}
```

## 📝 Exemplo de resposta gerada

> The alert: High CPU Usage, with the IP: 192.168.1.10 occurred in Zabbix.  
> Possible causes:  
> - High load due to intensive processes  
> - Insufficient resources  
> Suggested actions:  
> - Check running processes  
> - Optimize resource usage  
> - Consider hardware upgrades  
>  
> Kindly do not use any text formatting such as *.  
> And reply to me in the language: Português.
