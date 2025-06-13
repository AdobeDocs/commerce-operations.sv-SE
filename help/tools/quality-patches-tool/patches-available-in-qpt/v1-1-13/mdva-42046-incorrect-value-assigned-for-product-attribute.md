---
title: 'MDVA-42046: Felaktigt värde tilldelat för produktattribut'
description: MDVA-42046-korrigeringen åtgärdar ett problem där ett felaktigt värde tilldelas för produktattributet när en produkt som har ett datuminmatningsfält uppdateras. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.13 är installerat. Korrigerings-ID är MDVA-42046. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.
feature: Attributes, Products
role: Admin
exl-id: ff5903ff-70b3-4274-a8a1-450c2fde9750
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '509'
ht-degree: 0%

---

# MDVA-42046: Felaktigt värde tilldelat för produktattribut

MDVA-42046-korrigeringen åtgärdar ett problem där ett felaktigt värde tilldelas för produktattributet när en produkt som har ett datuminmatningsfält uppdateras. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.13 är installerat. Korrigerings-ID är MDVA-42046. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2-p2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.4 - 2.3.5-p2 och 2.4.0 - 2.4.4

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

När du har sparat en produkt med `news_from_date`- och/eller `news_to_date`-fält återställs värdena från dessa fält till standardvärdena.

<u>Steg som ska återskapas</u>:

1. Skapa en enkel produkt.
1. Exportera den produkt som skapades i steg ett.
1. I den exporterade CSV-filen anger du värden i fälten `news_from_date` och `news_to_date`. Exempel: 2021-05-15 och 2021-06-18.
1. Importera produkten med den ändrade CSV-filen.
1. Lägg till ytterligare kolumner&quot;Ange produkten som ny från datum&quot; och&quot;Ange produkten som ny till datum&quot; i produktrutnätet.
1. Öppna redigeringssidan för produkten och klicka utan ändringar på **Spara**.
1. Gå tillbaka till produktrutnätet och kontrollera produktinformationen.

<u>Förväntade resultat</u>:

Både&quot;Ange produkten som ny från datum&quot; och&quot;Ange produkten som ny till datum&quot; är desamma som innan du sparar.

<u>Faktiska resultat</u>:

* Värdena i kolumnerna&quot;Ange produkten som ny från datum&quot; och&quot;Ange produkten som ny till datum&quot; har ändrats.

* Kolumnen Ange produkten som ny från datum visar det aktuella datumet och kolumnen Ange produkten som ny till datum är tom.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med verktyget för kvalitetskorrigeringar ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i [!DNL Quality Patches Tool]-handboken.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
