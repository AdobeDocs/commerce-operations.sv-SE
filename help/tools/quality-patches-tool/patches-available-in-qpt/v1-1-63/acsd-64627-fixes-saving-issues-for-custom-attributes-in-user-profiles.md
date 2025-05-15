---
title: 'ACSD-64627: Det går inte att spara anpassade kundattribut i [!UICONTROL Company Structure]'
description: Använd korrigeringsfilen ACSD-64627 för att åtgärda Adobe Commerce-problemet där anpassade kundattribut inte kan sparas när användare läggs till eller redigeras i [!UICONTROL Company Structure].
feature: B2B
role: Admin, Developer
exl-id: 8e7dd72e-c21e-46cf-8e2b-9dccedfd8b04
source-git-commit: f4a7e00bb1a01fcc8ebc05cd74f4cdd1c4c6d7d4
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# ACSD-64627: Det går inte att spara anpassade kundattribut i [!UICONTROL Company Structure]

Korrigeringen ACSD-64627 åtgärdar ett problem där anpassade kundattribut inte kan sparas när användare läggs till eller redigeras på sidan **[!UICONTROL Company Structure]**. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.63 har installerats. Korrigerings-ID är ACSD-64627. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.9.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7-p3, 2.4.7-p4, 2.4.8

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p8, 2.4.7-p3, 2.4.7-p4, 2.4.8

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Anpassade kundattribut sparas inte när användare läggs till eller redigeras på sidan **[!UICONTROL Company Structure]**.

<u>Steg som ska återskapas</u>:

1. Installera en Adobe Commerce-instans med aktiverade B2B-funktioner.
1. Skapa ett nytt kundattribut med namnet *custom_upload* med värdet **[!UICONTROL Input Type]** för *[!UICONTROL File (attachment)]*.
1. Skapa ett annat kundattribut med namnet *image_attachment* med värdet **[!UICONTROL Input Type]** för *[!UICONTROL Image File]*.
1. Ange **[!UICONTROL Show on Storefront]** till *Yes* om du vill att båda attributen ska vara synliga på butiken. Markera alla formulär:
   * Kundregistrering
   * Redigera kundkonto
   * Admin - utcheckning
1. Skapa och aktivera ett nytt företag.
1. Logga in som företagsadministratör i butiken.
1. Navigera till **[!UICONTROL Customer Account]** > **[!UICONTROL Company Structure]** eller **[!UICONTROL Customer Account]** > **[!UICONTROL Company Users]**.
1. Klicka på **[!UICONTROL Add New User]**.
1. Klicka på **[!UICONTROL Upload]** för attributet *custom_upload*.
1. Klicka på **[!UICONTROL Select file]** för attributet *image_attachment*.

<u>Förväntade resultat</u>:

Filutforskaren öppnas för båda attributen. När du sparar lagras värdena och filerna kan överföras.

<u>Faktiska resultat</u>:

Knapparna svarar inte. Ingen filutforskare öppnas eller data sparas.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
