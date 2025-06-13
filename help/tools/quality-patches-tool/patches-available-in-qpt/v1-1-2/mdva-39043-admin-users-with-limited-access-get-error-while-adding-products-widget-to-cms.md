---
title: 'MDVA-39043: Administratörsanvändare får felmeddelande om att lägga till widget på CMS-sidan'
description: Korrigeringen MDVA-39043 åtgärdar ett problem där administratörsanvändare med begränsad åtkomst får ett fel när de lägger till widgeten"Produkter" på CMS-sidan. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.2 är installerat. Korrigerings-ID är MDVA-39043. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.
feature: Admin Workspace, CMS, Products
role: Admin
exl-id: 82488249-cca3-4a28-bdc1-fa93a4c9dc2f
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# MDVA-39043: Administratörsanvändare får felmeddelande om att lägga till widget på CMS-sidan

Korrigeringen MDVA-39043 åtgärdar ett problem där administratörsanvändare med begränsad åtkomst får ett fel när de lägger till widgeten&quot;Produkter&quot; på CMS-sidan. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.2 har installerats. Korrigerings-ID är MDVA-39043. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

Adobe Commerce (alla distributionsmetoder) 2.4.2-p1

**Kompatibel med Adobe Commerce-versioner:**

Adobe Commerce (alla distributionsmetoder) 2.3.4 - 2.4.3

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Administratörsanvändare med begränsad åtkomst får ett fel när widgeten&quot;Produkter&quot; läggs till på CMS-sidan.

<u>Steg som ska återskapas</u>:

1. Logga in på backend med administratören som endast har åtkomst till redigeringsinnehåll.
1. Gå till **Innehåll** > **Sidor**.
1. Öppna en sida som du vill redigera.
1. Redigera innehållet med **Page Builder**.
1. Lägg till widgeten **Produkt** från avsnittet **Lägg till innehåll**.
1. Klicka på **Konfigurera** i widgeten **Produkt**.

<u>Förväntade resultat</u>:

Inget fel visas.

<u>Faktiska resultat</u>:

Följande felmeddelande har tagits emot:

`*A technical problem with the server created an error. Try again to continue what you were doing. If the problem persists, try again later.*`

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med verktyget för kvalitetskorrigeringar ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i [!DNL Quality Patches Tool]-handboken.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
