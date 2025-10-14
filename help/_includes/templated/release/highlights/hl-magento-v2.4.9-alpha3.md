---
source-git-commit: 233ff6d5de2f4da3d477e70d066dd5cd46c771ee
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---
# Versionsinformation för Magento Open Source (v2.4.9-alpha3)

## Högdagrar i v2.4.9-alpha3

Följande högdagrar gäller för Magento Open Source version 2.4.9-alpha3.

### Braintree

#### Vaulting Google Pay via Account Area

I Magento 2.4.9-alpha3 kan man nu vault sina Google Pay-kort via kontoområdet när Google Pay Vault är aktiverat i Braintree. Vaultade kort visas under lagrade betalningsmetoder, kan användas för framtida inköp vid utcheckning och kan tas bort av kunden. Detta ger bättre stöd än Cards och PayPal till Google Pay.

_BUNDLE-3459_

#### Länka Magento-beställning till Braintree portalbeställning

I Magento 2.4.9-alpha3 har nu en Braintree Portal Link lagts till i orderinformationen i Magento Admin. När du klickar på länken öppnas den relaterade transaktionen i Braintree Portal (på en ny flik) med hjälp av handels-ID och transaktions-ID från Magento-ordern. Detta möjliggör direkt korsreferens utan att logga in i båda systemen separat.

_BUNDLE-3461_

#### Real Time Account Updater (RTAU)

Funktionen Real Time Account Updater (RTAU) i Magento 2.4.9-alpha3 för Braintree säkerställer att kortuppgifterna för Visa, Mastercard och Discover uppdateras automatiskt när korten går ut eller ersätts. Detta minimerar misslyckade betalningar, håller Magento Vault aktuellt och hoppar över typer som inte stöds (förbetald, Apple Pay, Google Pay) utan fel.

_BUNDLE-3462_

#### Stöd för ELO-kortstyp för Braintree-kortbetalningar

I Magento 2.4.9-alpha3 har stöd för typen av ELO-kort lagts till i Braintree Payments. Administratörer kan nu aktivera ELO i kreditkortskonfigurationen och kunderna kan beställa via ELO-kort i kassan, vilket ger smidiga transaktioner via Braintree.

_BUNDLE-3464_

### Ramverk

#### Migrera från RabbitMQ till Apache ActiveMQ

_AC-14558_

#### Uppgradera chart.js-beroendet till den senaste versionen

Diagram.js-beroendet uppgraderas till den senaste versionen, 4.5.0

_AC-15133 - [GitHub-kodbidrag](https://github.com/magento/magento2/commit/657f983e)_

#### Migrering från Laminas MVC

Adobe Commerce har infört en intern MVC-implementering som ersätter den gamla Laminas MVC för att säkerställa långsiktig kompatibilitet och stabilitet utöver PHP 8.5. Den här förändringen förbättrar prestanda, minskar externa beroenden och ger en mer framtidsklar grund för Commerce

_AC-15160_
