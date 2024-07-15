---
title: Självvärdande säkerhetskoncept för Adobe Commerce
description: Lär dig mer om självvärdande säkerhetsidéer och -koncept och de bästa metoderna att tänka på. Lär dig begrepp som skrivskyddade filsystem, inläsning av skadlig kod och många andra ämnen som du bör tänka på när du är värd för Adobe-handel.
landing-page-description: Lär dig några säkerhetsbegrepp och saker att tänka på när du är värd för Adobe Commerce på egen hand.
short-description: Lär dig strategier och säkerhetskoncept för att själv vara värd för Adobe Commerce.
kt: 11420
doc-type: tutorial
audience: all
last-substantial-update: 2023-04-13T00:00:00Z
exl-id: f76a8906-af31-4a61-be68-f5dad87161e2
feature: Install, Security
source-git-commit: 823498f041a6d12cfdedd6757499d62ac2aced3d
workflow-type: tm+mt
source-wordcount: '1546'
ht-degree: 0%

---

# Säkerhetskoncept

Säkerhet bör alltid vara en stark hänsyn till allt som rör ett e-handelsprojekt. Utan en stark säkerhetsställning är det yta som kan attackeras exponentiellt större. De koncept och idéer som presenteras innehåller metoder som visat sig minska de vanliga sårbarheter som normalt utnyttjas.

Följande koncept finns inte i någon speciell ordning. De är avsedda att ge vissa idéer och koncept att tänka på. Många är kostnadsfria eller kräver minimal installation, konfiguration och efterföljande övervakning. Undersök dessa ämnen utanför den här självstudiekursen för att se till att du har en tillräcklig förståelse för de koncept som presenteras här.

## Skrivskyddat filsystem

Skrivskyddat filsystemskoncept lånades från [Adobe Commerce i molninfrastrukturen](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/getting-started/cloud/1-overview.html){target="_blank"}. Detta tar helt bort ett större område som används av en dålig skådespelare. Många utnyttjar möjligheten att ändra en fil som förväntas finnas i Commerce-programmet för att undvika identifiering. I stället för att skapa en så ändras innehållet i en befintlig fil så att en oväntad åtgärd utförs. Om du skrivskyddar filsystemet minskar den här attackvektorn avsevärt.

## Använd TWO Factor Authentication och lösenordshanterare

Dela aldrig lösenord. Varje administratörsanvändare ska ha ett eget konto med rätt åtkomstkontrollista. Se till att tvåfaktorsidentifiering aldrig inaktiveras eller tas bort. Om du ger administratörsåtkomst till en tredje part måste du se till att lösenordet genereras av en lösenordshanterare och aldrig återanvänds.

## Skannade program

Skadlig programvara hittas oftast från en värdleverantör som försöker specialisera sig på Adobe Commerce. Det här biblioteket med kända skadliga program och explosioner växer ständigt i takt med att nya hot upptäcks, utforskas och diagnostiseras. Fråga om värdtjänstleverantören har en sådan tjänst och om de kan köras automatiskt eller endast på begäran. Det finns också tjänster som du kan prenumerera på och som kan använda sitt eget bibliotek med kända explosioner för att kontinuerligt kontrollera om ditt e-handelsprogram har utnyttjats. Vissa av dessa är endast externa, vissa kan läggas till i infrastrukturen för att ge en intern djup genomsökning av alla mappar, filer och till och med databasen. Det finns några leverantörer med många års erfarenhet på den här arenan, från Sansec.io till Sucuri och förstås MageReport. Vissa är kostnadsfria och andra kostar något. Om du vet att det här är tillgängligt och har ett genomtänkt samtal med din Adobe Commerce-arkitekt och DevOps-teamet säkerställer du att du hittar rätt lösning.

## Site-Wide Analysis Tool for Commerce

[Site-Wide Analysis Tool](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/intro.html){target="_blank"} är ett proaktivt självbetjäningsverktyg och en central lagringsplats med detaljerade systeminsikter och rekommendationer för att säkerställa säkerheten och användbarheten för din Adobe Commerce-installation. Den ger prestandaövervakning, rapporter och råd i realtid dygnet runt alla dagar för att identifiera potentiella problem och bättre synlighet för webbplatsens hälsa, säkerhet och programkonfigurationer. Det minskar upplösningstiden och förbättrar webbplatsens stabilitet och prestanda.

## Aktivera och verifiera inställningar för administratörsåtgärdsloggning

Du hittar detta när du har loggat in på Adobe Commerce-administratören och navigerat till Lager > Konfiguration > Avancerat > Admin > Loggning av administrationsåtgärder. Här finns en lista över händelser som övervakas och spelas in. Det är användbart när man gör kriminalteknisk analys på en utnyttjad webbplats, om misstanken om detta ger tillgång till Commerce-administratören. Denna loggning och rapport kan vara användbara för att se vilka händelser den dåliga skådespelaren har utfört. Om någon administratörsåtgärd för loggning är inaktiverad, vilket är ett tecken på att någon har inaktiverat dem för att täcka över loggningen när vissa åtgärder utförs.

## Basserver för SSH-åtkomst

Det här är svårare att förklara att de flesta ämnen i självstudiekursen om säkerhetsfrågor är svåra att förklara. Grundtanken med detta är att tillhandahålla en server som fungerar som mellanhand för SSH-åtkomst. På så sätt tillåter produktionsservrarna aldrig externa SSH-anslutningar. Du kan skapa den här bastionsservern och använda en lokal IP-mask för att se till att endast angivna servrar tillåts att använda SSH i dem.

## Granska ACL-roller och behörigheter

Varje administratörsanvändare av Adobe Commerce tilldelas en ACL-roll. Den här rollen ska skapas för att bara tillhandahålla den funktionalitet som måste utföra jobbet. ACL-rollerna bör utvärderas ofta för att säkerställa att de inte ger mer behörighet än nödvändigt. Skapa vid behov många ACL-roller med ansvarsområden. Om åtkomst beviljas till en tredje part av någon anledning bör de inaktiveras så snart som möjligt. Fråga dem hur länge de absolut behöver åtkomst och ange ett automatiskt förfallodatum när de skapar sina administratörsanvändare.

## Granska administratörsanvändare och SSH-användare ofta

För att upptäcka oönskade eller obehöriga administratörsanvändare bör administratörsanvändarlistan granskas ofta. En bra tumregel är att kontrollera vem som har SSH och administratörsåtkomst till Adobe Commerce-programmet varje månad. Om nya användare upptäcks inaktiverar du deras konto och följer eventuella företagspolicyer och procedurer för en sådan incident. Det är enklare att återskapa en användares åtkomst än att återställa efter en aktivering.

## Databasrensning

Begränsa åtkomst till produktionsdata. Dessa utsedda teammedlemmar bör ha möjlighet att dra ned på produktionsdatabaser och rensa dem från verkliga data. Om det är ett alternativ att ta bort data kan du korta av de tabeller som används, t.ex. order, citattecken och kunder. Ibland vill du dock ha en fullständig uppsättning data, men värdena kan anonymiseras. Detta gäller vanligtvis i en staging-miljö. Det är också användbart före uppgraderingar. Genom att ha den verkliga datavolymen, men anonymiserat, kan du testa och validera den tid det tar att köra en distribution för att uppgradera ordentligt. Om du har en begränsad uppsättning data kan du underskatta uppgraderingsprocessen och tidsåtgången.

+++Exempel på slumpmässig kundinformation
Här är ett exempel på hur du ändrar ut kundens e-postadress med en slumpmässig sträng och alla för- och efterhandsfält i vissa standardtabeller som Adobe Commerce lagrar data i. **Kom ihåg att kontrollera alla tabeller för att se om det finns känsliga data. Den här listan ingår inte i de tabeller som kan lagra kunddata.**

```SQL
SET FOREIGN_KEY_CHECKS=0;
UPDATE customer_entity SET email = REPLACE(email, SUBSTRING(email, LOCATE('@', email) +1), CONCAT(UUID(), '.com'));
UPDATE email_contact SET email = REPLACE(email, SUBSTRING(email, LOCATE('@', email) +1), CONCAT(UUID(), '.com'));
UPDATE sales_invoice_grid SET customer_email = 'customer@example.com', customer_name  = 'Jack Smith';
UPDATE sales_order SET customer_email = 'customer@example.com', customer_firstname = 'Sally', customer_lastname = 'Smith', remote_ip = '127.0.0.1';
UPDATE sales_order_address SET region = 'Ohio', postcode = '12345-1234', lastname = 'Smith', street = '123 Main street', region_id = 44, city = 'Phoenix', telephone = NULL, firstname = 'Jane', company = NULL;
UPDATE sales_order_grid SET customer_email = 'customer@example.com', shipping_name = 'Jack', billing_name = 'Jack Smith', billing_address = '123 Main Street', shipping_address = '321 Pine Street', customer_name = 'Jane Smith';
UPDATE sales_shipment_grid SET customer_email = 'customer@example.com', customer_name = 'Jane Smith', billing_address = '123 Main street', billing_name = 'Jack Doe', shipping_name = 'Susie Smith';
UPDATE quote SET customer_email = 'customer@example.com', customer_firstname = 'Sally', customer_lastname = 'Jones', customer_dob = NULL, remote_ip = '127.0.0.1';
UPDATE quote_address SET email = 'customer@example.com', firstname = 'Jack', lastname = 'Smith', company = NULL, street = '123 Main st', city = 'AnyCity', region = 'Some State', region_id = 44, postcode = '12345-1234', telephone = NULL;
UPDATE magento_rma SET customer_custom_email = 'customer@example.com' WHERE customer_custom_email IS NOT NULL;
UPDATE customer_address_entity SET firstname = 'Jack', lastname = 'Smith', telephone = '909-555-1212', postcode = NULL,  region = NULL, street = '123 Main street', city = 'Anycity', company = NULL;
UPDATE customer_grid_flat SET name = 'Jane Doe', email = 'customer@example.com', dob = NULL, gender = NULL, taxvat = NULL, shipping_full = '', billing_full = '', billing_firstname = 'Jack', billing_lastname = 'Smith', billing_telephone = NULL, billing_postcode = NULL, billing_country_id = NULL, billing_region = NULL, billing_street = '123 Main street', billing_city = 'Anycity', billing_fax = NULL, billing_vat_id = NULL, billing_company = NULL;
UPDATE sales_creditmemo_grid SET billing_name = 'Sally', billing_address = '123 Main Street', customer_name = 'Jack Smith', customer_email = 'customer@example.com';
    
UPDATE magento_rma_grid SET customer_name = 'Jack Smith';
SET FOREIGN_KEY_CHECKS=1;
```

+++


+++Du kan även korta av tabeller i stället för att försöka anonymisera

```SQL
SET FOREIGN_KEY_CHECKS=0;
TRUNCATE customer_log;  
TRUNCATE customer_visitor;  
TRUNCATE magento_logging_event;
TRUNCATE oauth_consumer;
TRUNCATE oauth_nonce;
TRUNCATE oauth_token;
TRUNCATE password_reset_request_event;
TRUNCATE acknowledgement;
TRUNCATE acknowledgement_report;
TRUNCATE avatax_log;
TRUNCATE avatax_queue;
TRUNCATE cron_schedule;
SET FOREIGN_KEY_CHECKS=1;
```

+++

+++Ta bort information i ett fullständigt exempel
Här är ett exempel på hur du tar bort alla order, offerter, kreditnotor med mera innan du startar programmet eller i en lägre utvecklingsmiljö

```SQL
DELETE FROM `gift_message`;
DELETE FROM `inventory_reservation`;
DELETE FROM `quote`;
DELETE FROM `quote_address`;
DELETE FROM `quote_address_item`;
DELETE FROM `quote_id_mask`;
DELETE FROM `quote_item`;
DELETE FROM `quote_item_option`;
DELETE FROM `quote_payment`;
DELETE FROM `quote_shipping_rate`;
DELETE FROM `reporting_orders`;
DELETE FROM `sales_bestsellers_aggregated_daily`;
DELETE FROM `sales_bestsellers_aggregated_monthly`;
DELETE FROM `sales_bestsellers_aggregated_yearly`;
DELETE FROM `sales_creditmemo`;
DELETE FROM `sales_creditmemo_comment`;
DELETE FROM `sales_creditmemo_grid`;
DELETE FROM `sales_creditmemo_item`;
DELETE FROM `sales_invoice`;
DELETE FROM `sales_invoiced_aggregated`;
DELETE FROM `sales_invoiced_aggregated_order`;
DELETE FROM `sales_invoice_comment`;
DELETE FROM `sales_invoice_grid`;
DELETE FROM `sales_invoice_item`;
DELETE FROM `sales_order`;
DELETE FROM `sales_order_address`;
DELETE FROM `sales_order_aggregated_created`;
DELETE FROM `sales_order_aggregated_updated`;
DELETE FROM `sales_order_grid`;
DELETE FROM `sales_order_item`;
DELETE FROM `sales_order_payment`;
DELETE FROM `sales_order_status_history`;
DELETE FROM `sales_order_tax`;
DELETE FROM `sales_order_tax_item`;
DELETE FROM `sales_payment_transaction`;
DELETE FROM `sales_refunded_aggregated`;
DELETE FROM `sales_refunded_aggregated_order`;
DELETE FROM `sales_shipment`;
DELETE FROM `sales_shipment_comment`;
DELETE FROM `sales_shipment_grid`;
DELETE FROM `sales_shipment_item`;
DELETE FROM `sales_shipment_track`;
DELETE FROM `sales_shipping_aggregated`;
DELETE FROM `sales_shipping_aggregated_order`;
DELETE FROM `tax_order_aggregated_created`;
DELETE FROM `tax_order_aggregated_updated`;
DELETE FROM `magento_rma`;
DELETE FROM `magento_rma_grid`;
DELETE FROM `magento_rma_item_entity`;
DELETE FROM `magento_rma_status_history`;
DELETE FROM `magento_sales_creditmemo_grid_archive`;
DELETE FROM `magento_sales_invoice_grid_archive`;
DELETE FROM `magento_sales_order_grid_archive`;
DELETE FROM `magento_sales_shipment_grid_archive`;
DELETE FROM `sequence_creditmemo_0`;
DELETE FROM `sequence_creditmemo_1`;
DELETE FROM `sequence_creditmemo_2`;
DELETE FROM `sequence_creditmemo_7`;
DELETE FROM `sequence_invoice_0`;
DELETE FROM `sequence_invoice_1`;
DELETE FROM `sequence_invoice_2`;
DELETE FROM `sequence_invoice_7`;
DELETE FROM `sequence_order_0`;
DELETE FROM `sequence_order_1`;
DELETE FROM `sequence_order_2`;
DELETE FROM `sequence_order_7`;
DELETE FROM `sequence_rma_item_0`;
DELETE FROM `sequence_rma_item_1`;
DELETE FROM `sequence_rma_item_2`;
DELETE FROM `sequence_rma_item_7`;
DELETE FROM `sequence_shipment_0`;
DELETE FROM `sequence_shipment_1`;
DELETE FROM `sequence_shipment_2`;
DELETE FROM `sequence_shipment_7`;

## USE THE FOLLOWING WITH CAUTION - CAN CAUSE ISSUES WITH TAX/PAYMENT PROCESSORS IF YOU REUSE ORDER NUMBERS, ETC.

ALTER TABLE sequence_creditmemo_0 AUTO_INCREMENT=1;
ALTER TABLE sequence_creditmemo_1 AUTO_INCREMENT=1;
ALTER TABLE sequence_creditmemo_2 AUTO_INCREMENT=1;
ALTER TABLE sequence_creditmemo_7 AUTO_INCREMENT=1;
ALTER TABLE sequence_invoice_0 AUTO_INCREMENT=1;
ALTER TABLE sequence_invoice_1 AUTO_INCREMENT=1;
ALTER TABLE sequence_invoice_2 AUTO_INCREMENT=1;
ALTER TABLE sequence_invoice_7 AUTO_INCREMENT=1;
ALTER TABLE sequence_order_0 AUTO_INCREMENT=1;
ALTER TABLE sequence_order_1 AUTO_INCREMENT=1;
ALTER TABLE sequence_order_2 AUTO_INCREMENT=1;
ALTER TABLE sequence_order_7 AUTO_INCREMENT=1;
ALTER TABLE sequence_rma_item_0 AUTO_INCREMENT=1;
ALTER TABLE sequence_rma_item_1 AUTO_INCREMENT=1;
ALTER TABLE sequence_rma_item_2 AUTO_INCREMENT=1;
ALTER TABLE sequence_rma_item_7 AUTO_INCREMENT=1;
ALTER TABLE sequence_shipment_0 AUTO_INCREMENT=1;
ALTER TABLE sequence_shipment_1 AUTO_INCREMENT=1;
ALTER TABLE sequence_shipment_2 AUTO_INCREMENT=1;
ALTER TABLE sequence_shipment_7 AUTO_INCREMENT=1;
```

+++

## Använd miljövariabler

[!BADGE Endast Adobe Commerce i molnet]{type=Informative}

Genom att använda miljövariabler blir det lättare att ange vissa värden som kan och bör ändras för varje miljö. Du kanske vill ha olika administratörs-URL:er för varje miljö. Genom att ange det här värdet som en miljövariabel kan du konfigurera det och snabbt referera till det här värdet från molngränssnittet när det behövs.

Du kan läsa mer om det här avsnittet i Experience League [Commerce om miljövariabler för molninfrastruktur](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-intro.html){target="_blank"}

## Skanningsverktyg för sårbarhet i programvara

CI/CD-flödet kan vara ett kraftfullt verktyg som kan automatisera vissa uppgifter. I synnerhet är möjligheten för en utvecklare att implementera kod som kan vara utnyttjbar alltid en verklig möjlighet. Vid granskning av peer-kod fångas vanligtvis sådana objekt upp, men eftersom det är en människa händer det misstag. Automatisk kodskanning minskar risken för oväntade sårbarheter i en nyligen introducerad funktion. Dessa verktyg kan till och med användas för att blockera sammanslagning av kod i den aktiva kodbasen. Det finns många sätt och verktyg för att erbjuda automatiserad kodsäkerhet och kvalitetskontroll. Det kan finnas robusta, anpassade verktyg, men de kräver ständiga uppdateringar och justeringar. Ett alternativ är att använda proaktivt uppdaterade verktyg som synk.io och Amazon kodinspektör.

## Brandvägg för webbaserade program

En Brandvägg för webbaserade program eller en WAF som ofta används när man pratar med DevOps eller en värdtjänstleverantör.

Brandväggar för webbaserade program (WAF) förhindrar att skadlig trafik kommer in på webbplatser och nätverk genom att filtrera trafik mot en uppsättning säkerhetsregler. Trafik som utlöser någon av reglerna blockeras innan den kan skada dina platser eller nätverk.

Adobe Commerce cloud WAF har en WAF-policy med en regeluppsättning som är utformad för att skydda dina Adobe Commerce webbprogram från en mängd olika attacker. Om du väljer ett alternativ för självbetjäning är det ditt ansvar att hitta en WAF och konfigurera reglerna. Vissa värdtjänstleverantörer och WAF-leverantörer har en allmän uppsättning regler som är bra att börja med, men förväntar sig att en del arbete ska få saker att fungera i ditt projekt.

WAF undersöker webb- och administratörstrafik för att identifiera misstänkt aktivitet. Den utvärderar GET- och POST-trafik (HTTP API-anrop) och använder regeluppsättningen för att avgöra vilken trafik som ska blockeras. WAF kan blockera en mängd olika attacker, bland annat SQL-injektionsattacker, serveröverskridande skriptattacker (cross-site scripting), dataexfiltreringsattacker och HTTP-protokollöverträdelser.

Som molnbaserad tjänst kräver WAF ingen maskinvara eller programvara för att kunna installera eller underhålla. Snabb, en befintlig teknikpartner, tillhandahåller programvara och expertis. Deras högpresterande, alltid aktiverade WAF finns i varje cache-nod över Fastlys globala leveransnätverk.

Mer information om WAF på Adobe Commerce i molnet får du av Fastly i [Adobe Commerce Knowledge Base FAQ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/faq/web-application-firewall-waf-powered-by-fastly-the-faq.html){target="_blank"}.

{{$include /help/_includes/hosting-related-links.md}}
