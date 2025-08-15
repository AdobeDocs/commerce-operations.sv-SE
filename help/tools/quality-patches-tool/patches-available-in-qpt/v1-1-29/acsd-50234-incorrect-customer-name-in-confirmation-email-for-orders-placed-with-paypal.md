---
title: 'ACSD-50234: Felaktigt kundnamn i bekräftelsemeddelande via e-post för beställningar som gjorts med  [!DNL PayPal]'
description: Använd korrigeringen ACSD-50234 för att åtgärda Adobe Commerce-problemet där kundnamnet visas felaktigt i bekräftelsemeddelandet för beställningar som gjorts med  [!DNL PayPal].
feature: Admin Workspace, Communications, Orders, Payments
role: Admin
exl-id: 9a8a7cef-0166-4b4b-96a0-87fd4f1a0ef3
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 0%

---

# ACSD-50234: Felaktigt kundnamn i bekräftelsemeddelande för beställningar som gjorts med [!DNL PayPal]

Korrigeringen ACSD-50234 åtgärdar ett problem där kundnamnet visas felaktigt i bekräftelsemeddelandet för beställningar som gjorts med [!DNL PayPal]. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.29 är installerad. Korrigerings-ID är ACSD-50234. Observera att problemet har åtgärdats i Adobe Commerce 2.4.5.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.7 - 2.4.4-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Bekräftelsemeddelande för beställningar som gjorts med [!DNL PayPal] visar fel kundnamn.

<u>Steg som ska återskapas</u>

1. Aktivera **[!UICONTROL PayPal Express Checkout]**.
1. Navigera till frontend som gäst.
1. Lägg produkter i kundvagnen.
1. Checka ut med **[!UICONTROL PayPal Express Checkout]** som betalningsmetod.
1. Kontrollera e-postmeddelandet med orderbekräftelsen.

<u>Förväntade resultat</u>

E-postmeddelandet med orderbekräftelsen, fakturameddelandet och alla leveransrelaterade e-postmeddelanden adresseras till kundens namn.

<u>Faktiska resultat</u>

E-postmeddelandet med orderbekräftelsen, fakturameddelandet och alla försändelserelaterade e-postmeddelanden adresseras till *Gäst*.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
