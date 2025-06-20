---
title: 'ACSD-63870: Kunden har inte loggat ut korrekt vid ändring av företagsstatus'
description: Använd patchen ACSD-63870 för att åtgärda Adobe Commerce-problemet där en företagskund inte är korrekt utloggad när företagets status ändras under en aktiv kundsession.
feature: Customers, B2B, Companies
role: Admin, Developer
exl-id: 4488f3cb-bb34-491e-8821-c2e98ff69429
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-63870: Kunden har inte loggat ut korrekt vid ändring av företagsstatus

Korrigeringen ACSD-63870 löser problemet där en företagskund inte är korrekt utloggad när företagets status ändras under en aktiv kundsession. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.59 har installerats. Korrigerings-ID är ACSD-63870. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4-p6

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.4-p10

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Kundutloggningsfel när företagsstatus ändras under en aktiv kundsession.

<u>Steg som ska återskapas</u>:

1. Aktivera B2B-funktioner.
1. Skapa en enkel produkt.
1. Skapa ett nytt företag och markera det som *Aktivt*.
1. Logga in som företagsanvändare och lägg till en produkt i kundvagnen.
1. Gå till kassan till steget [!UICONTROL Shipping Address]. Ange inte adressen.
1. Gå till admin och ändra företagsstatus till *Väntar på godkännande*.
1. Gå tillbaka till fronten och fyll i leveransadressen.

<u>Förväntade resultat</u>:

Kunden har loggats ut.

<u>Faktiska resultat</u>:

* Användare får tag i felet *Något gick fel*.
* `var/log/exception.log` innehåller:

  ```
  report.CRITICAL: InvalidArgumentException: Incorrect theme identification key in /home/lib/internal/Magento/Framework/View/Design/Theme/FlyweightFactory.php:60
  ```


## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Ytterligare steg krävs efter installationen av korrigeringsfilen

(Det här avsnittet är valfritt. Det kan finnas åtgärder som krävs efter att du har implementerat korrigeringen för att åtgärda problemet.) 

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
