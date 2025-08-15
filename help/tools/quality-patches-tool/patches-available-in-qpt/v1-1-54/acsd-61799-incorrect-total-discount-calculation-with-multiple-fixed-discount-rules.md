---
title: 'ACSD-61799: Felaktig total rabattberäkning med flera fasta rabattregler tillämpade på offert'
description: Använd patchen ACSD-61799 för att åtgärda Adobe Commerce-problemet där den totala rabatten inte beräknas korrekt när flera kundvagnsregler med fasta rabatter tillämpas på offerten.
feature: Price Rules
role: Admin, Developer
exl-id: a87ec1cd-f141-43b9-bde1-eca354c12d4e
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 0%

---

# ACSD-61799: Felaktig total rabattberäkning med flera fasta rabattregler tillämpade på offert

Korrigeringsfilen ACSD-61799 löser/åtgärdar ett problem där den totala rabatten beräknas felaktigt när flera kundvagnsregler med fasta rabatter tillämpas på offerten. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54 har installerats. Korrigerings-ID är ACSD-61799. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4-p6

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.4-p11

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Den totala rabatten beräknas felaktigt när flera kundvagnsregler med *[!UICONTROL Fixed amount discount for the whole cart]* tillämpas på en kundvagn.

<u>Steg som ska återskapas</u>:

1. Skapa fyra produkter till priset 1 000 dollar.
1. Skapa tre kundprisregler utan villkor som ger 100 USD rabatt för hela kundvagnen.
1. Skapa en annan kundvagnsprisregel som ger en rabatt på 100 USD för hela kundvagnen, med ett villkor som förhindrar att regeln tillämpas.
1. Inaktivera regeln.
1. Lägg tre produkter i kundvagnen och lägg rabatten i kundvagnen.
1. Lägg till ytterligare produkter i kundvagnen och observera rabatten i kundvagnen.
1. Aktivera den inaktiverade kundvagnsprisregeln.
1. Uppdatera kundvagnssidan och observera rabatten i kundvagnen.

<u>Förväntade resultat</u>:

1. Rabattbeloppet ändras inte om du lägger till ytterligare produkter i kundvagnen.
1. Rabattbeloppet ändras inte om kundvagnsprisregeln aktiveras med ett villkor som inte gäller.

<u>Faktiska resultat</u>:

1. Om du lägger till ytterligare produkter i kundvagnen ändras rabattbeloppet.
1. Om du aktiverar kundvagnsprisregeln med ett villkor som inte gäller, ändras rabattbeloppet.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
