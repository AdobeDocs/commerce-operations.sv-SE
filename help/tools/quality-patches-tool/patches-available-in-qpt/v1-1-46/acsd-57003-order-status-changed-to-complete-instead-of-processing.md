---
title: 'ACSD-57003: Orderstatus ändras till *Fullständigt* i stället för att ändras till *Bearbetning*'
description: Använd patchen ACSD-57003 för att åtgärda Adobe Commerce-problemet där orderstatusen ändras till *Complete* i stället för att ändras till *Processing*.
feature: Orders, Invoices, Shipping/Delivery
role: Admin, Developer
exl-id: a28ecc35-5c9a-4bba-b0b9-67fbe37ed8c3
source-git-commit: 128107310416e97edca3b122e97456138d04073f
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# ACSD-57003: Orderstatus ändras till *Fullständigt* i stället för att ändras till *Bearbetning*

ACSD-57003-korrigeringen åtgärdar ett problem där orderstatusen ändras till *Complete* i stället för att ändras till *Processing*. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.46 har installerats. Korrigerings-ID är ACSD-57003. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p3, 2.4.6-p8, 2.4.7-p3

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6 - 2.4.6-p9, 2.4.7-p2 - 2.4.7-p4

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Orderstatusen ändras till *Fullständigt* i stället för att ändras till *Bearbetning* när en order delvis återbetalas och delvis skickas.

<u>Steg som ska återskapas</u>:

1. Skapa en beställning med två konfigurerbara produkter.
1. Fakturera alla artiklar.
1. Leverera bara den första artikeln.
1. Återbetala/skapa en kreditnota för endast den levererade artikeln (*första artikeln*).
1. Kontrollera orderstatus.

<u>Förväntade resultat</u>:

Orderstatusen måste vara i tillståndet _Processing_.

<u>Faktiska resultat</u>:

Orderstatusen ändras till *Fullständig* efter att en kreditnota för den delvis levererade artikeln har skapats.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
