---
title: 'ACSD-48857: Det går inte att spara ändringar efter redigering med  [!DNL Page Builder]'
description: Använd korrigeringsfilen ACSD-48857 för att åtgärda Adobe Commerce-problemet där användaren inte kan spara ändringar efter redigering med  [!DNL Page Builder].
feature: Admin Workspace, CMS, Page Builder
role: Admin
exl-id: b03cd597-8fef-4528-9699-793dc61d34da
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# ACSD-48857: Det går inte att spara ändringar efter redigering med [!DNL Page Builder]

ACSD-48857-korrigeringen åtgärdar ett problem där användaren inte kan spara ändringar efter redigering med [!DNL Page Builder]. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.28 har installerats. Korrigerings-ID är ACSD-48857. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3 - 2.4.6

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Användaren kan inte spara ändringar efter redigering med [!DNL Page Builder].

<u>Steg som ska återskapas</u>

1. Logga in på Admin-webbplatsen.
1. Navigera till **[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]** för att skapa en tom CMS-sida.
1. Kör det här SQL-skriptet för att ange följande **[!UICONTROL Content]**-fältvärde:

   ```SQL
   update cms_page set content = '<div data-content-type="text" data-appearance="default" data-element="main"><h4 style="text-align: center;" contenteditable="true" data-placeholder="Edit Heading Text" data-content-type="heading" data-appearance="default" data-element="main">THE RULES</h4></div>' where page_id=8;
   ```

1. Gå tillbaka till **[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]** i Admin.
1. Redigera sidan.
1. Gå till fliken **[!UICONTROL Content]**.
1. Klicka på **[!UICONTROL Save]**.

<u>Förväntade resultat</u>

HTML innehållssanering implementeras. Detta tar bort [!DNL Page Builder] reserverade HTML-attribut i innehåll som genereras av textredigeraren.

<u>Faktiska resultat</u>

Sidan förblir osparad och inläsaren fortsätter snurra. Följande fel genereras i konsolen:

```
[ERROR] Page Builder was rendering for 5 seconds without releasing locks.
```

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
