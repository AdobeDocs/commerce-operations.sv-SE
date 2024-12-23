---
source-git-commit: 00b8e1bb5ee259763ddb2c52065cee2af98641e0
workflow-type: tm+mt
source-wordcount: '1154'
ht-degree: 0%

---
# Oktober 2024 Adobe Commerce 2.4.7 - beta - i korthet

## Högdagrar

Den här versionen av Adobe Commerce innehåller flera viktiga säkerhetskorrigeringar och plattformsförbättringar.

### Säkerhet

Följande säkerhetsförbättringar i den här versionen förbättrar efterlevnaden av de senaste säkerhetsrutinerna:

>[!NOTE]
>
>Den senaste informationen om säkerhetsfelkorrigeringarna finns i [Adobe säkerhetsbulletin APSB24-73](https://helpx.adobe.com/security/products/magento/apsb24-73.html).

<table style="table-layout:auto">
    <tbody>
        <tr>
            <td><strong>Inställningar</strong></td>
            <td>Den här versionen innehåller följande förbättringar av säkerhetsinställningarna:
              <ul>
                <li><strong>Rotation av krypteringsnyckel</strong>: Nu finns ett nytt CLI-kommando tillgängligt för att ändra krypteringsnyckeln. Mer information finns i artikeln <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/troubleshooting-encryption-key-rotation-cve-2024-34102">Troubleshooting Encryption Key Rotation (Felsökning av krypteringsnyckelrotation): CVE-2024-34102</a> i kunskapsbasen.<!-- AC-12589 --></li>
                <li><strong>Inställningar för engångslösenord </strong>: Den här uppdateringen krävs för att åtgärda ett fel som uppstod vid en <a href="https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/highlights/#new-system-configuration-validation-for-two-factor-authentication-otp_window-value">bakåtkompatibel ändring</a> i 2.4.7. Beskrivningen av fältet <strong>[!UICONTROL OTP Window]</strong> ger nu en korrekt förklaring av inställningen och standardvärdet har ändrats från <code>1</code> till <code>29</code>.<!-- AC-11762 --></li>
              </ul>
            </td>
        </tr>
    </tbody>
</table>

### Plattform

Följande plattformsuppgraderingar för den här versionen säkerställer att Adobe Commerce förblir en stabil och tillförlitlig plattform som är redo att uppfylla kraven i moderna e-handelsmiljöer:

<table style="table-layout:auto">
    <tbody>
        <tr>
            <td><strong>Databas</strong></td>
            <td>I enlighet med vår <a href="/help/release/lifecycle-policy.md">supportpolicy</a> är Adobe Commerce nu kompatibelt med följande LTS-versioner (long-term support) av följande databastekniker:
              <ul>
                <li><strong>MariaDB 11.4 LTS</strong> <em>_(stöds till 2029)_</em>: Den tidigare versionen (MariaDB 10.6) avslutas 2026, vilket gör den här uppgraderingen nödvändig för att upprätthålla systemintegritet och prestanda. MariaDB 10.6 stöds fortfarande, men Adobe rekommenderar uppgradering till MariaDB 11.4 vid uppgradering till Adobe Commerce 2.4.8.</li>
                <li><strong>MySQL 8.4 LTS</strong> <em>_(stöds till 2032)_</em>: Den tidigare versionen (MySQL 8.0) avslutas 2026, vilket gör den här uppgraderingen nödvändig för att upprätthålla systemintegritet och prestanda. MySQL 8.0 stöds fortfarande, men Adobe rekommenderar uppgradering till MySQL 8.4 vid uppgradering till Adobe Commerce 2.4.8</li>
              </ul>
            </td>
        </tr>
        <tr>
            <td><strong>PHP</strong></td>
            <td>Den här versionen innehåller följande PHP-förbättringar:
            <ul>
              <li><strong>PHP 8.1</strong>: Den här versionen tar bort PHP 8.1-kompatibilitet för Adobe Commerce 2.4.8. Du måste uppgradera till PHP 8.3 innan du uppgraderar till Adobe Commerce 2.4.8.</li>
              <li><strong>PHP 8.2</strong>: En av de signifikanta ändringarna i PHP 8.2 är borttagningen av null-parametrar till interna funktionsparametrar som inte kan vara null. Den här versionen åtgärdar inaktuella PHP 8.1-funktioner i kärnplattformskomponenter och säkerställer kompatibilitet med PHP 8.2.</li>
              <li><strong>PHPUnit 10</strong>: Den här versionen åtgärdar flera kritiska problem, förbättrar kompatibiliteten och ser till att Adobe Commerce testramverk följer de senaste branschstandarderna. Adobe rekommenderar att alla Commerce Marketplace-leverantörer och -kunder med anpassningar kontrollerar att deras enhets- och integreringstester körs på PHPUnit 10 i stället för 9.</li>
            </ul>
            </td>
        </tr>
        <tr>
            <td><strong>Komponenter</strong></td>
            <td>Följande <a href="/help/release/packages/adobe-commerce.md">komponenter och beroenden</a> från tredje part uppdaterades till de senaste stabila versionerna för att förbättra plattformens stabilitet och prestanda:
              <ul>
                <li>jquery/validate 1.20.x</li>
                <li>moment.js 2.30.1</li>
                <li>monolog/monolog 3.x</li>
                <li>monolog/Require.js 2.3.7</li>
                <li>TinyMCE 7.x</li>
                <li>wikimedia/less.php 5.x</li>
              </ul>
            </td>
        </tr>
        <tr>
            <td><strong>Sök</strong></td>
            <td>Adobe Commerce är nu optimerat för OpenSearch 2.x och är inte längre kompatibelt med Elasticsearch. Alla moduler och klasser i Elasticsearch 7 och 8 är nu föråldrade i kodbasen. Adobe rekommenderar starkt att man går över till OpenSearch för både lokala installationer och molninfrastrukturer för att säkerställa fortsatt support och kompatibilitet. Se <a href="/help/upgrade/prepare/opensearch-migration.md">Migrera till OpenSearch</a>.
              <ul>
                <li>Alternativen Elasticsearch 7 och Elasticsearch 8 är nu märkta som"(Borttagen)" i Admin-konfigurationen.</li>
                <li>När en användare väljer Elasticsearch som sökmotor i Admin-konfigurationen visas ett meddelande i Commerce om att <em>"Det här sökmotoralternativet stöds inte längre av Adobe. Vi rekommenderar att du använder OpenSearch som sökmotor i stället.</em></li>
              </ul>
            </td>
        </tr>
    </tbody>
</table>

### Prestanda

Den här versionen innehåller följande prestandaförbättringar:

<table style="table-layout:auto">
    <tbody>
        <tr>
            <td><strong>Indexerare</strong></td>
            <td>Standardläget <a href="/help/implementation-playbook/best-practices/maintenance/indexer-configuration.md#set-indexers-to-update-on-schedule">för indexering</a> för alla indexerare är nu [!UICONTROL **Update by Schedule**] när du installerar en ny version av Adobe Commerce eller uppgraderar från en tidigare version. Den nya standardinställningen säkerställer att indexerarna är i den rekommenderade konfigurationen, vilket förbättrar systemets prestanda och minskar eventuella problem.</td>
        </tr>
    </tbody>
</table>

### Kvalitet

Den här versionen innehåller följande kvalitetsförbättringar:

<table style="table-layout:auto">
    <tbody>
        <tr>
           <td><strong>Lager</strong></td>
           <td>Systemet fungerar nu utan det tidigare dolda beroendet från Catalog som introducerades av InventoryIndexer, vilket säkerställer att produktskapandet, växlingen av visningsläge, ändringen av Stock-status och andra relaterade funktioner fungerar som förväntat. Tidigare orsakade det här dolda beroendet inkonsekvenser eftersom olika enheter synkroniserades och indexeraren använde olika enheter.</td>
        </tr>
        <tr>
            <td><strong>Beställningar</strong></td>
            <td>För att minimera förvirring har knappetiketten [!UICONTROL **Submit Comment**] ändrats till [!UICONTROL **Update**] på sidan <a href="https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/order-management/orders/order-processing#notes-for-this-order">ordningsdetaljer</a>.</td>
        </tr>
    </tbody>
</table>

### GraphQL

Den här versionen innehåller följande GraphQL-förbättringar:

<table style="table-layout:auto">
    <tbody>
        <tr>
           <td><strong>Allmänna förbättringar</strong></td>
           <td>Den här versionen innehåller följande allmänna förbättringar av GraphQL API:
             <ul>
               <li><!--LYNX-401--><strong>StoreConfig</strong>: Fälten <code>grouped_product_image</code> och <code>configurable_product_image</code> har lagts till i typen <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-StoreConfig"><code>StoreConfig</code></a>.</li>
              <li><!--LYNX-387--><strong>CartItemPrices</strong>: Följande nya fält har lagts till i typen <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CartItemPrices"><code>CartItemPrices</code></a> för att ge stöd för exakta priser för visning och rabattberäkningar:
                <ul>
                  <li><code>original_item_price</code></li>
                  <li><code>original_row_total</code></li>
                  <li><code>row_total_including_catalog_discounts_only</code></li>
                </ul>
              </li>
              <li><!--LYNX-451--><strong>CartPrices</strong>: Fältet <code>grand_total_excluding_tax</code> har lagts till i typen <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CartPrices"><code>CartPrices</code></a>, vilket ger tydliga skattepliktiga priser.</li>
              <li><!--LYNX-542--><strong>updateCartItems-mutation</strong>: <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#mutation-updateCartItems"><code>updateCartItems</code></a>-mutationen har uppdaterats för att returnera lyckade svar med felinformation i stället för undantag. Förbättrad felmappning för att göra användarmeddelanden tydligare.</li>
              <li><!--LYNX-522--><strong>recaptchaV3Config-fråga</strong>: Ett <code>theme</code>-fält introducerades i <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#query-recaptchaV3Config"><code>recaptchaV3Config</code></a>-frågan. I det här fältet kan du ange namnet på temat som ska användas för att återge reCaptcha.</li>
              <li><!--LYNX-540--><strong>ProductInterface</strong>: Ett <code>quantity</code>-fält introducerades i <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-ProductInterface"><code>ProductInterface</code></a> för att ge information om lagernivån. Det visar tillgängligt lager eller null baserat på administratörsinställningarna.</li>
               <li><!--LYNX-460--><strong>Paketprodukter</strong>: Korrigerad prissättning för paketprodukter, vilket ger korrekt pris- och valutainformation.</li>
               <li><!--LYNX-547--><strong>Kvantitet</strong>: Förfinat meddelande för otillräckligt och otillgängligt antal meddelanden.</li>
               <li><!--LYNX-541--><strong>InsufficientStockError type</strong>: En ny <code>InsufficientStockError</code>-typ har lagts till för att hantera fall där det inte finns tillräckligt med lagringsnivåer. Schemat har anpassats för att stödja nya feltyper och förbättrar felrapporteringsfunktionerna.</li>
               <li><!--LYNX-476--><strong>Lagerbelopp</strong>: Utökat felmeddelande om att inkludera tillgängliga lagerbelopp. Ger användarna tydligare insikter om lagernivåer under orderuppdateringar.</li>
               <li><!--LYNX-377--><strong>Begärd kvantitet</strong>: <code>not_available_message</code> har lagts till i <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CartItemInterface"><code>CartItemInterface</code></a>.</li>
             </ul>
           </td>
        </tr>
        <tr>
           <td><strong>Kundhantering</strong></td>
           <td>Den här versionen innehåller följande förbättringar av kundhanteringen:
             <ul>
               <li><!--LYNX-391--><strong>generateCustomerToken-mutation</strong>: Förfinad felhantering i mutationen <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#mutation-generateCustomerToken"><code>generateCustomerToken</code></a> för att tillhandahålla specifika meddelanden för obekräftade e-postmeddelanden. Stöder bättre användarvägledning och fellösning.</li>
               <li><!--LYNX-390--><strong>resendConfirmationEmail-mutation</strong>: En ny <code>resendConfirmationEmail</code>-mutation har lagts till för att skicka om e-postbekräftelser.</li>
             </ul>
           </td>
        </tr>
        <tr>
           <td><strong>Orderhantering</strong></td>
           <td>Den här versionen innehåller följande förbättringar av användarorderhanteringen:
             <ul>
              <li><!--LYNX-470--><strong>Datum för första beställning</strong>: Ett nytt <code>date_of_first_order</code>-fält har lagts till i typen <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CustomerOrders"><code>CustomerOrders</code></a>.</li>
              <li><!--LYNX-468--><strong>OrderAddress</strong>: Utökade typen <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-OrderAddress"><code>OrderAddress</code></a> så att den inkluderade anpassade attribut, vilket förbättrar synligheten för orderdetaljer. Stöder visning av ytterligare information på orderbekräftelsesidor.</li>
              <li><!--LYNX-458--><strong>gästOrder- och gästordningsByToken-frågor</strong>: <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#query-guestOrder"><code>guestOrder</code></a>- och <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#query-guestOrderByToken"><code>guestOrderByToken</code></a>-frågorna har uppdaterats för att inkludera anpassade adressattribut, vilket ger fullständig adressinformation för nya konton.</li>
              <li><!--LYNX-450--><strong>CustomerOrder-typ</strong>: <code>is_virtual</code>-fältet har lagts till i <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CustomerOrder"><code>CustomerOrder</code></a>-typen, vilket stöder identifiering av virtuell produkt. Förbättrar orderhanteringen genom att skilja mellan virtuella och fysiska produkter.</li>
              <li><!--LYNX-449--><strong>orderItemPrices</strong>: En <code>OrderItemPrices</code>-typ som liknar <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CartItemPrices"><code>CartItemPrices</code></a> till <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-OrderItemInterface"><code>OrderItemInterface</code></a> har lagts till med flera nya prisfält.</li>
              <li><!--LYNX-448--><strong>Sammanfoga gästorder</strong>: Förbättrad API-funktion för att sammanfoga gästorder med kundkonton baserat på e-postmatchning. Effektiviserar orderhanteringen för återkommande kunder.</li>
              <li><!-- LYNX-523: --><strong>available_actions-fält</strong>: Utökade <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CustomerOrder"><code>CustomerOrder</code></a>-typen så att ett <code>available_actions</code>-fält inkluderades för bättre orderhantering. Fältet "available_actions" mappas till en uppräkning som visar möjliga åtgärder som kan utföras i ordningen.</li>
              <li><!-- LYNX-524 --><strong>CustomerOrder-typ</strong>: <code>customer_info</code>-fältet har lagts till i typen <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CustomerOrder"><code>CustomerOrder</code></a>. Det här fältet kräver och <code>OrderCustomerInfo</code>, som definierar information om kundnamnet.</li>
              <li><!--LYNX-519--><strong>Felkoder för orderannullering</strong>: Detaljerade felkoder har lagts till för typen <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CancelOrderOutput"><code>CancelOrderOutput</code></a>. Förbättrad felhantering och användarfeedback för orderannulleringsprocesserna.</li>
              <li><!--LYNX-515--><strong>Aktiverade gästanvändare för att skapa returer för order</strong>: mutationen <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#mutation-requestReturn"><code>requestReturn</code></a> har justerats för att stödja gästorderreturer.</li>
              <li><!--LYNX-505--><strong>confirmCancelOrder-mutation</strong>: En ny <code>confirmCancelOrder</code>-mutation har lagts till för att underlätta orderannullering för gästanvändare.</li>
             </ul>
           </td>
        </tr>
    </tbody>
</table>
