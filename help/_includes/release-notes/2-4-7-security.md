---
source-git-commit: 10a6329502bc63ec06bac0652301770bd8e2935a
workflow-type: tm+mt
source-wordcount: '701'
ht-degree: 0%

---
# 2.4.7 Säkerhetsförbättringar

Inga bekräftade attacker relaterade till dessa problem har inträffat hittills. Vissa säkerhetsluckor kan dock utnyttjas för att få tillgång till kundinformation eller ta över administratörssessioner. De flesta av dessa problem kräver att en angripare först får åtkomst till administratören. Därför påminner vi dig om att vidta alla nödvändiga åtgärder för att skydda din administratör, inklusive, men inte begränsat till, följande:

* IP-tillåtelselistning
* [Tvåfaktorsautentisering](https://developer.adobe.com/commerce/testing/functional-testing-framework/two-factor-authentication/)
* Användning av ett VPN
* Användning av en unik plats i stället för `/admin`
* Bra lösenordshygien

Säkerhetsförbättringar för den här versionen förbättrar efterlevnaden av de senaste säkerhetsstandarderna.

* **Ändringar av beteendet för icke genererade cachenycklar**:

   * Icke genererade cachenycklar för block innehåller nu prefix som skiljer sig från prefix för nycklar som genereras automatiskt. (Icke-genererade cachenycklar är nycklar som ställs in via malldirektivets syntax eller `setCacheKey` eller `setData` metoder.)
   * Icke genererade cachenycklar för block får nu endast innehålla bokstäver, siffror, bindestreck (-) och understreck (_).  <!-- AC-9831 -->

* **Begränsningar för antalet autogenererade kupongkoder**. Commerce begränsar nu antalet kupongkoder som genereras automatiskt. Standardmaxvärdet är 250 000. Handlare kan använda nya **[!UICONTROL Code Quantity Limit]** konfigurationsalternativ (**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Promotions]**) för att förhindra att systemet överbelastas med många kuponger. <!-- AC-8753 -->

* **Optimering av standardprocessen för att skapa Admin URL**. Genereringen av den förvalda admin-URL:en är optimerad för ökad slumpmässighet, vilket gör att genererade URL:er blir mindre förutsägbara. <!-- AC-9028 -->

* **Stöd för extra resursintegritet (SRI)** uppfyller PCI 4.0-kraven för verifiering av skriptintegritet på betalningssidor. Stöd för SRI (Subresource Integrity) ger integritetshash för alla JavaScript-resurser i det lokala filsystemet. Standardfunktionen för SRI implementeras bara på betalningssidorna för områdena Admin och storefront. Handlare kan dock utöka standardkonfigurationen till andra sidor. Se [Underresursintegritet](https://developer.adobe.com/commerce/php/development/security/subresource-integrity/) i _Commerce PHP Developer Guide_.<!--AC-1153-->

* **Ändringar i CSP (Content Security Policy)**—Konfigurationsuppdateringar och förbättringar av Adobe Commerce Content Security Policies (CSP) som uppfyller PCI 4.0-kraven. Mer information finns i [Skyddsprofiler för innehåll](https://developer.adobe.com/commerce/php/development/security/content-security-policies/) i _Commerce PHP Developer Guide_. <!--AC-11513-->

   * Standardkonfigurationen för CSP för betalningssidor för Commerce Admin och butiksområden är nu `restrict` läge. För alla andra sidor är standardkonfigurationen `report-only` läge.  I versioner före 2.4.7 konfigurerades CSP i `report-only` läge för alla sidor.

   * En nonce-provider har lagts till för att tillåta körning av infogade skript i en CSP. Enonce-providern gör det lättare att skapa unika nonce-strängar för varje begäran. Strängarna kopplas sedan till CSP-huvudet.

   * Lagt till alternativ för att konfigurera anpassade URI:er för att rapportera CSP-fel för sidan Skapa order i Admin och sidan Checka ut i butiken. Du kan lägga till konfigurationen från administratören eller genom att lägga till URI:n i dialogrutan `config.xml` -fil.

     >[!NOTE]
     >
     >Uppdaterar CSP-konfigurationen till `restrict` Läget kan blockera befintliga textbundna skript på betalningssidor i Admin och storefront, vilket orsakar följande webbläsarfel när en sida läses in: `Refused to execute inline script because it violates the following Content Security Policy directive: "script-src`. Åtgärda dessa fel genom att uppdatera vitlistskonfigurationen så att nödvändiga skript tillåts. Se [Felsökning](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#troubleshooting) i _Commerce PHP Developer Guide_.

* En ny cachekonfigurationsinställning för helsida kan minska riskerna med HTTP `{BASE-URL}/page_cache/block/esi` slutpunkt. Den här slutpunkten stöder obegränsade, dynamiskt inlästa innehållsfragment från Commerce layouthandtag och blockstrukturer. Den nya **[!UICONTROL Handles params size]** konfigurationsinställning anger värdet för den här slutpunktens `handles` -parameter, som avgör det högsta tillåtna antalet handtag per API. Egenskapens standardvärde är 100. Handlare kan ändra det här värdet från administratören (**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Handles params size]**). Se [Konfigurera Commerce-programmet så att det använder engelska](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cache/configure-varnish-commerce.html). <!-- AC-9113 -->

* **Inbyggd hastighetsbegränsning för betalningsinformation som överförs via REST och GraphQL API:er**. Merchants kan nu [konfigurera hastighetsbegränsning](https://experienceleague.adobe.com/en/docs/commerce-admin/config/sales/sales#rate-limiting) för betalningsinformation som skickas med REST och GraphQL. Detta extra skydd stöder förebyggande av kardningsattacker och kan minska antalet kardningsattacker som testar många kreditkortsnummer samtidigt. Detta är en ändring av standardbeteendet för en befintlig REST-slutpunkt. Se [Hastighetsbegränsning](https://developer.adobe.com/commerce/webapi/get-started/rate-limiting/).

* Standardbeteendet för [isEmailAvailable](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/is-email-available/) GraphQL query and the ([V1/customers/isEmailAvailable](https://adobe-commerce.redoc.ly/2.4.7-admin/tag/customersisEmailAvailable/#operation/PostV1CustomersIsEmailAvailable)) REST-slutpunkten har ändrats. API:erna returneras nu alltid som standard `true`. Handlare kan aktivera det ursprungliga beteendet genom att ställa in *[Aktivera utcheckning av gäster](https://experienceleague.adobe.com/en/docs/commerce-admin/config/sales/checkout)* i Admin to `yes`, men då kan oautentiserade användare få tillgång till kundinformation.
