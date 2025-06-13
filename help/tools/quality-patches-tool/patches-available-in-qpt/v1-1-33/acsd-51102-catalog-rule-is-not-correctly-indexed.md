---
title: 'ACSD-51102: Katalogregel som används för ett stort antal produkter har inte indexerats korrekt'
description: Använd patchen ACSD-51102 för att åtgärda Adobe Commerce-problemet där en katalogregel som tillämpas på ett stort antal produkter inte indexeras korrekt när regeln aktiveras av en schemalagd uppdatering.
feature: Catalog Management, Products
role: Admin
exl-id: 35a8078d-667b-4101-8562-ece052b44c9c
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%

---

# ACSD-51102: Katalogregel som används för ett stort antal produkter har inte indexerats korrekt

Korrigeringen ACSD-51102 åtgärdar ett problem där en katalogregel som tillämpas på ett stort antal produkter inte indexeras korrekt när regeln aktiveras av en schemalagd uppdatering. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.33 är installerad. Korrigerings-ID är ACSD-51102. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2 - 2.4.6-p1

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

En katalogregel som tillämpas på ett stort antal produkter indexeras inte korrekt när regeln aktiveras av en schemalagd uppdatering.

Förutsättningar:

* Kronjobbet är klart och körs varje minut.

<u>Steg som ska återskapas</u>:

1. Skapa en stor katalog med tusentals produkter för att få körningstiden för indexerarna för *katalogregeln* på mer än 120 sekunder när katalogregler aktiveras.
2. Skapa två katalogregler med statusen *Aktiv* inställd på *Nej*.  Exempel: *Test 1* och *Test 2*. Varje regel ska påverka alla produkter i katalogen och göra så att indexeraren körs i mer än 120 sekunder.
3. Kontrollera att statusen för indexeraren är *klar*.
4. Skapa schemalagda uppdateringar för att aktivera dessa två regler. Schemat *Test 2* ska påbörjas kort efter *Test 1*. Exempel: med en minuts skillnad.
5. Kontrollera produktpriserna i Store.

<u>Förväntade resultat</u>

Rabatter från båda reglerna tillämpas.

<u>Faktiska resultat</u>

Endast rabatten för den första regeln tillämpas.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) i [!DNL Quality Patches Tool]-handboken.
