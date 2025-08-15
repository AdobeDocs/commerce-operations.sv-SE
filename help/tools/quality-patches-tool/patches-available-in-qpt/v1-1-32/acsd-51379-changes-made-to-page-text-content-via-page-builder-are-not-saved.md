---
title: 'ACSD-51379: Ändringar av sidans textinnehåll via [!DNL Page Builder] sparas inte'
description: Använd korrigeringsfilen ACSD-51379 för att åtgärda Adobe Commerce-problemet där ändringar som gjorts i en sidas textinnehåll via  [!DNL Page Builder] inte sparas.
feature: Page Builder, Page Content
role: Admin
exl-id: 03fc2865-04b6-4330-b80c-8d694baa8c88
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%

---

# ACSD-51379: Ändringar av sidans textinnehåll via [!DNL Page Builder] sparas inte

Korrigeringen ACSD-51379 åtgärdar ett problem där ändringar som gjorts i en sidas textinnehåll via [!DNL Page Builder] inte sparas. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.32 är installerad. Korrigerings-ID är ACSD-51379. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Ändringarna som gjorts i en sidas textinnehåll via [!DNL Page Builder] sparas inte.

<u>Steg som ska återskapas</u>:

1. Logga in på Admin.
1. Gå till **[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]**.
1. Skapa en testsida med en rad och ett textelement på fliken **[!UICONTROL Content]**.
1. Spara sidan och gå tillbaka till fliken **[!UICONTROL Content]**.
1. Redigera texten genom att markera den och ändra den.

   **Obs!** Utgåvan kan bara reproduceras om texten markeras och ändras utan att redigeraren aktiveras.

1. Klicka på knappen **[!UICONTROL Save and Close]** på testsidan.
1. Öppna testsidan igen och kontrollera fliken **[!UICONTROL Content]**.

<u>Förväntade resultat</u>:

Den nya texten har sparats för ursprungliga och duplicerade textelement.

<u>Faktiska resultat</u>:

Textelementet har duplicerats, men den nya texten sparas inte.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
