---
title: '''ACSD-50849: Om du lägger till en ny produkt efter att cacheminnet rensats blir matchningsfelet'
description: Använd korrigeringsfilen ACSD-50849 för att korrigera Adobe Commerce-problemet där en ny produkt läggs till i kategorin efter att cacheminnet rensats resulterar i en felmatchning av positioner och urval av befintliga produkter.
feature: Cache, Categories, Products
role: Admin
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# ACSD-50849: Om du lägger till en ny produkt efter att cacheminnet rensats blir matchningsfelet felaktig

Korrigeringen ACSD-50849 åtgärdar ett problem där en ny produkt läggs till i kategorin efter att cacheminnet rensats, vilket resulterar i en felmatchning av positioner och val för befintliga produkter. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) QPT 1.1.32 är installerad. Korrigerings-ID är ACSD-50849. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.5-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Om du lägger till en ny produkt i kategorin efter att du rensat cacheminnet skapas en felmatchning av positioner och val för de befintliga produkterna.

<u>Steg som ska återskapas</u>:

1. Skapa två produkter.
1. Tilldela en produkt till en kategori.
1. Öppna kategorin från administratören.
1. Rensa cachen `bin/magento cache:flush`.
1. Lägg till den andra produkten i kategorin.

<u>Förväntade resultat</u>:

Befintliga produkter som tilldelats i kategorin tas inte bort automatiskt.

<u>Faktiska resultat</u>:

Den första (befintliga) produkten tas bort automatiskt.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
