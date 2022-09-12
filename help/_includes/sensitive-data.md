---
source-git-commit: 475dbc056ac3e6a00c8f794259bb0fbf04143687
workflow-type: tm+mt
source-wordcount: '72'
ht-degree: 0%

---
# Känsliga data

Adobe Commerce och Magento Open Source använder din krypteringsnyckel för att kryptera följande:

* Kreditkortsinformation
* Användarnamn och lösenord som anges i Admin-konfigurationen (t.ex. inloggningar på betalningsgateways)
* CAPTCHA-värden som skickas över nätverket

Adobe Commerce och Magento Open Source *not* kryptera:

* Användarnamn och lösenord för administration och kund (dessa lösenord hashas)
* Adress
* Telefonnummer
* Andra typer av personligt identifierbar information förutom kreditkortsnummer
