---
title: 'ACP2E-3689: Flera problem med kategoriträdvisning på djupare nivåer och spegling av ankarpunkt/icke-ankarrelationer'
description: Använd programfixen ACP2E-3689 för att åtgärda Adobe Commerce-problemet med kategoriträdvisning på mer än djup, fyra kapslingar och spegelvända fästpunktsrelationer.
feature: Categories, Page Content
role: Admin, Developer
exl-id: 8d3c484f-3f8d-4fc1-8b31-e850cb34341c
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 0%

---

# ACP2E-3689: Flera problem med kategoriträdvisning på djupare nivåer och spegling av ankarpunkt/icke-ankarrelationer

>[!NOTE]
>
>Den här korrigeringen ersätter [ACSD-62689](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-57/acsd-62689-customer-add-categories-issue-related-product-rules-and-widgets.md) för version 2.4.7 och senare.

Programrättningen ACP2E-3689 åtgärdar flera problem med kategoriträdvisning på mer än djupet av fyra kapslingar och reflekterar fästpunkt/icke-fästpunktsrelationer. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61 har installerats. Korrigerings-ID är ACP2E-3689. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7-p3

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Kategoriträdet på djupare nivåer (4+) visas inte korrekt och visar ankarfästpunktsrelationer.

<u>Steg som ska återskapas</u>:

1. Ställ in ett kategoriträd med kapslade kategorier på mer än 4 nivåer.
1. Expandera kategoriträdet i Admin som visas på olika platser:
   1. Konfigurera en [!UICONTROL Related Products Rule] och ange ett villkor baserat på kategorier.
   1. Skapa en widget och välj [!UICONTROL Layout Updates] i [!UICONTROL Anchor categories].

<u>Förväntade resultat</u>:

Alla nivåer i kategoriträdet visas korrekt.

<u>Faktiska resultat</u>:

Endast de första nivåerna (&lt;4) i kategoriträdet är tillgängliga.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
