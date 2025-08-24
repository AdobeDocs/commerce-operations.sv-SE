---
title: 'ACSD-67347: Beställningen misslyckas med felet"Kan inte hämta ett lås" när kupongkoder används'
description: Använd korrigeringsfilen ACSD-67347 på Adobe Commerce-utgåvan om beställningarna misslyckas med felet"Kan inte hämta ett lås" när kupongkoderna innehåller specialtecken (t.ex. BIT/123456) och fillåsning är aktiverat.
feature: Checkout, Shopping Cart
role: Admin, Developer
type: Troubleshooting
source-git-commit: 1a48428efbb022b53320370f68691eaed44809b3
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---


# ACSD-67347: Beställningen misslyckas med *Det går inte att hämta ett lås*-fel när kupongkoder används

Korrigeringen ACSD-67347 åtgärdar ett problem där beställningar misslyckas med ett *Det går inte att få ett lås* när kupongkoder innehåller specialtecken (t.ex. BIT/123456) och fillåsning är aktiverat. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69 har installerats. Korrigerings-ID är ACSD-67347. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.9.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p12

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p11 - 2.4.5-p13

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Orderfel med felet *Kan inte hämta ett lås* när kuponger med specialtecken används och fillåsning är aktiverat.

<u>Steg som ska återskapas</u>:

1. Installera 2.4-utveckling.
1. Ange fillåskonfigurationen i filen `env.php`:

   ```
   'lock' => [
           'provider' => 'file',
           'config' => [
               'path' => '/Users/awijesooriya/sites/acsd15194dev/locks'
           ]
       ],
   ```

1. Skapa en kundvagnsregel med en kupong med kupongkodformatet: *BIT/123456*.
1. Skapa en enkel produkt.
1. Lägg produkten i kundvagnen och använd kupongkoden.
1. Gå till kassan och lägg ordern.

<u>Förväntade resultat</u>:

Beställningar kan beställas eftersom det inte finns några begränsningar för att skapa kupongkoder.

<u>Faktiska resultat</u>:

Det går inte att montera ordern. Följande fel visas: *Det går inte att låsa.*

```
File "/Users/test/sites/test/locks/coupon_code_123/abc" cannot be opened Warning!fopen(/Users/test/sites/test/locks/coupon_code_123/abc): Failed to open stream: No such file or directory
```

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
