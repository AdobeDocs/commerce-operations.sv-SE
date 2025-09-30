---
title: Produkttillgänglighet
description: Läs mer om vilka Adobe Commerce-funktioner som stöds och kontrollera om de är kompatibla med vissa Adobe Commerce-utgåvor.
exl-id: 7e8e8ac2-a0b9-4023-a813-c0f1293e54c2
source-git-commit: d18a5d3b0723202328afe445ab1ba4673fa5f9b7
workflow-type: tm+mt
source-wordcount: '311'
ht-degree: 0%

---

# Produkttillgänglighet

I följande tabell beskrivs statusen för Adobe Commerce programvarutillgänglighet och var den ska hämtas, särskilt för program som är tillgängliga utanför det vanliga Adobe Commerce Composer-paketet.

Tjänster och tillägg testas på den senaste versionen av Commerce när produkterna släpps.

Versioner som stöds har testats fullständigt av Adobe. Hjälp för de versioner som stöds finns på Adobe kundsupport. Äldre versioner kanske fungerar som de ska men stöds inte officiellt.

>[!NOTE]
>
>Stöd för Adobe Commerce-versioner innefattar även stöd för [tillgängliga säkerhetsuppdateringar](versions.md).

## Adobe Authaged Extensions

De här Adobe Commerce-tilläggen är fristående från Adobe Commerce centrala kodbas. Detta gör att Adobe kan släppa versioner av dessa tillägg inom en mer flexibel tidsram och ge kunderna tidigare tillgång till nya funktioner.

Följande tabell visar versionsstödet för varje tillägg i förhållande till Adobe Commerce-versionen.

{{$include /help/_includes/templated/product-availability-extensions.md}}

## Commerce Services

[Commerce-tjänster](https://experienceleague.adobe.com/docs/commerce/user-guides/home.html?lang=sv-SE) är en uppsättning värdfunktioner från Adobe som ger robusta funktioner och snabba svarstider i kombination med din Commerce-instans.

Handlarna bör använda den senaste versionen av en tjänst för att säkerställa högsta stabilitet och funktionalitet. Dokumentationen beskriver den version som släpps för tillfället.

* Adobe Commerce Services är för närvarande kompatibelt med Commerce 2.4.4 och senare. Handlarna bör använda den senaste versionen av tjänsten.
* Tjänster anses vara kompatibla med tidigare versioner av Commerce 2.4.x, men stöds inte officiellt.
* Tjänster är inte kompatibla med Commerce 2.3.x, förutom produktrekommendationerna 3.3.7 och tidigare.
* Betalningstjänsten är för närvarande kompatibel med Magento Open Source 2.4.4 och senare. Handlarna bör använda den senaste versionen av tjänsten.

Följande tabell visar versionsstödet för varje tjänst i förhållande till Adobe Commerce-versionen.

{{$include /help/_includes/templated/product-availability-services.md}}

<!-- Last updated from includes: 2025-09-23 12:01:22 -->
