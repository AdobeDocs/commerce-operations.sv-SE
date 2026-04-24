---
title: 'Översikt: [!DNL Quality Patches Tool] (QPT) v1.1.78'
description: I det här underavsnittet finns en detaljerad beskrivning av de problem som åtgärdats av de korrigeringar som finns i  [!DNL Quality Patches Tool] (QPT) v1.1.78.
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
source-git-commit: 3e003e0cf2428a5e6ec45292fa19aaa2b9e9324d
workflow-type: tm+mt
source-wordcount: '574'
ht-degree: 0%

---

# Översikt: [!DNL Quality Patches Tool] (QPT) v1.1.78

Detta underavsnitt innehåller en detaljerad beskrivning av de problem som åtgärdats av de korrigeringar som finns i [!DNL Quality Patches Tool] (QPT) v1.1.78.

QPT v1.1.78 innehåller följande patchar:
1. **ACP2E-4416**: Korrigerar problemet där kundbelöningspunkter inte initieras när de skapas i Admin.
1. **ACP2E-4419**: Korrigerar problemet där presentkort inte används korrekt vid utcheckning efter lyckad reCAPTCHA v2-validering (jag är inte en robot) på butiken.
1. **ACP2E-4431**: Korrigerar problemet där relaterade produkter som matchar målreglerna tas bort under omindexeringsprocessen.
1. **ACP2E-4448**: Korrigerar problemet där konfigurationsändringar som gjorts under Redis-avbrott inte återspeglas efter Redis-återställning, vilket gör att inaktuella värden kvarstår.
1. **ACP2E-4452**: Korrigerar problemet där produktpriser på snabbordersidan inkluderar moms oavsett momsvisningskonfiguration.
1. **ACP2E-4456**: Korrigerar ett fel där det inte går att avbryta en beställning med en GraphQL-mutation om en beställning som enbart har betalats med presentkort avbryts till statusen Stängt.
1. **ACP2E-4507**: Korrigerar problemet där lösenordsalternativskonfigurationen inte används för begäranden om återställning av kundlösenord som görs via GraphQL-mutationer.
1. **ACP2E-4513**: Korrigerar problemet där utgångna CAPTCHA-bilder inte tas bort från systemet.
1. **ACP2E-4522**: Korrigerar problemet där ett intermittent dubblettnyckelfel inträffar i tabellen quote_coupons när flera sparade kundvagnsbegäranden eller offertförfrågningar körs samtidigt.
1. **ACP2E-4528**: Korrigerar problemet med stadsvalidering i kundadresser, som nu tillåter ett snedstreck (/) och avvisar ogiltiga tecken som !, &quot;, # och ?.
1. **ACP2E-4535**: Korrigerar ett fel där ett glömt lösenordsformulär gör att sessionen förstörs eller genereras om (PHPSESSID-ändringar) och gästvagnen rensas.
1. **ACP2E-4540**: Korrigerar problemet där Fotoramabiblioteket inte lästes in korrekt, vilket innebär att endast den första bifogade bilden visas.
1. **ACP2E-4555**: Korrigerar problemet där moderna telefonnummer som innehåller &quot;.&quot; eller &quot;/&quot; inte har validerats korrekt.
1. **ACP2E-4565**: Korrigerar problemet där GraphQL-frågan returnerar &quot;The current customer is not authorized&quot; när rubriken X-Adobe-Company används.
1. **ACP2E-4591**: Korrigerar problemet där kundsegment baserat på orderantal, t.ex.&quot;förstagångsköpare&quot;, inte uppdaterades när beställningar gjordes via REST API.
1. **ACP2E-4609**: Korrigerar problemet där sidan Mina offerter inte visar några offerter när vissa citattecken innehåller borttagna produkter.
1. **ACP2E-4613**: Korrigerar problemet där stora mediakatalogstrukturer orsakade långsamma getTree-svar, vilket leder till att katalogträdet för utökade media Gallery läses in.
1. **ACP2E-4628**: Korrigerar problemet där import av kunder med e-postadresser i versaler resulterar i ett odefinierat matrisnyckelfel när kontodelning är inställd på Global.
1. **ACP2E-4665**: Korrigerar problemet där underordnade produkter för konfigurerbara produkter som innehåller videor i produktgallerierna inte listas när de begärs via REST API.
1. **ACP2E-4732**: Korrigerar ett fel där partiell indexering stoppades för kunder med ett stort antal uppdateringar när kolumnen version_id i ändringstabellen nådde sitt högsta värde.
1. **ACP2E-4763**: Korrigerar problemet där GraphQL customerOrders-frågan returnerar inflated original_price_including_tax och original_row_total_including_tax när Catalog Prices är inställt på Inklusive Tax på grund av att moms tillämpas två gånger.
1. **ACSD-60989**: Korrigerar problemet där ändringar av en kolumn med en sekundärnyckel via ett deklarativt schema orsakar fel i MariaDB.

Använd menyn till vänster för att navigera till en viss korrigeringssida.
