---
title: 'ACSD-60811: Korrigerar begränsning av uppdatering av orderstatus till anpassade värden'
description: Använd patchen ACSD-60811 för att åtgärda Adobe Commerce-problemet där det bara går att uppdatera orderstatus med anpassade värden eller kommentarer om den aktuella statusen är "bearbetning" eller "bedrägeri".
feature: Orders, Admin Workspace
role: Admin, Developer
exl-id: 6d5391b3-7014-4d0a-b4ab-799f0733bbca
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# ACSD-60811: Korrigerar begränsning av uppdatering av orderstatus till anpassade värden

Korrigeringen ACSD-60811 åtgärdar ett problem där det endast är möjligt att uppdatera orderstatusen med ett anpassat värde eller en kommentar om den aktuella statusen är [!UICONTROL Processing] eller [!UICONTROL Suspected Fraud]. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56 har installerats. Korrigerings-ID är ACSD-60811. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7. 2.4.7-p1, 2.4.7-p2, 2.4.7-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Det går bara att uppdatera orderstatusen med ett anpassat värde eller en kommentar om den aktuella statusen är antingen *bearbetning* eller *bedrägeri*. Orderstatusen ändras inte när en ny status väljs och skickas.

<u>Steg som ska återskapas</u>:

1. Gå till **[!UICONTROL Stores]** > **[!UICONTROL Order Status]** om du vill skapa en anpassad orderstatus på administratörspanelen.
1. Klicka på **[!UICONTROL Assign Status to State]** för att tilldela den anpassade statusen till orderstatus.
1. Ändra orderstatus från ordervysidan på administratörspanelen.

<u>Förväntade resultat</u>:

Administratörsanvändaren bör kunna ändra orderstatusen till en anpassad orderstatus på administratörspanelen.

<u>Faktiska resultat</u>:

Orderstatusen är densamma när en ny orderstatus väljs och skickas.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
