---
title: 'ACSD-48318: Fel vid kapsling av miljöemulering i system.log'
description: Använd patchen ACSD-48318 för att åtgärda Adobe Commerce-problemet där felmeddelandet *main.ERROR:Environment emulation nesting is not allowed* visas i "system.log" varje gång ett fakturameddelande skickas.
feature: System, Orders
role: Admin, Developer
exl-id: 24af18de-80dd-4e0a-bdf9-5b9c075fc608
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '313'
ht-degree: 0%

---

# ACSD-48318: Fel vid kapsling av miljöemulering i `system.log`

Korrigeringen ACSD-48318 åtgärdar ett problem där felmeddelandet *main.ERROR:Environment emulation nesting is not allowed* visas i `system.log` varje gång ett fakturameddelande skickas. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.53 har installerats. Korrigerings-ID är ACSD-48318. Observera att problemet har åtgärdats i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.6-p8

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Felmeddelandet *Miljöemuleringsinkapsling är inte tillåtet* visas i `system.log` varje gång ett fakturameddelande skickas.

<u>Steg som ska återskapas</u>:

1. Placera en order och generera en faktura.
1. Öppna fakturan från Admin och klicka på **[!UICONTROL Send Email]**.
1. Följ samma steg för *kreditnota* och *leverans* genom att klicka på **[!UICONTROL Send Email]**.

<u>Förväntade resultat</u>:

Inga fel i `system.log`.

<u>Faktiska resultat</u>:

`system.log` är översvämmad med *main.ERROR: Det är inte tillåtet att kapsla miljöemulering*.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning &#x200B;](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

[[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
