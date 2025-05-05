---
title: 'ACSD-61969: Krävs för att skriva kupongkod som konfigurerats med versaler eller gemener'
description: Använd patchen ACSD-61969 för att åtgärda Adobe Commerce-problemet där en användare måste skriva in kupongkoden exakt som den är konfigurerad med versaler eller gemener.
feature: Price Rules
role: Admin, Developer
source-git-commit: b2660e3ca0dedbe4c9d8fa441f2e49b2e096474b
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# ACSD-61969: Krävs för att skriva kupongkod som konfigurerats med versaler eller gemener

Korrigeringen ACSD-61969 åtgärdar ett problem där en användare måste skriva in kupongkoden exakt som den är konfigurerad med versaler eller gemener. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.53 har installerats. Korrigerings-ID är ACSD-61969. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Du måste skriva kupongkoden exakt som den är konfigurerad med versaler eller gemener när du använder den från serverdelen. De är skiftlägeskänsliga när du skapar en Admin-order, men inte skiftlägeskänsliga i butiken.

<u>Steg som ska återskapas</u>:

1. Skapa en *[!UICONTROL Cart Price Rule]* med en specifik kupong *TEST*. Se till att kupongkoden är i versaler.
1. Skapa en order i Admin.
1. Lägg till *test* i fältet *[!UICONTROL Apply Coupon Code]* och klicka på pilen nära fältet för att tillämpa kupongen.
1. Observera resultatet.

<u>Förväntade resultat</u>:

Kupongen har tillämpats. Kupongfältet är inte skiftlägeskänsligt.

<u>Faktiska resultat</u>:

Kupongen tillämpas inte. Följande fel visas:

*Kupongkoden för testet är ogiltig. Verifiera koden och försök igen.*

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

[[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
