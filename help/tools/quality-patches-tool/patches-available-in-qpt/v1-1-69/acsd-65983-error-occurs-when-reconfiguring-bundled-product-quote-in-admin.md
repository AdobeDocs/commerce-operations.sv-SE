---
title: 'ACSD-65983: Fel inträffar när paketerade produktofferter konfigureras om i Admin'
description: Använd korrigeringsfilen ACSD-65983 för att åtgärda Adobe Commerce-problemet där ett fel uppstår när du försöker konfigurera en paketprodukt på skärmen [!UICONTROL Sales] > [!UICONTROL Quotes] > [!UICONTROL Edit] på serverdelen.
feature: B2B, Quotes
role: Admin, Developer
type: Troubleshooting
source-git-commit: 8a8f2b273bcbcf135677ad7ca289398bf660e02e
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---


# ACSD-65983: Fel inträffar när paketerade produktofferter konfigureras om i Admin

Korrigeringen ACSD-65983 åtgärdar ett problem där omkonfigurering av en paketerad produktoffert i Admin-serverdelen returnerar ett fel. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69 har installerats. Korrigerings-ID är ACSD-65983. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.9.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.8

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.8 - 2.4.8-p1

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Omkonfigurationen av en paketerad produktoffert i Admin-serverdelen returnerar ett fel.

<u>Steg som ska återskapas</u>:

1. Gå till administratörspanelen och aktivera **[!UICONTROL B2B Feature]**: **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Feature]**.
1. Skapa en paketprodukt med fast belopp (till exempel: *$10*) och lägg till tre eller fler enkla produkter med *0* belopp, *2* i **Alternativ 1** och *övrigt* i **Alternativ 2**.
1. Skapa ett företagskonto från frontend.
1. Gå till **[!UICONTROL Catalog]** > **[!UICONTROL Shared Catalogs]** och tilldela det skapade företaget och produkterna till den nya/anpassade delade katalogen.
1. Logga in som **företagsanvändare** i klientdelen och lägg till en enkel produkt i kundvagnen från paketet.
1. Öppna kundvagnssidan och skicka som **Begär en offert**.
1. Gå till serverdelen och redigera den skapade offerten.
1. Klicka på knappen **Konfigurera** i avsnittet **Citationsobjekt**.
1. Välj en annan enkel produkt i **Alternativ 2**.
1. Klicka nu på knappen **OK** och se felmeddelandet.

<u>Förväntade resultat</u>:

Du kan konfigurera begärda offertobjekt från administratören på vanligt sätt, utan att något felmeddelande visas.

<u>Faktiska resultat</u>:

Felmeddelandet visas:

*Ett tekniskt problem med servern skapade ett fel. Försök igen för att fortsätta med det du gjorde. Försök igen senare om problemet kvarstår.*

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool]
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i guiden för Commerce om molninfrastruktur

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken
