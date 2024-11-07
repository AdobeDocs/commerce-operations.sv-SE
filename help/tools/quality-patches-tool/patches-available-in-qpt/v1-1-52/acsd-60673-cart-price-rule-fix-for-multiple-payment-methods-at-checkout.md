---
title: "ACSD-60673: Problem [!UICONTROL Cart Price Rule] har korrigerats för flera betalningsmetoder vid utcheckning"
description: Använd korrigeringsfilen ACSD-60673 för att åtgärda Adobe Commerce-problemet där rabatterna från en [!UICONTROL Cart Price Rule] som använder ett betalningsmetodvillkor inte alltid anges i summorna.
feature: Price Rules
role: Admin, Developer
source-git-commit: 9334b0bb7aa32cd14622c6dcef799dffe7e35fdc
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# ACSD-60673: Problem [!UICONTROL Cart Price Rule] har korrigerats för flera betalningsmetoder vid utcheckning

Korrigeringen ACSD-60673 åtgärdar ett problem där rabatterna från en [!UICONTROL Cart Price Rule] som använder ett betalningsmetodvillkor inte alltid anges i summorna. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.52 är installerad. Korrigerings-ID är ACSD-60673. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p6

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

[!UICONTROL Cart Price Rule] för flera betalningsmetoder vid utcheckning gäller inte korrekt för den angivna betalningsmetoden.

<u>Förutsättningar</u>

Kontrollera att **[!UICONTROL Multiple Payment Methods]** > **[!UICONTROL Money Order]** och **[!UICONTROL Bank Transfer]** är aktiverade.

<u>Steg som ska återskapas</u>:

1. Aktivera **[!UICONTROL Multiple Payment Methods]**.
1. Skapa en *[!UICONTROL Cart Price Rule]*.
   * Ange **[!UICONTROL Conditions]** : Betalningsmetod till **[!UICONTROL Money Order]** (eller banköverföring)
   * Välj **[!UICONTROL Actions]** = *25%* rabatt på alla produkter
1. Skapa en virtuell produkt.
1. Om du vill kopiera en ny offert och gästkund *[!UICONTROL Status]* går du till butiken och rensar cookies.
1. Lägg den virtuella produkten i kundvagnen.
1. Gå till *utcheckning*.
1. Klicka på betalningsmetoden som definierades i *[!UICONTROL Cart Price Rule]*.
1. Uppdatera din *[!UICONTROL Billing Address]*.
1. Se till att rabatten visas i det totala beloppet.
1. Klicka i kryssrutan för att ändra betalningsmetod.
1. Kontrollera att rabatten syns.

<u>Förväntade resultat</u>:

Rabatten visas i *Summor* när du har markerat kryssrutan för att växla till en tillämplig betalningsmetod.

<u>Faktiska resultat</u>:

Rabatten visas inte i *Totals*.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
