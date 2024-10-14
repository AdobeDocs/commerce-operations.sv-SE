---
title: "ACSD-59865: [!UICONTROL Cart Price Rule] kan inte avbryta tidigare regler på grund av otillräcklig produktkvantitet"
description: Använd patchen ACSD-59865 för att åtgärda Adobe Commerce-problemet där värdet för *Rabattkvantitet* i *Fast belopp,* *Procent av produktrabatt* och *Köp X get Y* [!UICONTROL Cart Price Rules] inte längre avbryter åtgärden för tidigare regler.
feature: Price Rules
role: Admin, Developer
source-git-commit: 602a839708eab2551bd99a4f24e66edbde511150
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 0%

---

# ACSD-59865: [!UICONTROL Cart Price Rule] kan inte avbryta tidigare regler på grund av otillräcklig produktkvantitet

ACSD-59865-korrigeringen åtgärdar ett problem där *[!UICONTROL Discount quantity step]*-värdet i *[!UICONTROL Fixed amount discount],* *[!UICONTROL Percent of product price discount],* och *[!UICONTROL Buy X get Y]* [!UICONTROL Cart Price Rules] inte längre avbryter åtgärden för tidigare regler. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.52 är installerad. Korrigerings-ID är ACSD-59865. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

[!UICONTROL Cart Price Rule] kan inte avbryta tidigare tillämpade regler på grund av en otillräcklig produktkvantitet i kundvagnen.

<u>Steg som ska återskapas</u>:

1. Logga in som administratör.
1. Gå till **[!UICONTROL Marketing]** > **[!UICONTROL Cart Price Rules]** och klicka på **[!UICONTROL Add New rule]**.
   * Ange **[!UICONTROL Rule Name]** = *Testa - 1*
   * Markera alla *webbplatser* och *kundgrupper*
   * Ange **[!UICONTROL Priority]** = *0*
   * Gå till avsnittet **[!UICONTROL Actions]**:
      * Ange **[!UICONTROL Apply]** = *Procent av produktprisrabatt*
      * Ange **[!UICONTROL Discount amount]** = *10*
      * Ange **[!UICONTROL Maximum Qty Discount is Applied To]** = *100*
      * Ange **[!UICONTROL Discount Qty Step (Buy X)]** = *0*
      * Ange **[!UICONTROL Discard subsequent rules]** till *Nej*
1. Rensa cachen.
1. Gå till butiken, lägg till ett objekt i kundvagnen och fortsätt till *kassan/kundvagnen*.
1. Kontrollera att rabatten på *10%* används i kundvagnen.
1. Återgå till **[!UICONTROL Cart Price Rules]** och skapa en ny regel.
   * Ange **[!UICONTROL Rule Name]** = *Testa - 2*
   * Markera alla **[!UICONTROL Websites]** och **[!UICONTROL Customer Groups]**
   * Ange **[!UICONTROL Priority]** = *2*
   * Navigera till avsnittet **[!UICONTROL Actions]**:
      * Ange **[!UICONTROL Apply]** = *Procent av produktprisrabatt*
      * Ange **[!UICONTROL Discount amount]** = *20*
      * Ange **[!UICONTROL Maximum Qty Discount is Applied To]** = *100*
      * Ange **[!UICONTROL Discount Qty Step (Buy X)]** = *3*
1. Rensa cachen.
1. Gå tillbaka till Storefront igen.
1. Uppdatera kundvagnen för att uppdatera reglerna. Kontrollera att rabatten på *10%* inte längre gäller.
1. Lägg till artiklar i kundvagnen tills kvantiteten uppfyller det *steg*-värde som krävs för den andra regeln.

<u>Förväntade resultat</u>:

Den första [!UICONTROL Cart Price Rule] används när villkoren i den andra regeln uppfylls.

<u>Faktiska resultat</u>:

Prisreglerna tillämpas som de har konfigurerats på adminkontrollpanelen.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
