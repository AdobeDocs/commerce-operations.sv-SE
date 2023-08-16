---
title: Steg före start
description: Använd våra checklistor före lansering för att säkerställa en smidig implementering av Adobe Commerce webbplats.
exl-id: bd10881f-0336-4aa4-82ad-4d635010e2e4
feature: Deploy
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '520'
ht-degree: 0%

---

# Steg före start

När du har slutfört distributionen och testningen i testmiljöer kan du börja förbereda för att starta webbplatsen. Staging är en nära produktionsmiljö som körs på liknande maskinvara, konfigurationer, arkitektur och tjänster. Det kan minska driftstoppen och göra tillägg, service, anpassade konfigurationer och accepteringstest för handlare till viktiga komponenter för att släppa sajter och butiker.

Checklistan före start krävs för att verifiera statusen före start, som innehåller följande större verifieringar:

- Frys kod för distribution
- Se till att driftstoppen kommunicerades i förväg av minst en dag för underhållsrelease och en vecka för första starten
- Distributionsskript är konfigurerade/konfigurerade helt för produktions-/mellanlagrings-/integreringsmiljöer
- Databaserna är alla konfigurerade och identiska i mellanlagrings- och produktionsmiljöer
- SSL-certifikat (TLS) valideras för mellanlagrings-/produktionsmiljöer
- E-posttjänster är väl konfigurerade och fungerar för transaktionsmeddelanden
- CDN har konfigurerats för mellanlagrings-/produktionsmiljöer
- Ställ in säkerhetsgenomsökning för mellanlagrings-/produktionsmiljöer
   - Adobe Commerce säkerhetsgenomsökning
- Utför prestandautvärdering med
   - JMeter
   - Siege
   - Testa webbsidor
   - Google sidhastighet
- Validera alla tredjepartsintegreringar som ska fungera i programmet (OMS, CRM)
- Aktivera verktyget för prestandaövervakning (nya resultat)
- Datamigreringsaktiviteter vid repetering (om sådana finns)

![Bild som visar fas 1 av startprocessen](../../assets/playbooks/launch-steps-1.svg)

De största skillnaderna mellan Adobe Commerce lokala implementeringar och molnimplementeringar är distributionsskript och verktyg samt konfigurationen för SSL, Mail och CDN. Processen är dock fortfarande densamma.

För SSL-certifikat (TLS) tillhandahåller Adobe Commerce i molninfrastrukturen ett snabbcertifikat med jokertecken. Om du vill börja använda den måste du godkänna valideringen: lägg till posten Fast TXT i ett domännamn i dina DNS-inställningar. Posten Fastly TXT finns i kalkylbladet för introduktion, annars måste du skicka in en supportanmälan för att få den. Ersätt den här texten med dina frågor/kommentarer här. Om du använder ditt eget SSL-certifikat (TLS) i stället för ett Fast-jokertecken skickar du en supportanmälan med ditt certifikat bifogat till konfigurationen.

Adobe Commerce i molninfrastrukturen erbjuder SendGrid Mail-funktionalitet för dina transaktionsbaserade e-postmeddelanden. För Pro-planer måste du lägga till SendGrid-poster i dina DNS-inställningar. Poster i SendGrid finns i arbetsbladet, annars måste SI eller handlare skicka supportärenden för att få dem. Till att börja med behöver du inte göra några ändringar i din DNS. SendGrid är förkonfigurerat för dig.

## Fullständig checklista före start

Den fullständiga checklistan före start visar alla större aktiviteter vars fullständighet är nödvändig för att övergå till startläge.

- Uppdaterade planer för riskreducering live
- Korrigera angivna domännamn
- Utgående e-postmeddelanden har testats
- SSL-certifikat har etablerats och konfigurerats
- Den viktiga konfigurationen av Adobe Commerce-programmet uppdateras korrekt
- Bas-URL:er och basadministratörs-URL:er är korrekt inställda på det slutliga värdnamnet
- Administratörslösenord har ändrats
- Alla användare med åtkomst till program som inte längre kräver åtkomst tas bort
- Betalningskonfiguration för produktionsmiljö (för vissa används sandlådeläge för testning)
- Testdata (kund, önskelista, recensioner, order och relaterade data) från produktionsdatabasen rensas

![Bild som visar fas 2 av startprocessen](../../assets/playbooks/launch-steps-2.svg)
