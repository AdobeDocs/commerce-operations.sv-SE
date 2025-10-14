---
title: 'ACSD-62793: Datetime-attribut i exporterar saknade tidskomponenter. Om **[!UICONTROL Fields Enclosure]** är aktiverat omges attributvärden av citattecken'
description: Använd patchen ACSD-62793 för att åtgärda Adobe Commerce-problemet där datetime-attribut i exporterade data saknar tidskomponenten. Om **[!UICONTROL Fields Enclosure]** är aktiverat omges attributvärdena i kolumnen *additional_attributes* av dubbla citattecken.
feature: Attributes, Data Import/Export, Catalog Service
role: Admin, Developer
exl-id: 340dcc84-dcb8-40ed-b2ab-2d950d1dd1ca
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---

# ACSD-62793: Datetime-attribut i exporterar saknade tidskomponenter. Om **[!UICONTROL Fields Enclosure]** är aktiverat omges attributvärden av citattecken

Korrigeringen för ACSD-62793 åtgärdar ett problem där attribut för datum/tid i exporterade data saknar tidskomponenten. Om **[!UICONTROL Fields Enclosure]** är aktiverat kommer attributvärden i kolumnen *additional_attributes* att omslutas av dubbla citattecken. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55 är installerad. Korrigerings-ID är ACSD-62793. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7-p2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Tidsattribut i exporterade data inkluderar inte tidskomponenten. Om **[!UICONTROL Fields Enclosure]** är aktiverat kommer attributvärden i kolumnen *additional_attributes* att omslutas av dubbla citattecken.

<u>Steg som ska återskapas</u>:

1. Skapa ett produktattribut med **[!UICONTROL Catalog Input Type for Store Owner]** = **[!UICONTROL Date and Time]**.
1. Tilldela attributet till attributuppsättningen **[!UICONTROL Default]**.
1. Skapa en enkel produkt med ett datum- och tidsvärde för det nya attributet.
1. Exportera produkten till en CSV-fil från **[!UICONTROL System]** > *Dataöverföring* > **[!UICONTROL Export]**.
1. Kontrollera attributvärdet i kolumnen *additional_attributes*. Den har bara datumdelen, men inte tiden.
1. Uppdatera attributvärdet så att det använder tiden, t.ex. &quot;08/10/22, 3:20 PM&quot;.
1. Importera CSV-filen.
1. Kontrollera tabellen *catalog_product_entity_datetime*.

<u>Förväntade resultat</u>:

Datum och tid exporteras och importeras på rätt sätt.

<u>Faktiska resultat</u>:

Endast datumdelen exporteras och importeras.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning &#x200B;](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.


## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
