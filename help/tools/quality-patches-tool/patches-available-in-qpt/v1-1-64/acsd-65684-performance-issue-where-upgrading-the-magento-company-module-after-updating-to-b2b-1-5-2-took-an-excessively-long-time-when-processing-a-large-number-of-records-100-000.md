---
title: 'ACSD-65684: Det går långsamt att uppgradera Magento_Company i B2B 1.5.2 med över 100 000 poster i company_structure'
description: Använd patchen ACSD-65684 för att åtgärda Adobe Commerce-problemet där det tar för lång tid att uppgradera Magento_Company-modulen i B2B 1.5.2 på grund av att ett stort antal poster bearbetas (~100 000+) i tabellen company_structure.
feature: B2B
role: Admin, Developer
type: Troubleshooting
exl-id: 1b45ebe4-4fb4-4fb5-b107-a2d44ec784e0
source-git-commit: b1912bbc5aabd36067563326ee5c6bb84e14441d
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---

# ACSD-65684: Uppgradering av `Magento_Company` i [!DNL B2B] 1.5.2 är långsamt med över 100 000 poster i `company_structure`

Korrigeringen ACSD-65684 åtgärdar ett prestandaproblem där det tar för lång tid att uppgradera modulen `Magento_Company` i [!DNL B2B] 1.5.2 vid bearbetning av 100 000+ poster i tabellen `company_structure`. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64 har installerats. Korrigerings-ID är ACSD-65684. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.9.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce B2B (alla distributionsmetoder) 1.5.2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce B2B (alla distributionsmetoder) 1.5.2

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Prestandaproblem där det tar för lång tid att uppgradera modulen `Magento_Company` i [!DNL B2B] 1.5.2 vid bearbetning av mer än 100 000 poster i tabellen `company_structure`.

<u>Steg som ska återskapas</u>:

1. Installera Adobe Commerce 2.4.7-p4 med [!DNL B2B].
1. Lägg till 100 000 poster i tabellen `company_structure`.
1. Uppgradera till Adobe Commerce 2.4.7-p5 och den senaste [!DNL B2B]-modulen (1.5.2).
1. Använd patch ACSD-65540.
1. Kör:

```
bin/magento setup:upgrade
```

<u>Förväntade resultat</u>:

`setup:upgrade` slutförs inom rimlig tid.

<u>Faktiska resultat</u>:

Det tar för lång tid för `setup:upgrade` att slutföra.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
