---
title: 'ACSD-51884: Sökvägen till produktbildens cache är felaktig vid storleksändring, kommando'
description: Använd korrigeringsfilen ACSD-51884 för att åtgärda Adobe Commerce-problemet där sökvägen till produktbildens cacheminne blir felaktig efter att du har kört storlekskommandot.
feature: Products
role: Admin
exl-id: a3779e4b-2749-460e-a0a8-656b26bb06fa
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-51884: Sökvägen till produktbildens cache är felaktig vid storleksändring, kommando

Korrigeringen ACSD-51884 åtgärdar ett problem där ett internt fel där produktbildens cachesökväg blir felaktig efter att kommandot resize körts. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.37 har installerats. Korrigerings-ID är ACSD-51884. Observera att problemet har åtgärdats i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.7-2.4.7

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Sökvägen till produktbildens cache blir felaktig vid storleksändring.

<u>Steg som ska återskapas</u>:

1. Skapa ny webbplats/butik/butiksgranskning.
1. Skapa en produkt och tilldela den till båda webbplatserna och överför produktbilden.
1. Skapa ett nytt tema (se bifogad Adobe.zip).
1. In `app/design/Adobe/theme/etc/view.xml` change:

```
<vars module="Magento_Catalog">
           <var name="product_image_white_borders">1</var>
</vars>
```

till

```
<vars module="Magento_Catalog">
           <var name="product_image_white_borders">0</var>
</vars>
```

1. Använd temat för den tidigare skapade granskningen.
1. Kontrollera produktsidan på den andra webbplatsen. Produktbilden visas korrekt.
1. Använd tömningscache:
   `bin/magento cache:flush`
1. Kontrollera produktsidan på den andra webbplatsen.

<u>Förväntade resultat</u>:

Produktbilden visas korrekt.

<u>Faktiska resultat</u>:

Produktavbildningen finns inte.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
