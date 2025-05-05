---
title: 'MDVA-39305-V3: Inloggningsproblem med aktiverad [!DNL Google reCAPTCHA]'
description: Använd MDVA-39305-V3-korrigeringen för att åtgärda Adobe Commerce-problemet där registrerade kunder inte kan logga in när  [!DNL Google reCAPTCHA] är aktiverat. Den här korrigeringen åtgärdar också problemet där ett formulär kan skickas innan  [!DNL Google reCAPTCHA] fullständigt läses in. Dessutom korrigeras felet *Anropet till en medlemsfunktion ärDisabled() på null* när block används på icke-standardplatser på en CMS-sida.
feature: Console
role: Admin
source-git-commit: 7846079987d2b7c0e9fdd0485bb3aae4f09cd6f9
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%

---

# MDVA-39305-V3: Inloggningsproblem med aktiverad [!DNL Google reCAPTCHA]

>[!NOTE]
>
>Den här korrigeringen är en uppdatering av korrigeringen [MDVA-39305](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-1/mdva-39305-login-issues-with-enabled-google-recaptcha.md).

MDVA-39305-V3-korrigeringen åtgärdar ett problem där registrerade kunder inte kan logga in när [!DNL Google reCAPTCHA] är aktiverat. Den här korrigeringen åtgärdar också problemet där ett formulär kan skickas innan [!DNL Google reCAPTCHA] har lästs in helt. Dessutom åtgärdas felet *Anrop till medlemsfunktionen isDisabled() på null* när block används på icke-standardplatser på en CMS-sida.

Den här korrigeringen lades till i [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.48. Den uppdaterades i QPT 1.1.58-versionen för att inkludera nya Adobe Commerce 2.4.7-2.4.7-p4. Patch-ID:t är MDVA-39305-V3. Observera att problemet har åtgärdats i Adobe Commerce version 2.4.4, 2.4.5-p2 och 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4, 2.4.5-p2, 2.4.7

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4-p1 - 2.4.7-p4

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

### Fall I

1. Registrerade kunder kan inte logga in med den aktiverade [!DNL Google reCAPTCHA].
1. Ett formulär kan skickas innan [!DNL Google reCAPTCHA] har lästs in helt.

<u>Steg som ska återskapas</u>:

1. Gå till **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Security]** > **[!DNL Google reCAPTCHA Storefront]** och aktivera ***[!DNL Google reCAPTCHA]***.
1. Gå till fronten.
1. Öppna **[!UICONTROL Developer Tool Console]** i webbläsaren.

<u>Förväntade resultat</u>:

Inga CSP-varningar i konsolen.

<u>Faktiska resultat</u>:

CSP-varningar i konsolen.

### Fall II

Ett fel som anger *Anropet till en medlemsfunktion ärDisabled() på null* inträffar när block används på icke-standardplatser på en CMS-sida.

<u>Steg som ska återskapas</u>:

1. Skapa ett statiskt block med innehållet nedan:

   ```
   {{block class="Magento\Newsletter\Block\Subscribe" name="home.form.subscribe"
   template="Magento_Newsletter::subscribe.phtml"}}
   ```

1. Lägg till ett statiskt block på en CMS-sida från **[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Pages]** > **[!UICONTROL Add/Edit CMS page]** > **[!UICONTROL Content]**.
1. Spara sidan.

<u>Förväntade resultat</u>:

Sidan läses in utan fel.

<u>Faktiska resultat</u>:

Ett 500-fel inträffar på sidan i butiken.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.


