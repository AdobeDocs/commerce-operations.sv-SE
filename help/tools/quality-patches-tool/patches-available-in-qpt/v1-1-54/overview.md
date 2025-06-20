---
title: 'Översikt: [!DNL Quality Patches Tool] (QPT) v1.1.54'
description: I det här underavsnittet finns en detaljerad beskrivning av de problem som åtgärdats av de korrigeringar som finns i  [!DNL Quality Patches Tool] (QPT) v1.1.54.
feature: Tools and External Services
role: Admin, Developer
exl-id: 1496d15e-edf9-4be0-8e14-ebb2de6f12fe
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---

# Översikt: [!DNL Quality Patches Tool] (QPT) v1.1.54

Detta underavsnitt innehåller en detaljerad beskrivning av de problem som åtgärdats av de korrigeringar som är tillgängliga i [!DNL Quality Patches Tool] (QPT) v1.1.54.

QPT v1.1.54 innehåller följande patchar:

1. **ACSD-60267**: Korrigerar problemet där FPT (Fixed Product Tax) tillämpas korrekt när enkla produkter läggs till direkt i vagnen, men misslyckas när dessa produkter väljs med konfigurerbara produktalternativ.
1. **ACSD-61103**: Korrigerar problemet där antalet fel i tabellen `customer_entity` inte återställs till noll när en kund har loggat in via API-slutpunkter.
1. **ACSD-61134**: Korrigerar problemet där betalningsmetoden [!DNL Braintree Vault] automatiskt avmarkeras i arbetsflödet för utcheckning när en kund uppdaterar sin faktureringsadress genom att avmarkera kryssrutan *[!UICONTROL My billing and shipping address are the same]*.
1. **ACSD-61199**: Korrigerar problemet där CMS sidhierarkiflik inte visar en korrekt trädstruktur när en CMS-sida med en befintlig hierarki redigeras.
1. **ACSD-61200**: Korrigerar problemet där beräkningarna för *[!UICONTROL Total Amount]* och *[!UICONTROL Total Amount Actual]* i försäljningen saknar *[!UICONTROL Discount Tax Compensation Amount]* och *[!UICONTROL Shipping Discount Tax Compensation Amount]*, vilket orsakar avvikelser i försäljningsorderdata.
1. **ACSD-61522**: Korrigerar problemet där det går att ange e-postadresser i gästkundens fält *[!UICONTROL First Name]* och *[!UICONTROL Last Name]* och skicka ogiltiga orderbekräftelsemeddelanden.
1. **ACSD-61756**: Förbättrar prestanda för `AdvancedSalesRule` filter.
1. **ACSD-61799**: Korrigerar problemet där den totala rabatten beräknas felaktigt när flera kundvagnsregler med fasta rabatter tillämpas på offerten.
1. **ACSD-61845**: Korrigerar felet som inträffar när en begäran skickas med endast *text/html* accept header.
1. **ACSD-62056**: Korrigerar problemet där bildöverföring för en konfigurerbar produkt misslyckas om MSI är installerat.
1. **ACSD-62485**: Korrigerar problemet där `async.operations.all` konsumenter slutar arbeta när ett företag skapas.

Använd menyn till vänster för att navigera till en viss korrigeringssida.
