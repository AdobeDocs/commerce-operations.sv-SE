---
title: 'ACSD-63067: Löser kvantitetsvalideringsproblem i grupperade produkter i storefront'
description: Använd patchen ACSD-63067 för att åtgärda Adobe Commerce-problemet där alla produktkvantiteter i grupperade produkter felaktigt markeras som ogiltiga när endast en produkt har en felaktig kvantitet.
feature: Storefront
role: Admin, Developer
source-git-commit: 7446f4d83932eedc6fa711ad09c6ee559d357f70
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 0%

---

# ACSD-63067: Löser kvantitetsvalideringsproblem i grupperade produkter i storefront

Korrigeringen ACSD-63067 åtgärdar ett problem där alla produktkvantiteter i grupperade produkter markeras felaktigt som ogiltiga när endast en produkt har en felaktig kvantitet. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58 har installerats. Korrigerings-ID är ACSD-63067. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

Adobe Commerce (alla distributionsmetoder) 2.4.7-p2

**Kompatibel med Adobe Commerce-versioner:**

Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

I grupperade produkter gör en ogiltig kvantitet i en av underprodukterna att alla kvantiteter markeras felaktigt som ogiltiga. Dessutom visas ett valideringsmeddelande för alla produkter i stället för bara för den som har den ogiltiga kvantiteten.

<u>Steg som ska återskapas</u>:

1. Skapa en ny grupperad produkt med minst två enkla produkter som alternativ.
1. Öppna produkten i butiken.
1. Ange en ogiltig kvantitet (till exempel: -1) för ett av alternativen och en giltig kvantitet (till exempel: 1) för de återstående alternativen.
1. Klicka på **[!UICONTROL Add to Cart]**.

<u>Förväntade resultat</u>:

Endast den produkt som har den ogiltiga kvantiteten markeras som ogiltig.

<u>Faktiska resultat</u>:

Alla produktkvantiteter markeras som ogiltiga och meddelandet *Ange antalet produkter. visas för alla produkter*.


## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.


## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
