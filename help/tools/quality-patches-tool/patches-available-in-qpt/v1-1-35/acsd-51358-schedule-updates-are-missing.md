---
title: 'ACSD-51358: Schemauppdateringar saknas'
description: Använd patchen ACSD-51358 för att åtgärda Adobe Commerce-problemet där ändringar i schemalagda uppdateringar utan slutdatum leder till att andra schemalagda uppdateringar tas bort på samma enhet.
feature: Staging
role: Admin, Developer
exl-id: 6e2e598b-72f1-4f00-a989-3f75bf65f8f0
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-51358: Schemauppdateringar saknas

Korrigeringen ACSD-51358 åtgärdar ett problem där ändringar i schemalagda uppdateringar utan slutdatum leder till att andra schemalagda uppdateringar tas bort på samma enhet. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.35 är installerad. Korrigerings-ID är ACSD-51358. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Ändringarna i den schemalagda uppdateringen utan slutdatum leder till att andra schemalagda uppdateringar tas bort för samma entitet.

<u>Steg som ska återskapas</u>:

1. Skapa en **[!UICONTROL scheduled update]** utan slutdatum (*update 1*).
1. Skapa ny **[!UICONTROL scheduled update]** med samma startdatum som den första uppdateringen, men lägg till nästa dag och slutdatumet (*update 2*).
1. Redigera **[!UICONTROL scheduled update]** som skapats i steg 1 (*uppdatera 1*) och spara ändringarna.

<u>Förväntade resultat</u>

(*update 2*) ska finnas kvar i listan **[!UICONTROL schedule update]** när (*update 1*) redigeras.

<u>Faktiska resultat</u>

(*update 2*) togs bort från listan **[!UICONTROL schedule update]** när (*update 1*) redigerades.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) i [!DNL Quality Patches Tool]-handboken.
