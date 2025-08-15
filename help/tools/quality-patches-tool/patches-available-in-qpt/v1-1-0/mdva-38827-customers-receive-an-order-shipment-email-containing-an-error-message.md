---
title: 'MDVA-38827: Kunderna får orderleveransfel via e-post'
description: 'MDVA-38827-korrigeringen åtgärdar ett problem där kunderna får ett e-postmeddelande om orderleverans med följande felmeddelande: *Ett fel uppstod när innehållet genererades*. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.0 är installerat. Patch-ID:t är MDVA-38827. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.'
feature: Communications, Marketing Tools, Orders, Shipping/Delivery
role: Admin
exl-id: ab522c9c-2983-4c2f-b341-4487bdbee34d
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '535'
ht-degree: 0%

---

# MDVA-38827: Kunderna får orderleveransfel via e-post

MDVA-38827-korrigeringen åtgärdar ett problem där kunderna får ett e-postmeddelande om orderleverans med följande felmeddelande: *Ett fel uppstod när det här innehållet genererades*. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.0 har installerats. Patch-ID:t är MDVA-38827. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

Adobe Commerce om molninfrastruktur 2.4.2-p1

**Kompatibel med Adobe Commerce-versioner:**

Adobe Commerce (alla distributionsmetoder) 2.3.3-p1 - 2.4.2-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

När alternativet Meddela kunder via e-post för leverans har valts får kunderna ett e-postmeddelande med följande felmeddelande: *Ett fel uppstod när innehållet genererades*.

<u>Steg som ska återskapas</u>:

1. Gå till **Marknadsföring** > **Kommunikation** > **E-postmallar** och välj **Lägg till ny mall**.
   * Välj **Magento Försäljning** > **Ny leverans**.
   * Klicka på **Läs in mall**.
   * Lägg till ett mallnamn (t.ex. Core Shipping Template) och klicka på **Save**.
1. Gå till **Store** > Inställningar > **Konfiguration** > **Försäljning** > **E-post för försäljning**:
   * Aktivera **Leveranskommentarer**.
   * Välj **Kärnleveransmall** (se avsnittet&quot;Lägg till ett mallnamn&quot; i steg 1) under E-postmall för försändelsekommentar och E-postmall för försändelsekommentar för gäst.
1. Beställ. Gå till panelen Admin > **Försäljning** > **Beställning**, klicka på **Visa** och skicka sedan ordern.
1. Orderstatusen ändras från Väntande till Bearbetning.
1. Klicka på **Utleveranser** till vänster i sidofältsmenyn och klicka sedan på **Visa** för att visa ordningen.
1. Lägg till en kommentar i **Kommentarstext** nedan **Leveranshistorik** och markera kryssrutan **Meddela kund via e-post**.
1. Klicka på **Skicka kommentar**.

<u>Förväntade resultat</u>:

E-postförsäljning med försändelsekommentarer genereras.

<u>Faktiska resultat</u>:

Följande felmeddelande har tagits emot i e-postmeddelandet: *Ett fel uppstod när innehållet genererades.*

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med verktyget för kvalitetskorrigeringar ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i [!DNL Quality Patches Tool]-handboken.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
