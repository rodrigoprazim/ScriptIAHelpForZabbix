# ScriptIAHelpForZabbix

This script allows Zabbix to send alerts to the Gemini API (Google AI), requesting suggestions for possible causes and solutions for detected incidents. It generates concise responses with potential causes, debugging commands, and preventive measures.

## 📌 Requirements

* Zabbix 7.0 or higher
* A valid API key from [Gemini API](https://aistudio.google.com/app/apikey)
* Internet access for HTTP requests

## ⚙️ Required Parameters

The script expects the following parameters in the webhook `value` field:

* `alert_subject`: `{TRIGGER.NAME}`
* `ip_address`: `{HOST.IP}`
* `api_key`: `YOUR_GEMINI_KEY`

## 🌤️ Optional Parameter

* `language`: Defines the response language (e.g., `"Portuguese"`, `"pt-BR"`, `"Spanish"`). If not provided, the script will suggest that the user include this parameter. The default is English.

## 🧠 What the Script Does

1. **Validation**: Checks whether the required parameters are present and not empty.
2. **Formatting**: Creates a message with alert details and requests a concise response from the Gemini API.
3. **Request**: Sends the message to the Gemini API and processes the response.
4. **Language Suggestion**: If the `language` parameter is not provided, adds a tip suggesting the user to include it.

## 🛠️ Example Usage in Zabbix

* Go to “Alerts” > “Scripts” > “Create Script”

```json
{
  "alert_subject": "{TRIGGER.NAME}",
  "ip_address": "{HOST.IP}",
  "api_key": "YOUR_GEMINI_KEY",
  "language": "PT-BR"
}
```

![Alert Example](images/new_script.png)

* Access the alert panel and select a specific alert.

![Access Example](images/access_ia.png)

## 📝 Example of Generated Response

> The alert: High CPU Usage, with the IP: 192.168.1.10 occurred in Zabbix.
> Possible causes:
>
> * High load due to intensive processes
> * Insufficient resources
>   Suggested actions:
> * Check running processes
> * Optimize resource usage
> * Consider hardware upgrades

## ⭐ Star History

<a href="https://www.star-history.com/#rodrigoprazim/ScriptIAHelpForZabbix&Date">
 <picture>
   <source media="(prefers-color-scheme: dark)" srcset="https://api.star-history.com/svg?repos=rodrigoprazim/ScriptIAHelpForZabbix&type=Date&theme=dark" />
   <source media="(prefers-color-scheme: light)" srcset="https://api.star-history.com/svg?repos=rodrigoprazim/ScriptIAHelpForZabbix&type=Date" />
   <img alt="Star History Chart" src="https://api.star-history.com/svg?repos=rodrigoprazim/ScriptIAHelpForZabbix&type=Date" />
 </picture>
</a>
