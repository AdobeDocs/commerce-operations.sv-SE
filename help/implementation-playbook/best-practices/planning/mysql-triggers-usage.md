---
title: Användning av MySQL-utlösare
description: Lär dig hur du använder MySQL-utlösare effektivt med Adobe Commerce.
role: Developer
feature: Best Practices
exl-id: acac3e47-67c8-4eea-80e3-e26f2854391a
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 0%

---

# Bästa tillvägagångssätt för MySQL utlöser användning

I den här artikeln beskrivs hur du undviker prestandaproblem när du använder MySQL-utlösare. Utlösare används för att logga ändringar i granskningstabeller.

## Berörda produkter och versioner

- Adobe Commerce lokalt
- Adobe Commerce i molninfrastruktur

>[!WARNING]
>
>För Adobe Commerce i molnprojekt ska du alltid testa konfigurationsändringarna i mellanlagringsmiljön innan du ändrar konfigurationen för produktionsmiljön.

## Förstå prestandapåverkan

Utlösare tolkas som kod vilket innebär att MySQL inte förkompilerar dem.

Utlösarna är kopplade till frågans transaktionsutrymme och lägger till overhead till en tolk och tolk för varje fråga som utförs med tabellen. Utlösarna delar samma transaktionsutrymme som de ursprungliga frågorna, och även om dessa frågor konkurrerar om lås i tabellen konkurrerar utlösarna oberoende av varandra för lås i ett annat register.

Denna extra kostnad kan påverka webbplatsens prestanda negativt om många utlösare används.

>[!WARNING]
>
>Adobe Commerce stöder inte några anpassade utlösare i Adobe Commerce-databasen eftersom anpassade utlösare kan orsaka inkompatibilitet med framtida Adobe Commerce-versioner. Bästa tillvägagångssätt finns i [Allmänna MySQL-riktlinjer](../../../installation/prerequisites/database/mysql.md) i Adobe Commerce-dokumentationen.

## Använd utlösare effektivt

Följ de här riktlinjerna för att förhindra prestandaproblem när du använder utlösare:

- Om du har anpassade utlösare som skriver data när utlösaren körs, flyttar du den här logiken så att den skriver direkt till granskningstabellerna i stället. Genom att till exempel lägga till ytterligare en fråga i programkoden efter frågan som du vill skapa utlösaren för.
- Granska befintliga anpassade utlösare och överväg att ta bort dem och skriva direkt till tabellerna från programsidan. Kontrollera om det finns utlösare i databasen med [`SHOW TRIGGERS` SQL-sats](https://dev.mysql.com/doc/refman/8.0/en/show-triggers.html).
- För ytterligare hjälp, frågor eller frågor [skicka en Adobe Commerce-supportanmälan](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?#submit-ticket).

## Ytterligare information

- [Krav för MySQL](../../../installation/prerequisites/database/mysql.md)
- [Bästa databaspraxis för Adobe Commerce om molninfrastruktur](database-on-cloud.md)
