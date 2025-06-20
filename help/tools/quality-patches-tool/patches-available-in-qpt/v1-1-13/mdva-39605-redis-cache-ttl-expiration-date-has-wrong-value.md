---
title: 'MDVA-39605: TTL för Redis-cache (förfallodatum) har fel värde'
description: MDVA-39605-korrigeringen löser problemet där Redis cache TTL (förfallodatum) har fel värde. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.13 är installerat. Korrigerings-ID är MDVA-39605. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.
feature: Cache, Console, Services
role: Admin
exl-id: 65f5d50a-e49e-4155-9d1a-3758f0c723a8
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '554'
ht-degree: 0%

---

# MDVA-39605: TTL för Redis-cache (förfallodatum) har fel värde

MDVA-39605-korrigeringen löser problemet där Redis cache TTL (förfallodatum) har fel värde. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.13 är installerat. Korrigerings-ID är MDVA-39605. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.4 - 2.4.4

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

TTL-värdet för Redis-cachen (förfallodatum) har ett felaktigt värde.

<u>Steg som ska återskapas</u>:

Testa korrigeringen genom att rensa cacheminnet och öppna en konfigurerbar produkt i butiken. Öppna sedan en terminal (konsol) och följ stegen nedan:

1. Kör kommandot: `redis-cli`.
1. Kör `KEYS "*PRICE"` (det ska bara finnas en nyckel i resultatet, till exempel `zc:ti:e54_PRICE`). Kopiera nyckeln.
1. Kör `SMEMBERS` följt av nyckeln från föregående steg (till exempel `SMEMBERS zc:ti:e54_PRICE`). Kopiera valfri tangent från resultatet (t.ex. e54_4E67B390D5C28FC7C3D9BB0D37AB3F7B5E576421).
1. Kör `KEYS "*<key>"` med nyckelnamnet från föregående steg för att hämta det fullständiga nyckelnamnet (till exempel `KEYS "*e54_4E67B390D5C28FC7C3D9BB0D37AB3F7B5E576421"`). Det ska bara finnas en nyckel i resultatet (till exempel `zc:k:e54_4E67B390D5C28FC7C3D9BB0D37AB3F7B5E576421`). Som du kanske märker är det fullständiga nyckelnamnet bara nyckelnamnet med prefixet `zc:k:`. Kopiera det fullständiga nyckelnamnet.
1. Kör `HGETALL` följt av det fullständiga nyckelnamnet från steg 4 för att kontrollera värdet. Värdet ska innehålla serialiserade data för associerade produkter för en relaterad konfigurerbar produkt.
1. Kör `TTL` följt av det fullständiga nyckelnamnet från steg 4 för att kontrollera om nyckeln har en förfallotid. Resultatet ska skilja sig från **-1** och **-2** och ska vara cirka 2592000 (30 dagar). Även om den förfallodag som anges i koden är ett år har Redis-biblioteket i Adobe Commerce en hög maxgräns på 2592000-tal.

<u>Förväntade resultat</u>:

Förfallogränsen är 2592000s

<u>Faktiska resultat</u>:

Förfallogränsen är **-1** eller **-2**.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med verktyget för kvalitetskorrigeringar ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i [!DNL Quality Patches Tool]-handboken.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
