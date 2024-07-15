---
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '64'
ht-degree: 0%

---
# Känsliga data

Adobe Commerce använder din krypteringsnyckel för att kryptera följande:

* Kreditkortsinformation
* Användarnamn och lösenord som anges i Admin-konfigurationen (t.ex. inloggningar på betalningsgateways)
* CAPTCHA-värden som skickas över nätverket

Adobe Commerce krypterar *inte*:

* Användarnamn och lösenord för administration och kund (dessa lösenord hashas)
* Adress
* Telefonnummer
* Andra typer av personligt identifierbar information förutom kreditkortsnummer
