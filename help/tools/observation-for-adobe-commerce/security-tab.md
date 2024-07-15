---
title: Fliken [!UICONTROL Security]
description: Läs mer om fliken [!UICONTROL Security] i  [!DNL Observation for Adobe Commerce].
exl-id: b567e4a4-534e-4151-b6f6-bf59b1bd4028
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# Fliken [!UICONTROL Security]

Fliken **[!UICONTROL Security]** förklarar säkerhetsproblem och isolerar deras potentiella orsaker. Dessutom beskrivs bildrutorna på fliken.

## [!UICONTROL API calls by IP, details by URL]

Bildrutan **[!UICONTROL API calls by IP, details by URL]** visar ett antal API-anrop per IP över en vald tidsram. I den här bildrutan visas IP-adressen och API-URL:en som den IP-adressen användes till.

![API-anrop via IP](../../assets/tools/observation-for-adobe-commerce/calls-by-ip.jpg)

## [!UICONTROL Forgot Password]

Åtkomstbildrutan **[!UICONTROL Forgot Password]** visar antalet försök till glömt lösenord under en vald tidsram. Hög aktivitet mot en IP-adress kan vara en attack på webbplatsen.

![Lösenordet har glömts](../../assets/tools/observation-for-adobe-commerce/forgot-password.jpg)

## [!UICONTROL Create Account access]

Bildrutan **[!UICONTROL Create Account access]** visar antalet nya kontoaktiviteter under en vald tidsram. Hög aktivitet från en enda IP-adress kan tyda på en attack.

![create-account-access](../../assets/tools/observation-for-adobe-commerce/create-account-access.png)

## [!UICONTROL POST activities]

Bildrutan **[!UICONTROL POST activities]** visar `POST`-aktiviteterna för webbplatsen, som fasetteras på `client_ip` från [!DNL Fastly]-loggarna. Den visar också den URL som är tillgänglig för IP-adressen.

![POST-aktiviteter](../../assets/tools/observation-for-adobe-commerce/POST-activities.jpg)

## [!UICONTROL POST activities summary table]

Bildrutan **[!UICONTROL POST activities summary table]** visar de summerade `POST` aktiviteterna för webbplatsen, som fasetteras på `client_ip` från [!DNL Fastly] loggar. Den visar även antalet för den URL som är tillgänglig för IP-adressen. Antalet gäller för den valda tidsramen.

![POST-activity-summary](../../assets/tools/observation-for-adobe-commerce/POST-activities-summary.jpg)

## [!UICONTROL POST activities details table]

Bildrutan **[!UICONTROL POST activities details table]** visar `POST`-aktiviteter för webbplatsen från [!DNL Fastly]-loggarna. Den visar även all information från [!DNL Fastly]-loggen för dessa begäranden. Den är begränsad till de senaste 2000 ansökningarna.
![POST-activity-details](../../assets/tools/observation-for-adobe-commerce/POST-activities-details.jpg)

## [!UICONTROL Guest Carts activities]

Bildrutan **[!UICONTROL Guest Carts activities]** visar antalet gästvagnsaktiviteter under en vald tidsram, uppdelat efter IP-adress och URL. Gästvagnar kan användas i en kardinfarkt. I den här bildrutan visas det totala antalet begäranden där gästvagnens URL:er är tillgängliga.

![gästkartor-aktiviteter](../../assets/tools/observation-for-adobe-commerce/guest-carts-activities.jpg)

## [!UICONTROL API – forgot password, create account by Countries]

Bildrutan **[!UICONTROL API – forgot password, create account by Countries]** visar antalet konton som skapats och begäranden om att återställa ett glömt lösenord under en vald tidsram. Det är även lättare att visa ursprungslandet för begäran. Denna ram fokuserar på det land som begäran kommer från.

![api-glömde-countries](../../assets/tools/observation-for-adobe-commerce/api-forgot-countries.jpg)

## [!UICONTROL API - forgot password, create account by Countries and IP address]

Bildrutan **[!UICONTROL API - forgot password, create account by Countries and IP address]** visar antalet konton som skapats och begäranden om att återställa ett glömt lösenord under en vald tidsram. Det är även lättare att visa IP-adressen, URL-adressen som används och ursprungslandet för begäran. Den här bildrutan fokuserar på antalet IP-adresser.

![api-Hide-countries-ip](../../assets/tools/observation-for-adobe-commerce/api-forgot-countries-ip.png)

## [!UICONTROL Guest cart activities by IP]

Bildrutan **[!UICONTROL Guest cart activities by IP]** visar gästvagnsaktiviteter per IP under en vald tidsram.

![gästvagn-ip](../../assets/tools/observation-for-adobe-commerce/guest-cart-ip.png)

## [!UICONTROL Guest cart activities by Countries]

Bildrutan **[!UICONTROL Guest cart activities by Countries]** visar gästvagnsaktiviteter per land under en vald tidsram.

![gästvagn-land](../../assets/tools/observation-for-adobe-commerce/guest-cart-country.png)
