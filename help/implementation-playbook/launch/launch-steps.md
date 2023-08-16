---
title: Starta steg
description: Använd vår startchecklista för att säkerställa en smidig implementering av Adobe Commerce webbplatser.
exl-id: d7807b2f-85c0-4e3e-a473-c65dbec44d28
feature: Configuration, Deploy
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 0%

---

# Starta steg

När vi har testat och slutfört checklistan före start kan vi påbörja de sista stegen som ska startas vid övergången. De här stegen omfattar att komma in på en webbplats-startbiljetter (bli live), skära bort åtkomsten och slutligen testa din butik/dina butiker när de är live.

Adobe Commerce supporttekniker arbetar tillsammans med dig genom processen och kontrollerar status samt hjälper dig att åtgärda eventuella problem. Alla problem bör spåras med biljetter för att på bästa sätt fånga upp vad som hände och hur det löstes. När du börjar distribuera kontinuerliga upprepningar av uppdateringar till din startade butik kan liknande problem uppstå igen. Dessa biljetter kan hjälpa till att identifiera problemen och hjälpa till att justera era driftsättningsuppgifter.

- Konfigurera programmet till bas-URL
   - Växla DNS till den nya platsen
   - Åtkomst till DNS-tjänsten
   - Uppdatera dina A- och CNAME-poster för dina domäner och värdnamn
   - Vänta på att TTL-tiden går och få åtkomst till din butik

- Fullständigt test i produktion
   - Verifiera alla funktioner på webbplatsen
   - Verifierar CDN-cache
   - Verifiera alla integrerade tredjepartstjänster
   - Verifiera alla system från tredje part

- Kontakta Adobe Commerce hotline om några problem skulle blockera det aktiva

![Diagram som visar fas 3 av startprocessen](../../assets/playbooks/launch-steps-3.svg)
