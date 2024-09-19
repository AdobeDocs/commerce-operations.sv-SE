---
title: Åtkomst till [!DNL Site-Wide Analysis Tool]
description: Lär dig hur du kommer åt  [!DNL Site-Wide Analysis Tool]
exl-id: b691fb2c-8d66-4cf9-8612-bbcb4df5b95f
source-git-commit: 18416ae29cee182a5d088069065d73814fc7d860
workflow-type: tm+mt
source-wordcount: '529'
ht-degree: 0%

---

# Åtkomst till [!DNL Site-Wide Analysis Tool]

Det finns två sätt att komma åt [!DNL Site-Wide Analysis Tool Dashboard].

Du kan komma åt [!DNL dashboard] antingen från [[!DNL Site-Wide Analysis Tool] webbplatsen](https://supportinsights.adobe.com/commerce) direkt **(endast för Adobe Commerce i molninfrastrukturen)** och logga in med din Adobe ID, eller via [!DNL dashboard] från din butiks [!DNL Admin Panel].

Tjänsten [!DNL Site-Wide Analysis Tool] är tillgänglig i [produktionsläge](https://docs.magento.com/user-guide/magento/installation-modes.html) för [!DNL Admin]-användare med behörighet att komma åt användarens [rollresurser](https://docs.magento.com/user-guide/system/permissions-user-roles.html).

>[!NOTE]
>
>Från och med den 23 april 2024 har [!DNL Site-Wide Analysis Tool] tagits bort och är inte längre tillgänglig för Adobe Commerce lokala kunder.


![Instrumentpanel för webbplatsövergripande analys](../../assets/tools/site-wide-analysis-tool-dashboard.png)
*[!DNL Site-Wide Analysis Tool]Kontrollpanel*

## Alternativ 1: Logga in på din [!DNL Site-Wide Analysis Tool Dashboard] direkt från domänen [!DNL Site-Wide Analysis Tool] (endast för Adobe Commerce i molninfrastrukturen)

**[!DNL Adobe ID]krävs** för att få åtkomst till ett [!DNL Commerce]-konto.
Om du redan har ett [!DNL Commerce]-konto, men inte har något [!DNL Adobe ID], kan du skapa ett under inloggningsprocessen.

1. Gå till [https://supportinsights.adobe.com/commerce](https://supportinsights.adobe.com/commerce).

1. Klicka på knappen **[!UICONTROL Sign in with Adobe ID]** och följ anvisningarna.

   ![Instrumentpanel för webbplatsövergripande analys](../../assets/tools/adobe-id-login.jpg)
   *[!DNL Adobe ID]inloggningsskärm*

1. Godkänn villkoren.

1. **<u>Obs!</u>:** Ditt konto bör ha behörighet till **[!DNL Support Permissions]** för att få åtkomst till [!DNL Site-Wide Analysis Tool Dashboard].
Mer information finns i [Dela ett [!DNL Commerce] konto](https://experienceleague.adobe.com/docs/commerce-admin/start/commerce-account/commerce-account-share.html) i användarhandboken.

## Alternativ 2: Loggar in på [!DNL Site-Wide Analysis Tool Dashboard] från butikens [!DNL Admin Panel]

### Steg 1: Verifiera behörigheter

Kontrollera att användarkontot [!DNL Admin] har behörighet att komma åt [!DNL Site-Wide Analysis Tool] via sin [tilldelade användarroll](https://docs.magento.com/user-guide/system/permissions-user-roles.html).

>[!IMPORTANT]
>
>Rollresursen [!DNL Site-Wide Analysis Tool] (behörighet) är **inte** automatiskt tilldelad. Det MÅSTE aktiveras för användarrollen och den roll som tilldelas individuellt till varje användarkonto i [!UICONTROL Admin].

Gör följande för den anpassade rollen som behöver [!DNL Site-Wide Analysis Tool]-åtkomst:

1. Välj rollresursen **[!UICONTROL Reports]** > *[!UICONTROL System Insights]* > **[!UICONTROL Site-Wide Analysis Tool]**.

   ![Instrumentpanel för webbplatsövergripande analys](../../assets/tools/swat-role-access.png)
   *[!DNL Site-Wide Analysis Tool]behörighet har valts för rollen*

1. Klicka på **[!UICONTROL Save Role]**.

1. Meddela alla användare som har tilldelats den rollen att logga ut från [!DNL Admin] och logga in igen.

>[!NOTE]
>
>Om du har verifierat att användarkontot har behörighet att komma åt [!DNL Site-Wide Analysis Tool] och användaren får ett 403-fel när han/hon försöker komma åt verktyget från [!DNL Admin], kan HTTP-åtkomstkontrollen vara aktiverad för din instans av Adobe Commerce i molninfrastrukturen. Instrumentpanelen [!DNL Site-Wide Analysis Tool] stöds INTE om du har aktiverat HTTP-autentisering. Mer information om hur du löser det här problemet finns i [supportartikeln](https://support.magento.com/hc/en-us/articles/360057400172-403-errors-when-accessing-Site-Wide-Analysis-Tool-on-Magento?_ga=2.168901729.117144580.1649172612-1623400270.1640858671).

### Steg 2: Åtkomst [!DNL Site-Wide Analysis Tool]

1. Gå till **[!UICONTROL Reports]** > *[!UICONTROL System Insights]* > **[!UICONTROL Site-Wide Analysis Tool]** på sidofältet *[!UICONTROL Admin]*.

   ![Instrumentpanel för webbplatsövergripande analys](../../assets/tools/ac-admin-panel-marked.jpg)
   *[!DNL Site-Wide Analysis Tool]-plats i [!DNL Admin Panel] i Adobe Commerce*

1. Läs *användningsvillkoren* för [!DNL Site-Wide Analysis Tool] och klicka på **[!UICONTROL Accept]** för att fortsätta.

   Varje användare måste godkänna användningsvillkoren för sessionen. Det här steget upprepas för varje inloggad session.


1. Klicka på den flik som du vill visa högst upp på kontrollpanelen.

   ![Instrumentpanel för webbplatsövergripande analys](../../assets/tools/swat-information-tab.png)
   *[!DNL Site-Wide Analysis Tool]information*

## Generera rapporter från [!DNL Site-Wide Analysis Tool Dashboard]

1. Klicka på **[!UICONTROL Generate Report]** i det övre högra hörnet av instrumentpanelen.

1. Markera kryssrutan för varje **[!UICONTROL Type]**- och **[!UICONTROL Priority]**-inställning som du vill inkludera i rapporten.

1. Klicka på **[!UICONTROL Generate Report]**.

   ![Instrumentpanel för webbplatsövergripande analys](../../assets/tools/swat-report-settings.png)
   *Rapportinställningar*

| TABB | BESKRIVNING |
| --- | --- |
| Kontrollpanel | Visar systemets hälsa med aktuella meddelanden och rekommendationer efter prioritet. |
| Information | Ger kundkontaktinformation och en sammanfattning av aktuella biljetter med detaljerad information om varje installerad Adobe Commerce-produkt. |
| Recommendations | Visar rekommendationer baserade på bästa praxis för att hantera problem som upptäcks på din plats. |
| Undantag | Visar en lista över fel som genererats av programmet och som orsakas av onormala förhållanden utan felhanterare. |
| Tillägg | Visar alla tillägg från tredje part och tredjepartsbibliotek. |

>[!NOTE]
>
>När du har tillämpat en rekommendation kan det ta några dagar innan den har uppdaterats i [!DNL Site-Wide Analysis Tool Dashboard] eller den genererade rapporten.
