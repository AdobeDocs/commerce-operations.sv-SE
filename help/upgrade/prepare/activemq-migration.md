---
title: Migrera från RabbitMQ till ActiveMQ
description: Läs om hur du ersätter meddelandeköhanteraren som används för lokala installationer av Adobe Commerce.
feature: Services, Configuration
source-git-commit: 7610a5843b526a765dd35188722b7be8e6051049
workflow-type: tm+mt
source-wordcount: '649'
ht-degree: 0%

---

# Migrerar till ActiveMQ

ActiveMQ (Apache ActiveMQ Artemis) är en meddelandeförmedlare med höga prestanda och flera protokoll som erbjuder ett alternativ till RabbitMQ för hantering av meddelandeköer i Adobe Commerce.

Från och med 2.4.8-p3, 2.4.7-p8, 2.4.6-p13 och 2.4.5-p16 stöder Adobe Commerce ActiveMQ som meddelandeköansvarig. Detta ger ytterligare flexibilitet för lokala installationer att välja mellan RabbitMQ och ActiveMQ baserat på deras infrastrukturkrav och expertis.

## Innan du börjar

Innan du startar migreringen bör du kontrollera följande:

1. Granska din nuvarande RabbitMQ-konfiguration i `app/etc/env.php`.
1. Gör en fullständig säkerhetskopiering av databasen och koddatabasen.
1. Kontrollera att installationen uppfyller systemkraven för ActiveMQ.
1. Planera för ett underhållsfönster för att slutföra migreringen.

## Migreringssökväg

Att migrera till ActiveMQ är en enkel process, men det är viktigt att se till att alla väntande meddelanden behandlas innan man byter mäklare.

Dessa migreringsanvisningar förutsätter att Adobe Commerce är det enda programmet som använder meddelandeköhanteraren.

### Steg 1: Placera platsen i underhållsläge

1. Placera platsen i [underhållsläge](../../installation/tutorials/maintenance-mode.md):

   ```bash
   bin/magento maintenance:enable
   ```

1. Verifiera att underhållsläget är aktiverat:

   ```bash
   bin/magento maintenance:status
   ```

### Steg 2: Kontrollera antalet RabbitMQ-meddelanden

Kontrollera att alla meddelanden i RabbitMQ har bearbetats innan du fortsätter. Använd någon av följande metoder:

#### Metod A: Använda kontrollpanelen för RabbitMQ-hantering

1. Åtkomst till gränssnittet för RabbitMQ-hantering på `http://<host>:15672`
1. Standardautentiseringsuppgifter: `guest/guest`
1. Navigera till fliken **Köer**
1. Verifiera att alla köer visar **0 meddelanden**

   ![Kontrollpanel för RabbitMQ-hantering](../../assets/upgrade-guide/rabbitmq_mgmt_dashboard.png)

#### Metod B: Använda kommandoraden kaninitmqctl

1. Kontrollera alla köer och antalet meddelanden:

   ```bash
   rabbitmqctl list_queues name messages consumers
   ```

   <img src="../../assets/upgrade-guide/rabbitmqctl.png" alt="CLI-utdata för KaninMQ" width="500" />

1. Kontrollera detaljerad köinformation:

   ```bash
   rabbitmqctl list_queues name messages messages_ready messages_unacknowledged consumers
   ```

   <img src="../../assets/upgrade-guide/rabbitmqctl_detailed.png" alt="CLI-utdata för RabbitMQ" width="500" />

### Steg 3: Bearbeta väntande meddelanden

Om det finns väntande meddelanden i någon kö bearbetar du dem innan du fortsätter.

1. Få en lista över tillgängliga konsumenter:

   ```bash
   bin/magento queue:consumers:list
   ```

1. Bearbeta konsumenter som en grupp eller som en enskild meddelandekö:

   - **Bearbeta konsumenter som en grupp**

     ```bash
     bin/magento cron:run --group=consumers
     ```

     >[!NOTE]
     >
     >Om cron redan körs i systemet behöver du inte köra `bin/magento cron:run --group=consumers` manuellt. Kontrollera i stället att meddelanden behandlas genom att kontrollera antalet meddelanden med kommandona från steg 2.

   - **Bearbeta en specifik meddelandekö**

     ```bash
     bin/magento queue:consumers:start <consumer_name> --max-messages=<number>
     ```

     Så här bearbetar du asynkrona åtgärder:

     ```bash
     bin/magento queue:consumers:start async.operations.all --max-messages=1000
     ```

     >[!NOTE]
     >
     >Parametern `--max-messages` begränsar antalet meddelanden som ska bearbetas innan konsumenten stannar. Justera det här värdet baserat på din köstorlek.

   - **Övervaka meddelandebearbetning**

     Kontrollera antalet meddelanden kontinuerligt tills alla köer är tomma:

     ```bash
     # Check every few seconds until 0 messages remain
     watch -n 5 "rabbitmqctl list_queues name messages | grep -v '^Listing' | grep -v '0$'"
     ```

### Steg 4: Verifiera att alla meddelanden har bearbetats

Kontrollera att **alla köer visar 0 meddelanden** innan du fortsätter till nästa steg. Kör verifieringskommandona från steg 2 igen.

>[!WARNING]
>
>Gå inte vidare till nästa steg om några meddelanden förblir obearbetade. Dataförlust kan inträffa om du byter mäklare medan meddelanden fortfarande väntar.

### Steg 5: Stoppa konsumenter och kronijobb

1. Stoppa alla användare av meddelandekön som körs:

   ```bash
   # If using supervisor
   supervisorctl stop all
   
   # Or manually kill consumer processes
   pkill -f "queue:consumers:start"
   ```

1. Inaktivera cron-jobb:

   ```bash
   bin/magento cron:remove
   ```

1. Kontrollera att cron-jobb har tagits bort:

   ```bash
   crontab -l
   ```

### Steg 6: Säkerhetskopiera aktuell konfiguration

Skapa en säkerhetskopia av din aktuella konfiguration:

```bash
cp app/etc/env.php app/etc/env.php.backup.rabbitmq
```

### Steg 7: Avinstallera eventuellt RabbitMQ

Du kan avinstallera RabbitMQ om det inte behövs längre.

### Steg 8: Installera och konfigurera ActiveMQ i Adobe Commerce

Information om hur du slutför installations- och konfigurationsåtgärder för ActiveMQ, som att konfigurera STOMP-protokollet och verifiera anslutningen, finns i [installations- och konfigureringshandboken](../../installation/prerequisites/activemq.md).

### Steg 9: Installera om cron-jobb

1. När testningen är klar installerar du om cron-jobb:

   ```bash
   bin/magento cron:install
   ```

1. Kontrollera att cron-jobb är schemalagda:

   ```bash
   crontab -l
   ```

### Steg 10: Inaktivera underhållsläge

1. När du har verifierat att allt fungerar som det ska kan du inaktivera underhållsläget:

   ```bash
   bin/magento maintenance:disable
   ```

1. Kontrollera att underhållsläget är inaktiverat:

   ```bash
   bin/magento maintenance:status
   ```

### Steg 11: Övervaka systemet

Övervaka datorn 24-48 timmar efter migreringen för att se till att alla köåtgärder fungerar korrekt:

- Kontrollera regelbundet att ActiveMQ-webbkonsolen innehåller information
- Övervaka programloggar för körelaterade fel
- Kontrollera att asynkrona åtgärder (spara i config, exportera osv.) fungerar
- Kontrollera kronloggarna för att se till att konsumenterna kör

```bash
# Monitor system logs for queue activity
tail -f var/log/system.log | grep -i queue

# Monitor cron logs
tail -f var/log/cron.log

# Check running consumer processes
ps aux | grep "queue:consumers:start"
```

## Återställning

Om problem uppstår under eller efter migreringen kan du återställa till RabbitMQ:

1. Aktivera underhållsläge:

   ```bash
   bin/magento maintenance:enable
   ```

1. Stoppa alla konsumenter och avaktivera kron:

   ```bash
   pkill -f "queue:consumers:start"
   bin/magento cron:remove
   ```

1. Återställ den tidigare konfigurationen:

   ```bash
   cp app/etc/env.php.backup.rabbitmq app/etc/env.php
   ```

1. Starta RabbitMQ (om den stoppas):

   ```bash
   sudo systemctl start rabbitmq-server
   ```

1. Rensa cache:

   ```bash
   bin/magento cache:flush
   ```

1. Installera om cron:

   ```bash
   bin/magento cron:install
   ```

1. Inaktivera underhållsläge:

   ```bash
   bin/magento maintenance:disable
   ```

Inga ytterligare ändringar av konfigurationsvärdet krävs efter att migreringen har slutförts.

