---
title: Steg efter start
description: Använd checklistan efter lanseringen för att säkerställa en smidig implementering av Adobe Commerce webbplats.
exl-id: 0c3162d9-6475-4b34-9278-e5aea39bd0f9
feature: Deploy
source-git-commit: ce41158f900fad27e3e7b8157f5c64ac988bbabf
workflow-type: tm+mt
source-wordcount: '165'
ht-degree: 0%

---

# Steg efter start

När webbplatsen är publicerad ska dessa aktiviteter utföras så snart som möjligt för att säkerställa att webbplatsen startades korrekt:

- Aktivera monitorverktyg (New Relic), aktivera kontroller och övervaka webbplatsen för att säkerställa att alla tjänster och all åtkomst finns i grönt
- Aktivera Adobe Commerce säkerhetsgenomsökning regelbundet
- Tagga klustret som live och skapa en supportbiljett för att aktivera High SLA-övervakning
- CSE (Customer Success Engineer) och TAM (Technical Account Manager) utför följande uppgifter så fort en övergång är klar:
   - Tagga klustret som High SLA för Adobe Commerce-klienten och skapa en supportbiljett för att aktivera det
   - Aktivera **internal** Djurkontroller för domännamn (offentlig åtkomst till kungadömet är inte tillgänglig)
   - Granska övervakningsstatus och se till att alla objekt är gröna
   - Håll intressenter informerade om garantitiden och parametrar via e-post på en live-dag

![Diagram som visar fas 4 av startprocessen](../../assets/playbooks/launch-steps-4.svg)
