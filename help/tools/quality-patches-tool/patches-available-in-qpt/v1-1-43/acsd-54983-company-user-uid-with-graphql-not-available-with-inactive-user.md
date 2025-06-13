---
title: 'ACSD-54983: Företagsanvändare UID med GraphQL är inte tillgänglig med inaktiv användare'
description: Använd ACSD-54983-korrigeringen för att åtgärda Adobe Commerce-problemet där det inte går att få företagsanvändaren UID med GraphQL-begäran när användarstatusen är inaktiv.
feature: GraphQL
role: Admin, Developer
exl-id: b188270f-5454-41c9-8370-f4c396095297
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 0%

---

# ACSD-54983: Företagsanvändare UID med GraphQL är inte tillgänglig med inaktiv användare

Korrigeringen ACSD-54983 åtgärdar ett problem där det inte går att skicka en begäran från företagsanvändaren till UID med GraphQL när användarstatusen är inaktiv. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.43 har installerats. Korrigerings-ID är ACSD-54983. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Det går inte att hämta företagsanvändaren UID med GraphQL-begäran när användarstatusen är inaktiv.

<u>Steg som ska återskapas</u>:

1. Skapa ett företag med en administratörsanvändare. Exempel: company@test.com.
1. Skapa en ny kund.
1. Tilldela den nya kunden till ett företag.
1. Hämta en **[!UICONTROL company admin token]**.
1. Hämta företagsstrukturen med **[!UICONTROL company admin token]**. Se [Returnera företagsstrukturen](https://developer.adobe.com/commerce/webapi/graphql/schema/b2b/company/queries/company/#return-the-company-structure) i utvecklardokumentationen.
1. Svaret innehåller bara *ACTIVE*-kunder med deras ID:n.
1. Uppdatera företagsanvändaren till *INACTIVE*.
1. Hämta företagsstrukturen igen.

<u>Förväntade resultat</u>:

Det går att hämta företagsanvändaren UID när statusen är inaktiv.

<u>Faktiska resultat</u>:

De inaktiva kunderna finns inte med i listan. Det går inte att hämta företagsanvändaren UID när statusen är inaktiv.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
