---
title: "MDVA-37725: E-postmeddelanden som skickas via icke-standardwebbplatser innehåller standardwebbplatsens URL:er för logotyp"
description: Korrigeringen MDVA-37725 åtgärdar ett problem där asynkrona e-postmeddelanden om beställningar skickas via icke-standardwebbplatser som innehåller URL:er för logotyper från standardwebbplatsen.
feature: Communications, Orders
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---

# MDVA-37725: E-postmeddelanden som skickas via icke-standardwebbplatser innehåller standardwebbplatsens logotyp-URL

>[!WARNING]
>
> MDVA-37725-korrigeringen är föråldrad.

Korrigeringen MDVA-37725 åtgärdar ett problem där asynkrona e-postmeddelanden om beställningar skickas via icke-standardwebbplatser som innehåller URL:er för logotyper från standardwebbplatsen. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.4 har installerats. Patch-ID:t är MDVA-37725. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

Adobe Commerce (alla distributionsmetoder) 2.4.2

**Kompatibel med Adobe Commerce-versioner:**

Adobe Commerce (alla distributionsmetoder) 2.3.0 - 2.4.3

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Asynkrona e-postmeddelanden om beställning skickas via icke-standardwebbplatser som innehåller standardwebbplatsens logotyp-URL:er.

<u>Förutsättningar</u>:

1. Den andra webbplatsen/butiken/butiksvyn måste ha skapats.
1. Konfigurationen för **asynkron sändning** måste aktiveras från **Lager** > **Inställningar** > **Konfiguration** > **Försäljning** > **E-post för försäljning** > **Allmänna inställningar**.
1. Konfigurationen för **Lägg till lagringskod i URL:er** är aktiverad så att du enkelt kan komma åt den sekundära webbplatsen från **Lager** > **Inställningar** > **Konfiguration** > **URL-alternativ**.

<u>Steg som ska återskapas</u>:

1. Lägg order från både den första och den andra butiken.
1. Kör cron för att skicka e-postmeddelanden.
1. Kontrollera e-postmeddelandet från den andra webbplatsen.

<u>Förväntade resultat</u>:

E-postens logotyp-URL innehåller den andra webbplatsens URL.

<u>Faktiska resultat</u>:

E-postens logotyp-URL innehåller standardwebbplatsens URL.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med verktyget för kvalitetskorrigeringar ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i [!DNL Quality Patches Tool]-handboken.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i avsnittet [Patchar i QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html-).
