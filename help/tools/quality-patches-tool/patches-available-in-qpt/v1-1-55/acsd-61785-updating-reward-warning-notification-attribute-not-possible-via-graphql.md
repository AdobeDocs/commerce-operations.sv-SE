---
title: 'ACSD-61785: Attributet för belöning_varning_notification kan inte uppdateras via GraphQL-mutation och REST API-anrop'
description: Använd patchen ACSD-61785 för att åtgärda Adobe Commerce-problemet där det inte går att uppdatera attributet "gain_warning_notification" via GraphQL-mutation och REST API-anrop.
feature: REST, GraphQL, Rewards
role: Admin, Developer
source-git-commit: 87ce6004a632f860447d55c13c08f78533ab093e
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 0%

---

# ACSD-61785: Attributet för belöning_varning_notification kan inte uppdateras via GraphQL-mutation och REST API-anrop

Korrigeringen ACSD-61785 åtgärdar ett problem där det inte går att uppdatera attributet `reward_warning_notification` via GraphQL-mutation och REST API-anrop. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55 är installerad. Korrigerings-ID är ACSD-61785. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

Adobe Commerce (alla distributionsmetoder) 2.4.7-p2

**Kompatibel med Adobe Commerce-versioner:**

Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Det går inte att uppdatera attributet `reward_warning_notification` via GraphQL-mutation och REST API-anrop.

<u>Steg som ska återskapas</u>:

1. Kontrollera GraphQL och REST API-schemat/dokumentationen för *prenumerera för Balansuppdateringar* och *Prenumerera för meddelanden om utgångna punkter*.

<u>Förväntade resultat</u>:

Det går att prenumerera på *uppdateringar av belöningssaldo* och för *meddelanden om förfallodatum för poäng* via GraphQL och REST API.

<u>Faktiska resultat</u>:

GraphQL och REST API saknar den här funktionen.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
