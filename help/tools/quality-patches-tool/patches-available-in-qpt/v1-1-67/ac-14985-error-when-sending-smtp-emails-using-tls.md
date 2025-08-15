---
title: 'AC-14985: Fel vid sändning av SMTP-e-post med TLS'
description: Använd korrigeringen AC-14985 för att åtgärda Adobe Commerce-problemet när ett fel inträffar när SMTP-e-post (Simple Mail Transfer Protocol) skickas med TLS (Transport Layer Security).
feature: Configuration
role: Admin, Developer
type: Troubleshooting
exl-id: 98d91421-ebfd-4414-ade3-f25d29541874
source-git-commit: 515e6d1f00c910455a2ffddf70c4a450184e7e81
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---

# AC-14985: Fel vid sändning av SMTP-e-post med TLS

Korrigeringen AC-14985 åtgärdar ett problem där ett fel inträffar när SMTP-meddelanden (Simple Mail Transfer Protocol) skickas via TLS (Transport Layer Security). Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67 har installerats. Patch-ID:t är AC-14985. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.9.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.8

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.8 - 2.4.8-p1

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Ett fel inträffar när e-post skickas via SMTP med TLS aktiverat.

<u>Steg som ska återskapas</u>:

1. Konfigurera SMTP enligt följande:
* Transport: SMTP
* Värd: url.to.smtp.host
* Port: 587
* SSL: TLS

<u>Förväntade resultat</u>:

E-postmeddelandet har skickats utan fel.

<u>Faktiska resultat</u>:

Följande fel visas:

```
error:1408F10B:SSL routines:ssl3_get_record:wrong version number [] []
```

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
