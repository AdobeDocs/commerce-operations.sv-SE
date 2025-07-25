---
title: 'ACSD-53704: Historik över återbetalningsbalans har inte beräknats efter förfallodatum'
description: Använd patchen ACSD-53704 för att åtgärda Adobe Commerce-problemet där historiken för belöningspoängsaldo inte beräknas efter belöningspoängens förfallodatum.
feature: Rewards
role: Admin, Developer
exl-id: 8cd297cc-9e9d-4615-b817-283065a79c2f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# ACSD-53704: Historik över återbetalningsbalans har inte beräknats efter förfallodatum

Korrigeringen ACSD-53704 åtgärdar ett problem där historiken för belöningspoängsaldo felberäknas efter belöningspoängens förfallodatum. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.39 är installerad. Korrigerings-ID är ACSD-53704. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Återbelöningspoängens saldohistorik beräknas inte efter förfallodatumet för belöningspoängen.

<u>Steg som ska återskapas</u>:

1. Skapa en kund direkt.
1. Lägg till belöningspoäng för kunden med olika förfallodatum.
1. Kontrollera tabellen `magento_reward_history` och ange förfallodatumet för den senaste posten med belöningspunkter till ett tidigare datum:

   ```
   UPDATE magento_reward_history SET expired_at_static = '2023-08-24 10:47:38' WHERE history_id = 3;
   ```

1. Kontrollera belöningshistorikrutnätet i **[!UICONTROL Admin]** > **[!UICONTROL Customers]** > **[!UICONTROL All Customers]** > **[!UICONTROL Edit customer]** > **[!UICONTROL Reward points]** > **[!UICONTROL Reward Points History]** och **[!UICONTROL Reward Points Balance]**.

<u>Förväntade resultat</u>:

Balansen för belöningspoäng visar endast de återstående poängen.

<u>Faktiska resultat</u>:

Saldot för belöningspoäng återspeglar det belopp som innehåller de utgångna punkterna.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool]
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i guiden för Commerce om molninfrastruktur

## Relaterad läsning

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool]
* [Metodtips för att ändra databastabeller](https://experienceleague.adobe.com/sv/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) i Commerce Implementeringspellbook

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
