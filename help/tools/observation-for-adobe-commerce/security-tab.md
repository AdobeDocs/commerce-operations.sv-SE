---
title: The [!UICONTROL Security] tab
description: Läs mer om [!UICONTROL Security] flik för [!DNL Observation for Adobe Commerce].
exl-id: b567e4a4-534e-4151-b6f6-bf59b1bd4028
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# The [!UICONTROL Security] tab

The **[!UICONTROL Security]** på fliken förklaras säkerhetsproblem och deras potentiella orsaker isoleras. Dessutom beskrivs bildrutorna på fliken.

## [!UICONTROL API calls by IP, details by URL]

The **[!UICONTROL API calls by IP, details by URL]** bildrutan visar ett antal API-anrop per IP för en vald tidsram. I den här bildrutan visas IP-adressen och API-URL:en som den IP-adressen användes till.

![API-anrop via IP](../../assets/tools/observation-for-adobe-commerce/calls-by-ip.jpg)

## [!UICONTROL Forgot Password]

The **[!UICONTROL Forgot Password]** åtkomstbildrutan visar antalet försök till glömt lösenord under en vald tidsram. Hög aktivitet mot en IP-adress kan vara en attack på webbplatsen.

![Glömt lösenord](../../assets/tools/observation-for-adobe-commerce/forgot-password.jpg)

## [!UICONTROL Create Account access]

The **[!UICONTROL Create Account access]** visas antalet nya kontoaktiviteter under en vald tidsram. Hög aktivitet från en enda IP-adress kan tyda på en attack.

![create-account-access](../../assets/tools/observation-for-adobe-commerce/create-account-access.png)

## [!UICONTROL POST activities]

The **[!UICONTROL POST activities]** bildrutan visar `POST` aktiviteter för platsen, facetterade på `client_ip` från [!DNL Fastly] loggar. Den visar också den URL som är tillgänglig för IP-adressen.

![POST](../../assets/tools/observation-for-adobe-commerce/POST-activities.jpg)

## [!UICONTROL POST activities summary table]

The **[!UICONTROL POST activities summary table]** bildrutan visar sammanfattningen `POST` aktiviteter för platsen, facetterade på `client_ip` från [!DNL Fastly] loggar. Den visar även antalet för den URL som är tillgänglig för IP-adressen. Antalet gäller för den valda tidsramen.

![Sammanfattning av POSTER](../../assets/tools/observation-for-adobe-commerce/POST-activities-summary.jpg)

## [!UICONTROL POST activities details table]

The **[!UICONTROL POST activities details table]** bildrutan visar `POST` aktiviteter för webbplatsen från [!DNL Fastly] loggar. Den visar även all information från [!DNL Fastly] logga för dessa förfrågningar. Den är begränsad till de senaste 2000 ansökningarna.
![POST-aktiviteter-details](../../assets/tools/observation-for-adobe-commerce/POST-activities-details.jpg)

## [!UICONTROL Guest Carts activities]

The **[!UICONTROL Guest Carts activities]** Bildrutan visar antalet gästvagnsaktiviteter under en vald tidsram, uppdelat efter IP-adress och URL. Gästvagnar kan användas i en kardinfarkt. I den här bildrutan visas det totala antalet begäranden där gästvagnens URL:er är tillgängliga.

![Gästvagnsaktiviteter](../../assets/tools/observation-for-adobe-commerce/guest-carts-activities.jpg)

## [!UICONTROL API – forgot password, create account by Countries]

The **[!UICONTROL API – forgot password, create account by Countries]** visas antalet konton som skapats och begäranden om att återställa ett glömt lösenord under en vald tidsram. Det är även lättare att visa ursprungslandet för begäran. Denna ram fokuserar på det land som begäran kommer från.

![api-glömde-countries](../../assets/tools/observation-for-adobe-commerce/api-forgot-countries.jpg)

## [!UICONTROL API - forgot password, create account by Countries and IP address]

The **[!UICONTROL API - forgot password, create account by Countries and IP address]** visas antalet konton som skapats och begäranden om att återställa ett glömt lösenord under en vald tidsram. Det är även lättare att visa IP-adressen, URL-adressen som används och ursprungslandet för begäran. Den här bildrutan fokuserar på antalet IP-adresser.

![api-Hide-countries-ip](../../assets/tools/observation-for-adobe-commerce/api-forgot-countries-ip.png)

## [!UICONTROL Guest cart activities by IP]

The **[!UICONTROL Guest cart activities by IP]** bildrutan visar gästvagnsaktiviteter per IP under en vald tidsram.

![gästvagn-ip](../../assets/tools/observation-for-adobe-commerce/guest-cart-ip.png)

## [!UICONTROL Guest cart activities by Countries]

The **[!UICONTROL Guest cart activities by Countries]** bildrutan visar gästvagnsaktiviteter per land under en vald tidsram.

![gästvagn-land](../../assets/tools/observation-for-adobe-commerce/guest-cart-country.png)
