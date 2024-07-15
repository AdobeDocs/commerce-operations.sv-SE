---
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '144'
ht-degree: 0%

---
# CLI-alternativ för kunder som använder meddelandekön

| Namn | Beskrivning | Värde | Obligatoriskt |
|------|-------------|-------|----------|
| `--consumers-wait-for-messages` | Bestämmer om konsumenterna ska vänta på ett meddelande från kön. | 1 - Ja, 0 - Nej | Nej |

* `0`: Konsumenterna bearbetar tillgängliga meddelanden i kön, stänger TCP-anslutningen och avslutar. Konsumenterna väntar inte på att ytterligare meddelanden ska skickas till kön, även om antalet bearbetade meddelanden är mindre än värdet `--max_messages` som angavs när konsumenterna startades.

* `1`: Konsumenterna fortsätter att bearbeta meddelanden från meddelandekön tills det maximala antalet meddelanden (det värde som anges för `--max_messages` i kommandot `queue:consumers:start`) nås innan TCP-anslutningen stängs och konsumentprocessen avslutas. Om kön töms innan `--max_messages` nås väntar konsumenten på att fler meddelanden ska komma fram. Om du använder arbetare för att köra konsumenter i stället för att använda ett cron-jobb anger du den här variabeln till `1`.

>[!WARNING]
>
>Alternativet `--consumers-wait-for-messages` är ett globalt alternativ och kan inte konfigureras separat för varje konsument.
