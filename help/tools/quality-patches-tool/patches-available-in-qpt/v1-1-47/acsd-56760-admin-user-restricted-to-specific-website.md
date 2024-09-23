---
title: 'ACSD-56760: Administratörsanvändaren är begränsad till en specifik webbplats och kan inte sortera eller lägga till nya produkter'
description: Använd patchen ACSD-56760 för att åtgärda Adobe Commerce-problemet där den administratör som är begränsad till en viss webbplats inte kan sortera eller lägga till nya produkter i en kategori om webbutiken har en egen rotkategori.
role: Admin
source-git-commit: d722ba5ba25ffc03d87b9eddeb2830353124055d
workflow-type: tm+mt
source-wordcount: '496'
ht-degree: 0%

---

# ACSD-56760: Administratörsanvändaren är begränsad till en specifik webbplats och kan inte sortera eller lägga till nya produkter

Korrigeringsfilen ACSD-56760 åtgärdar ett problem där administratören som är begränsad till en viss webbplats och inte kan sortera eller lägga till nya produkter i en kategori om webbutiken har en egen rotkategori. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.47 har installerats. Korrigerings-ID är ACSD-56760. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6 - 2.4.6-p4

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Administratörsanvändaren som är begränsad till en viss webbplats och som inte kan sortera eller lägga till nya produkter i en kategori om webbutiken har en egen rotkategori.

<u>Steg som ska återskapas</u>:

1. Skapa *2*-webbplatser.
1. Skapa en **[!UICONTROL restricted admin user]** med åtkomst till endast *1*-webbplatsen.
1. Logga in som **[!UICONTROL restricted admin user]** och försök ändra produktpositionerna i en kategori.

*Fall 1*:

* *2* butiker.
* *2* rotkategorier, alla webbplatser som tilldelas till dess egen kategorirot.

*Fall 2*:

* *2* butiker.
* Endast rotkategorin *1* har tilldelats båda webbplatserna.

<u>Förväntade resultat</u>:

* *Fall 1*: Den begränsade administratören ska kunna sortera produkter i den tillgängliga kategorin.
* *Fall 2*: Den begränsade administratören kan inte sortera produkter i den tillgängliga kategorin eftersom detta även påverkar den begränsade butiken.

<u>Faktiska resultat</u>:

* *Fall 1*: Den begränsade administratören kan inte sortera produkter i den tillgängliga kategorin.
* *Fall 2*: Den begränsade administratören kan sortera produkter i den tillgängliga kategorin, vilket påverkar de begränsade butikerna.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
