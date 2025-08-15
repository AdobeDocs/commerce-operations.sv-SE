---
title: 'ACSD-62481: Kundvagnen är tom även om [!UICONTROL Persistence] är aktiverat'
description: Använd patchen ACSD-62481 för att åtgärda problemet med Adobe Commerce där funktionen för beständig kundvagn inte fungerar när du använder popup-fönstret för inloggning vid utcheckning.
feature: Shopping Cart, Checkout
role: Admin, Developer
exl-id: 79fb3161-f56e-45f3-9933-cf95703f1554
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# ACSD-62481: Kundvagnen är tom även om *[!UICONTROL Persistence]* är aktiverat

Korrigeringen ACSD-62481 åtgärdar ett problem där funktionen för beständig kundvagn inte fungerar när popup-fönstret för inloggning används vid utcheckning eftersom kryssrutan *[!UICONTROL Remember Me]* saknas, vilket gör att produkter försvinner från kundvagnen efter utloggning. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57 är installerad. Korrigerings-ID är ACSD-62481. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Funktionen för beständig kundvagn misslyckas vid användning av popup-fönstret för inloggning vid utcheckning eftersom den saknar kryssrutan *[!UICONTROL Remember Me]*. Detta gör att produkterna försvinner från kundvagnen efter utloggningen.

<u>Steg som ska återskapas</u>:

1. Konfigurera gästkontot och de beständiga kundvagnsinställningarna på följande sätt i administratören:

   * Navigera till **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Checkout]** > **[!UICONTROL Checkout Options]** och ange *[!UICONTROL Allow Guest Checkout]* som *Nej*.

      * Klicka på **[!UICONTROL Save Config]**.

   * Navigera till **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Persistent Shopping Cart]** > **[!UICONTROL General Options]** och ställ in *[!UICONTROL Enable Persistence]* på *Ja*.
   * Lämna alla andra inställningar som standard, men ändra *[!UICONTROL Clear Persistence on Sign Out]* till *Nej*.

      * Klicka på **[!UICONTROL Save Config]**.

1. Gå till **[!UICONTROL Catalog]** > **[!UICONTROL Products]** > **[!UICONTROL Add product]** om du vill lägga till en enkel produkt i katalogen.

   * Fyll i de nödvändiga minimidetaljerna och se till att de finns i lager.

1. Skapa ett kundkonto på frontend med huvudformuläret `(../customer/account/create/)` och logga ut.
1. Lägg produkten i kundvagnen som gäst.
1. Öppna minivagnen med ikonen längst upp till höger och klicka sedan på **[!UICONTROL View and Edit Cart]**.
1. Gå till kassan.
1. Logga in på det nya kundkontot via popup-dialogrutan som visas och logga ut.

<u>Förväntade resultat</u>:

Kundvagnen behåller produkterna från den tidigare inloggade användaren.

<u>Faktiska resultat</u>:

* Kundvagnen är tom.
* Popup-inloggningsdialogrutan visar inte alternativet *[!UICONTROL Remember Me]*.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: Uppgraderingar och korrigeringar > Tillämpa korrigeringar i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
