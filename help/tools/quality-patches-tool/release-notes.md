---
title: Versionsinformation
description: Läs mer om vilka korrigeringsfiler som finns för Adobe Commerce och vilka problem de löser.
exl-id: 22262555-f5ea-49ad-98ad-ea8428ef66d5
source-git-commit: 9e71d979e0662770043fd9ca74b9ba8b5a6752f0
workflow-type: tm+mt
source-wordcount: '24552'
ht-degree: 0%

---

# Versionsinformation

[[!DNL Quality Patches Tool]](https://github.com/magento/quality-patches) innehåller enskilda korrigeringsfiler som utvecklats av Adobe och Magento Open Source-communityn. Med den kan du tillämpa, återställa och visa allmän information om alla enskilda korrigeringsfiler som är tillgängliga för den installerade versionen av Adobe Commerce. Du kan använda korrigeringsfiler i Adobe Commerce- och Magento Open Source-projekt oavsett vem som har utvecklat korrigeringsfilen. Du kan till exempel använda en korrigering som utvecklats av communityn på Adobe Commerce-projekt.

>[!INFO]
>
>Se [Tillämpa korrigeringsfiler](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html#apply-individual-patches) för instruktioner om hur du använder korrigeringsfiler i dina Adobe Commerce-projekt. Se [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i programuppdateringshandboken om du vill visa en fullständig lista över släppta korrigeringsfiler.

>[!INFO]
>
>Mer information om [!DNL quality patches] som har skapats av gemenskapen för Magento Open Source finns i [versionsinformationen](https://github.com/magento/quality-patches/blob/master/community-release-notes.md).

## v1.1.58 {#v1-1-58}

* **ACSD-48570** (för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.4.7) - Korrigerar problemet där sidan för återställning av lösenord inte kunde nås genom att klicka på länken [!UICONTROL Admin] återställ lösenord när **Lägg till lagringskod till URL:er** var *aktiverad* som tidigare resulterade i inloggningssidan eller en 404} visas.
* **ACSD-62118** (för Adobe Commerce >=2.4.6 &lt;2.4.8) - Korrigerar problemet där tabellen `sales_order_tax_item` inte uppdateras fullständigt när [!DNL B2B] order placeras med metoden Inköpsorder.
* **ACSD-63067** (för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.4.8) - Korrigerar problemet där alla produktkvantiteter markeras felaktigt och meddelandet *[!DNL Please specify the quantity of product(s).]* visas för alla produkter i en grupperad produkt när endast en kvantitet är felaktig.
* **ACSD-63090** (för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.4.8) - Korrigerar problemet där kundvagnsartiklar tas bort när en produkt tas bort efter att ha lagts till i vagnen.
* **ACSD-63182** (för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.4.8) - Korrigerar problemet när ett fel inträffar när en duplicerad paketprodukt sparas med **[!DNL MSI]** *aktiverad*.
* **ACSD-63283** (för Adobe Commerce >=2.4.4 &lt;2.4.8) - Korrigerar problemet där beställningsartiklar från presentregistret orsakar ett undantag och där presentregisteruppdateringar innehåller objekt som inte tillhör registret.
* **ACSD-63299** (för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.4.8) - Korrigerar problemet där specialpriset för en konfigurerbar produkt inte visas i butiken.
* **ACSD-63325** (för Adobe Commerce och Magento Open Source >=2.4.7 &lt;2.4.8) - Korrigerar problemet där ett `Syntax Error: Unexpected <EOF>`-fel inträffar när en tom [!DNL GraphQL] -begäran skickas.
* **ACSD-63329** (för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.4.8) - Korrigerar problemet där standardvärden för attribut med **[!UICONTROL Date]** eller **[!UICONTROL Date and Time]** indatatyper inte anges när du skapar produkter via [!DNL REST API].
* **ACSD-63572** (för Adobe Commerce och Magento Open Source >=2.4.5 &lt;2.4.8) - Korrigerar problemet där de temporära tabellerna för `CatalogRule`-indexeraren inte rensas om indexeringsprocessen avslutas.
* **ACSD-63578** (för Adobe Commerce >=2.4.4 &lt;2.4.8) - Korrigerar problemet där **[!UICONTROL Delete]**-knappen i **[!UICONTROL Add to Order by SKU]** i [!UICONTROL Admin] inte tar bort [!DNL SKU] när du klickar på  -knappen.
* Uppdaterade versioner: **MDVA-39305-V3**
* Ersatta korrigeringsfiler: **ACSD-56280**
* Inaktuella korrigeringsfiler: **ACSD-62872**

## v1.1.57 {#v1-1-57}

* **ACSD-57570** (för Adobe Commerce >=2.4.4 &lt;2.4.4-p10) - Korrigerar problemet där en begränsad administratörsanvändare med åtkomst till en viss butik inte alltid kan se alla delade kataloger som produkterna är tilldelade till, och inte heller kan se kunder som inte kan sparas, vilket leder till inkonsekvenser i systemet.
* **ACSD-58325** (för Adobe Commerce >=2.4.6 &lt;2.4.7) - Korrigerar problemet där knappen **[!UICONTROL Import]** är tillgänglig även efter ett valideringsfel.
* **ACSD-59083** (för Adobe Commerce >=2.4.4 &lt;2.5.0) - Korrigerar problemet där vissa databasuppdateringsåtgärder resulterar i ett *Bastabell- eller vyfel som inte hittas* om [!DNL mview]-uppdateringen körs samtidigt.
* **ACSD-61622** (för Adobe Commerce och Magento Open Source >=2.4.6-p1 &lt;2.4.7) - Korrigerar problemet där [!DNL FedEx]:s kontospecifika frekvenser saknas i svaret.
* **ACSD-61895** (för Adobe Commerce >=2.4.4 &lt;2.5.0) - Korrigerar problemet där kategorifrågan [!DNL GraphQL] returnerar kategorier med behörigheten **allow** även om rotkategorin inte har behörigheten **allow** .
* **ACSD-62212** (för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.5.0) - Korrigerar problemet där e-postinnehållet **Har glömt lösenordet** inte översatts till butiksvyns språk.
* **ACSD-62481** (för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.5.0) - Korrigerar problemet där kundens kundvagn blir tom även om **[!UICONTROL Persistence]** är aktiverat.
* **ACSD-62629** (för Adobe Commerce och Magento Open Source >=2.4.7 &lt;2.5.0) - Korrigerar problemet där en produktlista som används i **[!UICONTROL Widgets]** inte speglar kategorivillkoret.
* **ACSD-62635** (för Adobe Commerce och Magento Open Source >=2.4.7 &lt;2.5.0) - Korrigerar problemet där produkter som är relaterade till flera butiker inte visas korrekt i produktfrågan för [!DNL GraphQL].
* **ACSD-62671** (för Adobe Commerce och Magento Open Source >=2.4.7 &lt;2.5.0) - Korrigerar problemet där [!DNL GraphQL]-begäran inte returnerar aktuell adressinformation vid det första försöket.
* **ACSD-62689** (för Adobe Commerce och Magento Open Source >=2.4.7 &lt;2.5.0) - Korrigerar problemet där kunden inte kan lägga till kategorier i **[!UICONTROL Related Product Rules and Widgets]** efter *depth 4*.
* **ACSD-62708** (för Adobe Commerce och Magento Open Source >=2.4.4-p11 &lt;2.4.5) || >=2.4.5-p10 &lt;2.4.6-p2 || >=2.4.6-p8 &lt;2.4.7-p1) - Korrigerar problemet där [!DNL TinyMCE] 7-redigerarens teckensnittsstorlek i administratören visar *PT* och inte *PX* . Nu kan du även ange teckenstorleken i *PX* i stället för *PT*.
* **ACSD-62758** (för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.5.0) - Korrigerar problemet där produktvideor inte återges korrekt på informationssidan för **[!UICONTROL Configurable Product]** om [!DNL URL] innehåller valda alternativ.
* **ACSD-62951** (för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.5.0) - Korrigerar problemet där e-postmeddelandet om kreditnota skickas utan att några artiklar eller summor tas med.
* **ACSD-62965** (för Adobe Commerce >=2.4.7 &lt;2.5.0) - Korrigerar problemet där ett `LocalizedException`-meddelande inte ingår i orderplaceringssvaret [!DNL GraphQL].
* **ACSD-63286** (för Adobe Commerce >=2.4.6 &lt;2.4.7) - Korrigerar problemet där produkter som tilldelats till en delad katalog via [!DNL API] inte visas i butiken förrän en manuell omindexering har utförts.
* **ACSD-63326** (för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.5.0) - Korrigerar problemet där [!UICONTROL Admin] omdirigeras till en bruten sida efter att en beställning har gjorts från serverdelen.
* Uppdaterade versioner: **ACSD-51739**
* Ersatta korrigeringsfiler: **MDVA-43451**, **ACSD-62755**

## v1.1.56 {#v1-1-56}

* **ACSD-63244** (för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.4.8) - Korrigerar problemet där ett [!DNL JavaScript] -fel förhindrar att [!DNL Google Maps] återges korrekt. Åtgärdar problemet där det finns många *Uncaught TypeError: this._each är inte en funktion*-fel i konsolen på panelen [!UICONTROL Admin].
* **ACSD-63242** (för Adobe Commerce och Magento Open Source >=2.4.6-p8 &lt;2.4.7) || >=2.4.7-p3 &lt;2.4.8) - Korrigerar problemet med låg importhastighet när katalogprodukter med fler än 10 000 poster läggs till.
* **ACSD-63062** (för Adobe Commerce och Magento Open Source >=2.4.7 &lt;2.4.8) - Korrigerar problemet där felaktiga kundrabattberäkningar inträffar när flera överlappande regler tillämpas.
* **ACSD-62979** (för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.4.7) - Korrigerar problemet där fel [!UICONTROL Store ID] i [!DNL GraphQL]-huvudet orsakar ett allvarligt minnesfel.
* **ACSD-62971** (för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.4.8) - Korrigerar problemet där import av Stock-källor med icke-numeriska värden i kolumnen **quantity** resulterar i att **quantity** anges till *0*.
* **ACSD-62872** (för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.4.8) - Åtgärdar problemet med unik attributvalidering där schemauppdateringar valideras felaktigt.
* **ACSD-62755** (för Adobe Commerce och Magento Open Source >=2.4.4-p11 &lt;2.4.5) || >=2.4.5-p10 &lt;2.4.6 || >=2.4.6-p8 &lt;2.4.7 || >=2.4.7-p3 &lt;2.4.8) - Korrigerar problemet där [!DNL TinyMCE] 7 kräver att teckensnittsstorlek och teckensnitt läggs till specifikt i initieringsinställningarna för redigeraren.
* **ACSD-62670** (för Adobe Commerce och Magento Open Source >=2.4.4-p11 &lt;2.4.5) || >=2.4.5-p10 &lt;2.4.6 || >=2.4.6-p8 &lt;2.4.7 || >=2.4.7-p3 &lt;2.4.8) - Korrigerar problemet där [!UICONTROL Products Ordered] rapporterar export till [!DNL CSV] och [!DNL XML] returnerar ett fel.
* **ACSD-62577** (för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.4.8) - Korrigerar problemet med långsam prestanda för sökfrågor i butiker genom att optimera både fråga- och tabellindex.
* **ACSD-62475** (för Adobe Commerce och Magento Open Source >=2.4.7 &lt;2.4.8) - Korrigerar problemet där [!UICONTROL Gift Card]-produkterna sammanfogas felaktigt i kundvagnen.
* **ACSD-62428** (för Adobe Commerce och Magento Open Source >=2.4.6 &lt;2.4.7) - Korrigerar problemet där `is_out_of_stock` är inställt på ett felaktigt värde i katalogsökningsindexet när [!DNL SKU] inte är inställt som ett sökbart attribut.
* **ACSD-62355** (för Adobe Commerce och Magento Open Source >=2.4.6 &lt;2.4.8) - Förbättrar inläsningstiden för den konfigurerbara produktredigeringssidan när den konfigurerbara produkten baseras på många attribut med många värden.
* **ACSD-61805** (för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.4.8) - Korrigerar problemet där produkter ligger utanför lagret efter att bakgrundsorderstatusen har uppdaterats via [!DNL REST API].
* **ACSD-60811** (för Adobe Commerce och Magento Open Source >=2.4.7 &lt;2.4.8) - Korrigerar problemet där det endast är möjligt att uppdatera orderstatus med ett anpassat värde eller en kommentar om den aktuella statusen är antingen *bearbetning* eller *bedrägeri*.
* **ACSD-62952** (för Adobe Commerce >=2.4.4 &lt;2.4.8) - Korrigerar problemet där datumet [!UICONTROL Gift Registry] visas felaktigt på butiken.
* **ACSD-55339** (för Adobe Commerce >=2.4.4 &lt;2.4.8) - Korrigerar problemet där en produkt [!DNL SKU] som börjar med &quot;0&quot; (noll) tar bort &quot;0&quot;, vilket förhindrar att offerten uppdateras.
**
* Uppdaterade patchar: **ACSD-59514**
* Uppdaterade versioner: **ACSD-60816**
* Ersatta korrigeringsfiler: **ACSD-59967**

## v1.1.55 {#v1-1-55}

* **ACSD-58383** (för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.4.8) - Korrigerar problemet där en återbetalning skapas via [!DNL REST API] med två identiska begäranden som utförs samtidigt, vilket skapar dubbla kreditnotor.
* **ACSD-58471** (för Adobe Commerce >=2.4.4 &lt;2.4.8) - Korrigerar problemet där dynamiskt innehåll inte kan läsas in på produktinformationssidan när de associerade katalogprisreglerna var schemalagda.
* **ACSD-58566** (för Adobe Commerce >=2.4.6 &lt;2.4.8) - Korrigerar problemet där [!DNL GraphQL] returnerar ett internt serverfel när fältet `created_at` frågas i mutationen `addPurchaseOrderComment`.
* **ACSD-58685** (för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.4.8) - Korrigerar det problem där e-postmeddelanden som initierats när e-postkommunikation inaktiverades, fortfarande skulle skickas när e-postkommunikation återaktiverades.
* **ACSD-58735** (för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.4.8) - Korrigerar problemet där en begränsad administratör inte kunde visa de övergivna kundvagnarna på kundkontosidan i [!UICONTROL Admin] för en associerad webbplats.
* **ACSD-58828** (för Adobe Commerce och Magento Open Source >=2.4.6 &lt;2.4.8) - Korrigerar problemet där serversidans valideringsmeddelande *address krävs* visas om ett obligatoriskt fält lämnas tomt, tillsammans med valideringsmeddelandet på klientsidan. Verifieringen på serversidan visar inte meddelandet om tomma obligatoriska fält, och verifieringen på klientsidan kommer att hantera felmeddelandet med meddelandet *Detta är ett obligatoriskt fält.*
* **ACSD-60344** (för Adobe Commerce >=2.4.4 &lt;2.4.8) - Korrigerar problemet där e-postmeddelanden med dubblettorderbekräftelse skickas när en **[!UICONTROL Purchase Order]** används med automatiskt godkännande.
* **ACSD-61348** (för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.4.8) - Korrigerar problemet där önskelisteobjekt visas via [!DNL GraphQL], men inte i butiken i en miljö med flera webbplatser.
* **ACSD-61534** (för Adobe Commerce och Magento Open Source >=2.4.7 &lt;2.4.8) - Korrigerar problemet där designkonfigurationen inte kunde anges med kommandot `bin/magento config:set` och låsta värden kan ändras med formulärhantering. Låsta värden som angetts från [!DNL CLI] med `--lock-env` eller `--lock-conf` kan inte uppdateras.
* **ACSD-61785** (för Adobe Commerce >=2.4.4 &lt;2.4.8) - Åtgärdar problemet där det inte gick att uppdatera `reward_warning_notification` -attributet via [!DNL GraphQL] mutation- och [!DNL REST API]-anrop, vilket justerar dess beteende med `reward_update_notification`.
* **ACSD-62591** (för Adobe Commerce och Magento Open Source >=2.4.7 &lt;2.4.8) - Korrigerar problemet där temat inte växlar korrekt när **[!UICONTROL User Agent Rules]** är konfigurerat.
* **ACSD-62793** (för Adobe Commerce och Magento Open Source >=2.4.7 &lt;2.4.8) - Korrigerar problemet där `datetime` -attribut i exporterade data inte innehåller tidskomponenten. Om **[!UICONTROL Fields Enclosure]** dessutom är *aktiverad* kommer attributvärden i kolumnen `additional_attributes` att omslutas av dubbla citattecken.
* **ACSD-62332** (för Adobe Commerce >=2.4.6 &lt;2.4.7) - Korrigerar problemet där produktlistfrågan [!DNL GraphQL] var begränsad till `total_count` av 10 000 produkter. Korrigerar problemet där [!DNL Live Search] ställer in den aktuella sidan till ** i stället för sidan ** i sökvillkoren när frågan ställs via [!DNL GraphQL].
* Uppdaterade versioner: **ACSD-46581**, **ACSD-49513**, **ACSD-52801**, **ACSD-59514**
* Ersatta korrigeringsfiler: **ACSD-52801**, **ACSD-55100**
* Föråldrade korrigeringsfiler: **ACSD-52085**, **ACSD-57854**

## v1.1.54 {#v1-1-54}

* **AC-13283** (för Adobe Commerce och Magento Open Source 2.4.6-p8) - Återställer monteringsordning bakåt och inkompatibla ändringar som ingår i 2.4.6-p8.
* **ACSD-60267** (för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.4.8) - Korrigerar problemet där FPT (Fixed Product Tax) tillämpas korrekt när enkla produkter läggs till direkt i kundvagnen, men misslyckas när du väljer dessa produkter med konfigurerbara produktalternativ.
* **ACSD-61103** (för Adobe Commerce och Magento Open Source >=2.4.6 &lt;2.4.7) - Korrigerar problemet där antalet fel i tabellen `customer_entity` inte återställs till noll när en kund har loggat in via API-slutpunkter.
* **ACSD-61134** (för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.4.7) - Korrigerar problemet där betalningsmetoden [!DNL Braintree Vault] automatiskt avmarkeras i kassaarbetsflödet när en kund uppdaterar sin faktureringsadress genom att avmarkera kryssrutan *[!UICONTROL My billing and shipping address are the same]*.
* **ACSD-61199** (för Adobe Commerce >=2.4.4 &lt;2.4.8) - Korrigerar problemet där sidhierarkifliken i CMS inte visar en korrekt trädstruktur när en CMS-sida med en befintlig hierarki redigeras.
* **ACSD-61200** (för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.4.8) - Korrigerar problemet där beräkningarna för *[!UICONTROL Total Amount]* och *[!UICONTROL Total Amount Actual]* i försäljningen saknar *[!UICONTROL Discount Tax Compensation Amount]* och *[!UICONTROL Shipping Discount Tax Compensation Amount]*, vilket orsakar avvikelser i försäljningsorderdata.
* **ACSD-61522** (för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.4.8) - Korrigerar problemet där det går att ange e-postadresser i gästkundens fält *[!UICONTROL First Name]* och *[!UICONTROL Last Name]* och skicka ogiltiga orderbekräftelsemeddelanden via e-post.
* **ACSD-61756** (för Adobe Commerce >=2.4.4 &lt;2.4.7) - Förbättrar prestanda för `AdvancedSalesRule` filter.
* **ACSD-61799** (för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.4.5) - Korrigerar problemet där den totala rabatten felaktigt beräknas när flera kundvagnsregler med fasta rabatter tillämpas på offerten.
* **ACSD-61845** (för Adobe Commerce och Magento Open Source >=2.4.7-p1 &lt;2.4.8) - Korrigerar felet som inträffar när en begäran skickas med endast *text/html* accept header.
* **ACSD-62056** (för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.4.8) - Korrigerar problemet där bildöverföringen för en konfigurerbar produkt misslyckas om MSI är installerat.
* **ACSD-62485** (för Adobe Commerce >=2.4.4 &lt;2.4.6-p8) || >=2.4.7 &lt;2.4.8) - Korrigerar problemet där `async.operations.all` konsumenten slutar arbeta när ett företag skapas.
* Uppdaterade versioner: **ACSD-48661**, **ACSD-55100**, **ACSD-61553**
* Inaktuella korrigeringsfiler: **ACSD-51846**

## v1.1.53 {#v1-1-53}

* **ACSD-48318** (för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.4.7) - Korrigerar problemet där miljöemuleringsinkapsling inte tillåts. Emuleringen startar under anropet `send()` när emuleringen stoppas under anropet till `getInfoBlockHtml()`.
* **ACSD-59930** (för Adobe Commerce >=2.4.6 &lt;2.4.8) - Förbättrar prestanda för företagets **[!UICONTROL Create]** -, **[!UICONTROL Save]** - och **[!UICONTROL Delete]** -flöden.
* **ACSD-60584** (för Adobe Commerce och Magento Open Source >=2.4.5 &lt;2.4.7) - Korrigerar problemet där en åtkomsttoken som skapats för användaren på en webbplats tillåts komma åt eller ändra kundinformation på andra webbplatser.
* **ACSD-60804** (för Adobe Commerce >=2.4.4 &lt;2.4.8) - Korrigerar problemet där redigering av en kund som är länkad till ett borttaget företag orsakar felet *Anrop till en medlemsfunktion `getSuperUserId()` på null*.
* **ACSD-61133** (för Adobe Commerce >=2.4.4-p5 &lt;2.4.5) || >=2.4.5-p4 &lt;2.4.6 || >=2.4.6-p2 &lt;2.4.8) - Korrigerar problemet där `sales_clean_quotes` [!DNL cron] tar bort offerter från ej godkända inköpsorder.
* **ACSD-61528** (för Adobe Commerce >=2.4.6 &lt;2.4.8) - Korrigerar problemet där hämtning av roller från [!UICONTROL Admin] med [!DNL GraphQL] inte ger några resultat.
* **ACSD-61553** (för Adobe Commerce och Magento Open Source >=2.4.5 &lt;2.4.7) - Korrigerar problemet där **[!UICONTROL Cart Price Rule]** rabatter inte beräknas korrekt när flera rabatter med olika prioritet och **[!UICONTROL Maximum Qty Discount is Applied To]** används för produkten.
* **ACSD-61667** (för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.4.8) - Förbättrar lagerprestanda för att skapa leveranser för många källor med upphämtning i butiken.
* **ACSD-61969** (för Adobe Commerce >=2.4.7 &lt;2.4.8) - Korrigerar problemet där användaren måste skriva in en skiftlägeskänslig kupongkod för att matcha exakt som kupongkoden konfigurerats.
* Uppdaterade versioner: **ACSD-54989**, **ACSD-60632**

## v1.1.52 {#v1-1-52}

* **BUNDLE-3375** (för Adobe Commerce och Magento Open Source) - Lägger till alla nödvändiga fält för att uppfylla kraven för 3DS VISA-fullmakt när [!DNL Braintree] används som betalningsgateway.
* **ACSD-59366** (för Adobe Commerce >=2.4.6 &lt;2.4.8) - Åtgärdar ett fel som inträffar när ett försök görs att ta bort ett team som innehåller inaktiverade användare som inte visas i grupplistan.
* **ACSD-59865** (för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.4.7) - Korrigerar problemet där en [!UICONTROL Cart Price Rule] inte avbryter tidigare tillämpade regler om kvantiteten av produkten i vagnen inte är tillräckligt för att reglerna ska tillämpas.
* **ACSD-59925** (för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.4.8) - Korrigerar problemet med sortering av objekt i [!UICONTROL Media Gallery] efter position i GraphQL.
* **ACSD-59952** (för Adobe Commerce >=2.4.4 &lt;2.4.8) - Korrigerar problemet när ett fel inträffar när en [!UICONTROL Shared Catalog] skapas med ett grupp-ID som är tilldelat till ett befintligt [!UICONTROL Shared Catalog].
* **ACSD-60590** (för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.4.7) - Förbättrar prestanda för generering av [!UICONTROL Bestsellers Aggregated Daily Reports] för ett stort antal placerade order.
* **ACSD-60673** (för Adobe Commerce >=2.4.4 &lt;2.4.8) - Korrigerar problemet där [!UICONTROL Cart Price Rule] för flera betalningsmetoder vid utcheckning inte gäller korrekt för den specifika betalningsmetoden.
* **ACSD-60684** (för Adobe Commerce och Magento Open Source >=2.4.6 &lt;2.4.7) - Korrigerar problemet där GraphQL produktsortering efter flera fält inte fungerar som förväntat.
* **ACSD-60788** (för Adobe Commerce >=2.4.7 &lt;2.4.8) - Korrigerar problemet där anpassade skript för [!DNL Google Tag Manager] inte körs på grund av fel i Content Security Policy (CSP).
* **ACSD-61322** (för Adobe Commerce >=2.4.6 &lt;2.4.8) - Korrigerar problemet där [!UICONTROL Products/Categories] som inte har tilldelats [!UICONTROL Shared Catalog] för standardgruppen (allmän grupp) fortfarande ingår i XML-platskartan.
* **ACSD-61366** (för Adobe Commerce och Magento Open Source >=2.4.7 &lt;2.4.8) - Korrigerar problemet där `setup:static-content:deploy --jobs 4`-kommandot körs med flera jobb som inte fungerar med *Port måste konfigureras i värdparameterfelet* när porten har angetts för databasanslutningen.
* Uppdaterade patchar: ACSD-51857, ACSD-57394

## v1.1.51 {#v1-1-51}

* **ACSD-59786** (för Adobe Commerce och Magento Open Source >=2.4.6 &lt;2.4.8) - Korrigerar problemet där GraphQL returnerar ett internt serverfel när ett offert-ID för en offert som gått ut ska hämtas.
* **ACSD-60234** (för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.4.8) - Korrigerar problemet där ett felaktigt belopp visas [!DNL PayPal] när rabatten tillämpas av betalningsmetoden.
* **ACSD-59967** (för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.4.7-p2) - Korrigerar problemet där ett JavaScript-fel förhindrar att [!DNL Google Maps] återges korrekt.
* **ACSD-60326** (för Adobe Commerce >=2.4.4 &lt;2.4.8) - Korrigerar problemet där ett fel inträffar i GraphQL-frågan om kundreturstatus.
* **ACSD-60538** (för Adobe Commerce >=2.4.7 &lt;2.4.8) - Korrigerar problemet där produktattributen inte visas korrekt i GraphQL-svaret om en produkt är inaktiverad i *[!UICONTROL All Store Views]* och endast är aktiverad i specifika butiksvyområden, vilket leder till att produkten inte visas korrekt.
* **ACSD-60631** (för Adobe Commerce och Magento Open Source >=2.4.7 &lt;2.4.8) - Korrigerar problemet där GraphQL returnerar ett fel när samma enkla produkt tilldelas till flera konfigurerbara produkter.
* **ACSD-60632** (för Adobe Commerce och Magento Open Source >=2.4.5-p8 &lt;2.4.8) - Korrigerar problemet där en ny adress sparas varje gång ett orderplaceringsförsök görs, oavsett om ordern har skapats eller inte.
* **ACSD-60816** (för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.4.7) - Korrigerar problemet där [!DNL New Relic Browser Monitoring] -skripten som injicerats av APM-agenten inte är kompatibla med CSP (Content Security Policy), vilket förhindrar att de körs.
* **ACSD-61195** (för Adobe Commerce och Magento Open Source >=2.4.7 &lt;2.4.8) - Korrigerar problemet där inga kundvagnsobjekt returneras på den sista sidan för GraphQL-kundvagnsbegäran.
* Uppdaterade patchar: ACSD-59378

## v1.1.50 {#v1-1-50}

* **ACSD-59280** (för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.4.5) - Korrigerar felet *Anrop till den odefinierade metoden ReflectionUnionType::getName()* som inträffar när 2.4.4-pX-versioner installeras.
* **ACSD-45049** (för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.4.4-p8) || >=2.4.5 &lt;2.4.6) - Korrigerar problemet där en kund *[!UICONTROL Is required]* -attributinställning inte fungerar som den ska per webbplats i Admin.
* **ACSD-46938** (för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.4.6) - Korrigerar problemet med prestandan för DB-utlösare som återskapas under `setup:upgrade`.
* **ACSD-48210** (för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.4.7) - Korrigerar problemet där uppdateringen av ett *[!UICONTROL Website Scope]* -attribut i en viss butiksvy åsidosätter attributvärdena i det globala omfånget.
* **ACSD-54887** (för Adobe Commerce och Magento Open Source >=2.4.4-p4 &lt;2.4.4-p9) || >=2.4.5-p3 &lt;2.4.5-p8 || >=2.4.6-p1 &lt;2.4.6-p6) - Korrigerar problemet där kundvagnen rensas efter att kundsessionen har upphört och [!UICONTROL Persistent Shopping Cart] är aktiverat.
* **ACSD-58141** (för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.4.8) - Korrigerar problemet där PHPSESSID återskapas vid begäranden om POST i butiksområdet för en inloggad kund om [!DNL L2 Redis cache] är aktiverad och kunden uppdateras från Admin.
* **ACSD-58352** (för Adobe Commerce >=2.4.4 &lt;2.4.7) - Korrigerar problemet där returattributetiketter för standardbutiksvyn returneras via GraphQL API när en icke-standardbutiksvy anges i begärandehuvudet.
* **ACSD-58442** (för Adobe Commerce >=2.4.4 &lt;2.4.7-p1) - Korrigerar problemet där enheter med en bredd på 768 px behandlas som mobila, vilket gör att meny och rubrik läses in i mobilvyn i stället för i skrivbordsvyn.
* **ACSD-58790** (för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.4.8) - Korrigerar funktionen nyp till zoomning på produktinformationssidans bilder i mobilvyn på [!DNL Chrome].
* **ACSD-59036** (för Adobe Commerce och Magento Open Source >=2.4.7 &lt;2.4.8) - Åtgärdar ett undantag som inträffar när produktpriser läses in med både nedre och övre gränser som är lika med $0.
* **ACSD-59229** (för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.4.7) - Korrigerar problemet där kundgruppsrelaterad information sparas i fel segment på grund av det gamla värdet för X-Magento-Vary i begäran.
* **ACSD-59378** (för Adobe Commerce och Magento Open Source >=2.4.5 &lt;2.4.6) - Korrigerar problemet där URL-omskrivningar på butiksnivå uppdateras felaktigt under importen.
* **ACSD-59514** (för Adobe Commerce >=2.4.4 &lt;2.4.7-p2) - Korrigerar problemet där formulär i administrationsområdet med [!DNL Page Builder] orsakade felet *[!DNL Page Builder]återgav i 5 sekunder utan att frigöra lås.* i webbläsarkonsolen när formuläret har skickats och det går inte att spara ändringarna.
* **ACSD-60303** (för Adobe Commerce >=2.4.4-p9 &lt;2.4.5) || >=2.4.5-p8 &lt;2.4.6 || >=2.4.6-p6 &lt;2.4.8) - Korrigerar problemet där en beställning från Admin inte kan placeras om HTML-minification är aktiverat.
* **ACSD-60441** (för Adobe Commerce och Magento Open Source 2.4.4-p9) || 2.4.5-p8 || 2.4.6-p6 || 2.4.7-p1) - Åtgärdar problemet med att uppdatera kunder via `V1/customers` [!DNL REST API] -slutpunkten när du använder integreringsåtkomsttoken som genererats från backend-servern.
* Uppdaterade patchar: ACSD-57003

## v1.1.49 {#v1-1-49}

* **ACSD-56979** (för Adobe Commerce och Magento Open Source >=2.4.3 &lt;2.4.7) - Korrigerar problemet där produktbilder tas bort efter att en mellanlagringsuppdatering har tagits bort.
* **ACSD-57086** (för Adobe Commerce och Magento Open Source >=2.4.3 &lt;2.4.7) - Korrigerar problemet där beställningar från icke-standardwebbplatser med aktiverade villkor inte behandlas korrekt.
* **ACSD-57588** (för Adobe Commerce och Magento Open Source >=2.4.6 &lt;2.4.7) - Korrigerar problemet där leverans av en order till flera adresser utlöser ett fel under bearbetning av region-ID.
* **ACSD-57643** (för Adobe Commerce och Magento Open Source >=2.4.6 &lt;2.4.7) - Korrigerar problemet där produkter med anpassade alternativ felaktigt läggs till i kundvagnen via GraphQL.
* **ACSD-57846** (för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.7) - Korrigerar problemet där GraphQL-produkter som söker efter ett filter för nollpriser inte returnerar några resultat på grund av ett undantag.
* **ACSD-57941** (för Adobe Commerce och Magento Open Source >=2.4.6 &lt;2.4.7) - Korrigerar problemet där produktalternativ felaktigt har tilldelats till administratörsarkivet i stället för deras respektive butiker.
* **ACSD-58375** (för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.7) - Korrigerar problemet där fel *[!DNL YouTube API Key]* -konfiguration orsakar ett fel när en [!DNL YouTube] -video läggs till på butiksvynivå.
* **ACSD-58739** (för Adobe Commerce och Magento Open Source >=2.4.7 &lt;2.4.8) - Korrigerar problemet där partiell omindexering orsakar ett fel.
* **ACSD-58446** (för Adobe Commerce >=2.4.6 &lt;2.4.7) - Korrigerar problemet där systemet ger ett felmeddelande som inte är informativt och som inte är förenligt med användargränssnittet när ett team med underordnade användare eller team tas bort, oavsett status (inaktiv).
* **ACSD-58054** (för Adobe Commerce >=2.4.4 &lt;2.4.6) - Korrigerar problemet där det går att generera kundtoken för inaktiva kunder via API.
* **ACSD-58163** (för Adobe Commerce >=2.4.3 &lt;2.4.7) - Korrigerar problemet där *[!UICONTROL Cart Price Rule]* inte tillämpar en rabatt för en gästkund från den matchande *[!UICONTROL Customer Segment]*-vagnen utan kupongkod.
* **ACSD-57045** (för Adobe Commerce >=2.4.5 &lt;2.4.7) - Korrigerar problemet där URL-omskrivningar orsakar oändliga sidloopar efter att *[!UICONTROL Website Root]* har avmarkerats från *[!UICONTROL Hierarchy]*.
* Uppdaterade patchar: ACSD-46815, ACSD-47027, ACSD-51683, ACSD-55031, ACSD-51819, ACSD-54965-v2

## v1.1.48 {#v1-1-48}

* **ACSD-55566** (för Adobe Commerce och Magento Open Source >=2.4.3 &lt;2.4.7) - Korrigerar problemet där `mergeCart`-mutationen misslyckas med ett *internt serverfel* i [!DNL GraphQL]-svaret när käll- och målkundvagnar som har samma paketobjekt sammanfogas.
* **ACSD-56546** (för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.4.7) - Korrigerar problemet där konfigurerbara produkter och paketprodukter visas som **Utanför lagret** när **inte visas i produktkonfigurationen** är *Inaktiverat*.
* **ACSD-56635** (för Adobe Commerce >=2.4.6 &lt;2.4.7) - Korrigerar problemet där den importerade kunden dupliceras med samma e-postadress när en import används med **kontodelning** inställd på *Global*.
* **ACSD-56741** (för Adobe Commerce och Magento Open Source >=2.4.6 &lt;2.4.7) - Korrigerar felmeddelandet *Försöker få åtkomst till matrisförskjutning på värdet null* som visas under `setup:upgrade` när databasen innehåller en anpassad [!DNL MySQL]-utlösare som inte är relaterad till indexeringsmekanismen och [!DNL MView].
* **ACSD-57315** (för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.7) - Korrigerar problemet när en ny transaktion skapas i [!DNL PayPal Payflow Pro] varje gång knappen [!UICONTROL Fetch] klickas på skärmen **[!UICONTROL View transaction]** i Admin.
* **ACSD-57337** (för Adobe Commerce >=2.4.4 &lt;2.4.6) - Korrigerar problemet där en administratörsanvändare med åtkomstbegränsningar för specifika webbplatser kan se företag från alla webbplatser i rutnätet **[!UICONTROL Companies]** .
* **ACSD-57394** (för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.4.7) - Korrigerar problemet med felaktig produktsortering efter flera sorteringsfält i [!DNL GraphQL].
* **ACSD-57565** (för Adobe Commerce och Magento Open Source >=2.4.6 &lt;2.4.7) - Korrigerar problemet där kontrollpanelen i **[!UICONTROL Order]** visar felaktig ordningsinformation tills tidsperioden har uppdaterats. På kontrollpanelen visas nu korrekt orderstatistik vid den första inläsningen.
* **ACSD-57854** (för Adobe Commerce och Magento Open Source >=2.4.5 &lt;2.4.7) - Korrigerar problemet när [!DNL GraphQL] -produktförfrågningar returnerade inaktiverade kategorier i kategoriaggregeringarna.
* **ACSD-58008** (för Adobe Commerce >=2.4.5 &lt;2.4.7) - Korrigerar problemet där en schemalagd uppdatering tog bort den tidigare versionen av ett mellanlagrat objekt, om inget slutdatum angavs.
* Uppdaterade patchar: MDVA-39305-V2, ACSD-48627, ACSD-54965

## v1.1.47 {#v1-1-47}

* **ACSD-55241** (för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.7) - Korrigerar problemet där attributen *[!UICONTROL Used]* och *[!UICONTROL Times Used]* visar felaktiga värden för genererade kuponger när de används vid utcheckning med flera adresser.
* **ACSD-56760** (för Adobe Commerce >=2.4.6 &lt;2.4.7) - Korrigerar problemet där en administratörsanvändare som är begränsad till en viss webbplats inte kan sortera eller lägga till nya produkter i en kategori om webbutiken har en egen rotkategori.
* **ACSD-56858** (för Adobe Commerce >=2.4.2 &lt;2.4.7) - Korrigerar problemet där B2B-företagsrollbehörigheter visas felaktigt för en företagsadministratör med begränsat antal användare.
* **ACSD-57074** (för Adobe Commerce och Magento Open Source >=2.4.6 &lt;2.4.7) - Korrigerar problemet där det anpassade attributet *Yes/No* med `attrbute_code` som börjar med `price_` inte fungerar korrekt med indexering, och produkter med sådana attribut inte är tillgängliga på frontsidan.
* Uppdaterade patchar: ACSD-53378, ACSD-51819

## v1.1.46 {#v1-1-46}

* **ACSD-46767** (för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.4.6) - Korrigerar problemet där kategorisidan cachelagrar ogiltiga när lagerkvantiteten ändras, även om produkten fortfarande finns i lager.
* **ACSD-54656** (för Adobe Commerce >=2.4.5 &lt;2.4.6) - Korrigerar problemet där den osynliga Recaptcha misslyckas under utcheckningen, vilket förhindrar att en ordning placeras.
* **ACSD-55100** (för Adobe Commerce >=2.4.6 &lt;2.4.7) - Korrigerar problemet där GraphQL inte returnerar mer än 10 000 produkter i sökresultaten.
* **ACSD-56621** (för Adobe Commerce >=2.4.2 &lt;2.4.7) - Korrigerar problemet där det uppdaterade förnamnet och efternamnet inte visas i sidhuvudet för hälsningar för företagsadministratörsanvändaren.
* **ACSD-56842** (för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.7) - Korrigerar problemet där de fördröjda proxyfabrikerna och de fördröjda proxyfabrikerna saknas efter körning av `setup:di:compile`.
* **ACSD-57003** (för Adobe Commerce och Magento Open Source >=2.4.6 &lt;2.4.7) - Korrigerar problemet där orderstatusen ändras till *[!UICONTROL Complete]* i stället för att ändras till *[!UICONTROL Processing]* när en order delvis återbetalas och delvis skickas.
* Uppdaterade patchar: ACSD-50260-v2, ACSD-54966

## v1.1.45 {#v1-1-45}

* **ACSD-56886** (för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.7) - Korrigerar problemet där en konfigurerbar produkt inte finns i lager när en av två underordnade produkter inaktiveras av en schemalagd uppdatering.
* **ACSD-56616** (för Adobe Commerce och Magento Open Source >=2.4.5 &lt;2.4.6) - Korrigerar problemet där paketerade produkter visas som i lager på butiken när deras enkla produkter inte finns i lager.
* **ACSD-56515** (för Adobe Commerce >=2.4.2 &lt;2.4.7) - Korrigerar problemet där en administratör med behörighet på webbplatsnivå inte kan lägga till eller redigera ett dynamiskt block.
* **ACSD-56447** (för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.7) - Korrigerar problemet där tillägg av samma produkt till kundvagnen via parallella REST webb-API-begäranden resulterar i två separata objekt i kundvagnen.
* **ACSD-56415** (för Adobe Commerce och Magento Open Source >=2.4.5 &lt;2.4.7) - Korrigerar problemet där prestandan för partiell prisindexering försämras på grund av en `DELETE` -fråga när databasen har många partiella prisdata att indexera.
* **ACSD-54965** (för Adobe Commerce >=2.4.5 &lt;2.4.6) - Korrigerar problemet där Visual Merchandising-rutnätet inte visar korrekt mediefil när en produkt endast har tilldelats till anpassat lager.
* **ACSD-52824** (för Adobe Commerce >=2.4.5 &lt;2.4.7) - Korrigerar problemet där PayPal Express-, Google Pay- och Apple Pay-knapparna visas för företagskunder när sådana betalningsmetoder är inaktiverade i företagsinställningarna.
* Uppdaterade patchar: ACSD-56193

## v1.1.44 {#v1-1-44}

* **ACSD-56790** (för Adobe Commerce och Magento Open Source >=2.4.6 &lt;2.4.7) - Korrigerar problemet där en användare omdirigeras till Admin Dashboard när kategoriprodukter sorteras med alternativet **Flytta från Stock till botten** och felet `Invalid security or form key. Please refresh the page` visas högst upp på skärmen.
* **ACSD-56280** (för Adobe Commerce >=2.4.4 &lt;2.4.7) - Korrigerar problemet där beställning från ett presentregister leder till ett undantag.
* **ACSD-56246** (för Adobe Commerce och Magento Open Source >=2.4.6 &lt;2.4.7) - Korrigerar problemet där data tas bort från det anpassade flervalsattributet när en schemalagd uppdatering för en produkt aktiveras.
* **ACSD-56193** (för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.4) - Korrigerar ett fel där cacheminnet Varnish/Fastly inte uppdateras när ett schemalagt block används i kategoribeskrivningen med Page Builder.
* **ACSD-56158** (för Adobe Commerce och Magento Open Source >=2.4.5 &lt;2.4.7) - Korrigerar problemet där kundvagnsfrågan returnerar det totala momsvärdet för varje momsregel.
* **ACSD-56023** (för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.7) - Korrigerar problemet där widgetinnehåll inte uppdateras på CMS-sidan när cache är aktiverat.
* **ACSD-55427** (för Adobe Commerce >=2.4.5 &lt;2.4.7) - Korrigerar problemet där administratörsanvändaren inte kan ta bort tilldelningen av en produkt från en delad katalog från produktsidan i Admin.
* **ACSD-55352** (för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.7) - Korrigerar problemet där orderstatusen ändras till Stängd efter att en partiell kreditnota med kundbelöningspunkter har skapats och alternativen för kreditnota försvinner från sidan för Admin-order.
* **ACSD-55231** (för Adobe Commerce >=2.4.2 &lt;2.4.7) - Korrigerar problemet där du inte kan lägga till produkter i en kundvagn med snabborderfunktionen.
* **ACSD-54283** (för Adobe Commerce >=2.4.3 &lt;2.4.4) - Korrigerar problemet där produkter/kategorier som inte har tilldelats den delade katalogen för standardkatalogen (allmän grupp) fortfarande ingår i XML-platskartan.
* Uppdaterade patchar: ACSD-52041, ACSD-54040, ACSD-51819

## v1.1.43 {#v1-1-43}

* **ACSD-54972** (för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.7) - Korrigerar problemet där URL:en för den kanoniska kategorin inte uppdateras efter att kategorins URL har ändrats.
* **ACSD-53636** (för Adobe Commerce och Magento Open Source >=2.4.3 &lt;2.4.5) - Korrigerar problemet där det ordinarie priset inte visas på produktlistsidor för konfigurerbara produkter som har underordnade produkter med specialpriser.
* **ACSD-54885** (för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.7) - Korrigerar problemet med utcheckning av flera adresser när administratörsanvändaren använder funktionen *Logga in som kund* .
* **ACSD-55610** (för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.4.7) - Korrigerar problemet där en delvis annullerad order har ett felaktigt rabattbelopp.
* **ACSD-55334** (för Adobe Commerce och Magento Open Source >=2.4.3 &lt;2.4.7) - Korrigerar översättningar för etiketter via översättningsordlistor i GraphQL-svar.
* **ACSD-54739** (för Adobe Commerce >=2.4.5 &lt;2.4.7) - Åtgärdar ett problem där produktStock-statusvillkoret inte tillämpas för relaterade produktregler.
* **ACSD-53925** (för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.7) - Korrigerar problemet där administratören inte kan spara CMS-blocket med produktkarusell när `catalog_product_price` dimensions-mode är inställt på *webbplats*.
* **ACSD-52714** (för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.7) - Korrigerar problemet där datumfiltret inte fungerar i administratörsrutnätet när datumformatet är inställt på *Y-m-d*.
* **ACSD-55055** (för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.7) - Förbättrar prestanda för inläsning av produktattribut i kundvagnsregler i kundvagnen.
* **ACSD-53790** (för Adobe Commerce >=2.4.6 &lt;2.4.7) - Korrigerar problemet där flera RMA-filer för en enskild produkt kan skapas via REST API.
* **ACSD-56090** (för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.5) - Korrigerar problemet där GraphQL-begäran svarar med alla butiksdata i stället för de specifikt begärda lagringsdata.
* **ACSD-54983** (för Adobe Commerce >=2.4.2 &lt;2.4.7) - Korrigerar problemet där det inte går att hämta företagsanvändaren UID med GraphQL-begäran när användarstatusen är *[!UICONTROL Inactive]*.
* **ACSD-53309** (för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.7) - Korrigerar problemet där moms inte tillämpas fullt ut i etiketten *[!UICONTROL Regular Price]* när det anpassningsbara alternativet är valt.
* **ACSD-55305** (för Adobe Commerce >=2.4.4 &lt;2.4.7) - Korrigerar problemet där popup-fönstret *[!UICONTROL Edit Company User]* på **[!UICONTROL myAccount]** > **[!UICONTROL Company Structure]** -sidan låser sig med en inläsare på skärmen.
* Uppdaterade patchar: ACSD-49013

## v1.1.42 {#v1-1-42}

* **ACSD-53658** (för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.4.7) - Korrigerar problemet där *[!UICONTROL Recently Viewed]* produktdata inte uppdateras korrekt i butiksvyn.
* **ACSD-54626** (för Adobe Commerce >=2.4.6 &lt;2.4.7) - Korrigerar problemet där du inte kan skapa en ny inköpsorderregel (`createPurchaseOrderApprovalRule`) med attributet `NUMBER_OF_SKUS` via [!DNL GraphQL].
* **ACSD-53845** (för Adobe Commerce och Magento Open Source >=2.4.0 &lt;2.4.7) - Korrigerar [!DNL MySQL] timeout-problemet för anslutningen när `consumer max_messages` = 0.
* **ACSD-54890** (för Adobe Commerce och Magento Open Source >=2.4.0 &lt;2.4.7) - Korrigerar problemet där `aggregate_sales_report_bestsellers_data` orsakar [!DNL MySQL] fel på grund av att det inte finns tillräckligt med utrymme på `/tmp`-disken.
* **ACSD-55112** (för Adobe Commerce och Magento Open Source >=2.4.0 &lt;2.4.7) - Korrigerar problemet där *[!UICONTROL Submit review]*-knappen kan klickas flera gånger utan [!DNL Google reCAPTCHA v3]-validering.
* **ACSD-54264** (för Adobe Commerce >=2.4.4-p5 &lt;2.4.5) || >=2.4.5-p4 &lt;2.4.6 || >=2.4.6-p2 &lt;2.4.7) - Korrigerar problemet där felmeddelandet *&quot;Det går inte att uppdatera det begärda attributet. Rad-ID: store_id* visas när en kund försöker checka ut med en överlåtbar offert från en annan butiksvy.
* **ACSD-54418** (för Adobe Commerce och Magento Open Source >=2.4.0 &lt;2.4.7) - Korrigerar problemet där ett fast rabattbelopp felaktigt tillämpas på varje underordnad produkt till det dynamiskt prissatta paketet.
* **ACSD-55238** (för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.4.7) - Korrigerar sparandet av den tomma produkten *[!UICONTROL Meta Description]*.
* **ACSD-54966** (för Adobe Commerce och Magento Open Source >=2.4.5 &lt;2.4.7) - Korrigerar problemet där en kupongkod med begränsad användning per kund inte kan återanvändas om föregående order misslyckas.
* **ACSD-54060** (för Adobe Commerce och Magento Open Source >=2.4.3 &lt;2.4.7) - Korrigerar problemet där en begränsad administratör inte kan spara en produkt om den är underordnad en annan produkt som tilldelats ett annat omfång.
* **ACSD-48910** (för Adobe Commerce och Magento Open Source >=2.4.5 &lt;2.4.6) - Korrigerat problemet där en paketprodukt som tilldelats flera källor går ut ur lagret efter att en order har fakturerats och skickats, även om den fortfarande har en kvantitet som inte är noll.
* **ACSD-55381** (för Adobe Commerce >=2.4.2 &lt;2.4.7) - Korrigerar ett internt serverfel när `configurable_product_option_uid` - och `configurable_product_option_value_uid` -fält från en [!DNL B2B] *[!UICONTROL Requisition list]* via [!DNL GraphQL] efterfrågas.
* **ACSD-55628** (för Adobe Commerce >=2.4.4-p2 &lt; 2.4.5) || >=2.4.5-p1 &lt; 2.4.6) - Korrigerar överföring av en fil i företagsregistreringsformuläret och ersättning av en fil för ett kundattribut i butiken.
* Uppdaterade patchar: ACSD-51240, ACSD-51890, ACSD-53098

## v1.1.41 {#v1-1-41}

* **ACSD-54376** (för Adobe Commerce >=2.4.2 &lt;2.4.7) - Korrigerar problemet som uppstår i kundvagnen när en produkt tas bort från den delade katalogen efter att den redan har lagts till i kundvagnen.
* **ACSD-53722** (för Adobe Commerce >=2.4.4 &lt;2.4.7) - Korrigerar problemet där priset för produktalternativen ändras till $0 när schemalagda uppdateringar för olika omfattningar aktiveras.
* **ACSD-53643** (för Adobe Commerce >=2.4.3 &lt;2.4.7) - Korrigerar problemet där ordern har ett felaktigt totalt ordervärde när en inköpsorder med inaktiverade produkter eller produkter som inte finns i lager placeras. Den har åtgärdats genom att knappen *[!UICONTROL Place Order]* för sådana inköpsorder döljs.
* **ACSD-54067** (för Adobe Commerce och Magento Open Source >=2.4.0 &lt;2.4.7) - Korrigerar problemet där en produktvideo inte spelas upp på en mobil enhet.
* **ACSD-55414** (för Adobe Commerce och Magento Open Source >=2.4.0 &lt;2.4.6) - Förbättrar prestanda när MariaDB försöker konvertera EAV-entitet_id från sträng till heltal.
* **ACSD-51819** (för Adobe Commerce >=2.4.4 &lt;2.4.4-p4) - Korrigerar problemet där flera order kan placeras med samma offert-ID.
* **ACSD-53118** (för Adobe Commerce >=2.4.0 &lt;2.4.7) - Korrigerar problemet där *[!UICONTROL Cart Price Rule]* används med kupongkod medan produkten har ett tomt attribut, vilket borde ha gjort regeln ogiltig.
* **ACSD-54324** (för Adobe Commerce >=2.4.5 &lt;2.4.7) - Korrigerar problemet där begäran GraphQL reksition_lists inte tar hänsyn till sidnumreringsinställningar och returnerar alla resultat.
* Uppdaterade patchar: MDVA-42855-v2

## v1.1.40 {#v1-1-40}

* **ACSD-54680** (för Adobe Commerce >=2.4.0 &lt;2.4.6) - Korrigerar problemet där det inte går att bearbeta en B2B-offert som skickats för en produkt med flera tilldelade källor.
* **ACSD-54040** (för Adobe Commerce >=2.4.4-p5 &lt;2.4.5) || >=2.4.5-p4 &lt;2.4.6) - Korrigerar problemet där fältet *[!UICONTROL Created]* är tomt i den ordning som detaljer när B2B-moduler är aktiverade.
* **ACSD-54319** (för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.6) - Korrigerar problemet där produktpriset är noll i *[!UICONTROL Product in Cart]* -rapporten.
* **ACSD-53378** (för Adobe Commerce och Magento Open Source >=2.4.5 &lt;2.4.7) - Förbättrar utcheckningsidans laddningstid för kunder som har stora adressböcker.
* **ACSD-52657** (för Adobe Commerce och Magento Open Source >=2.4.5 &lt;2.4.7) - Korrigerar problemet där minikortet inte uppdateras på den sekundära butiksgranskningen, som använder en underdomän.
* **ACSD-53414** (för Adobe Commerce >=2.4.6 &lt;2.4.7) - Korrigerar problemet där en begränsad administratörsanvändare kan se CMS-sidor utanför sitt behörighetsområde.
* **ACSD-54472** (för Adobe Commerce >=2.4.6 &lt;2.4.7) - Korrigerar problemet där kunder i ett avvisat företag fortfarande kan autentisera och kunder i ett blockerat och avvisat företag fortfarande kan göra beställningar. Korrigeringen lägger till ytterligare validering för GraphQL-slutpunkter.
* **ACSD-52801** (för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.4.7) - Lägger till alternativet att göra en partiell matchning när du söker efter produkter i GraphQL.
* **ACSD-55004** (för Adobe Commerce och Magento Open Source >=2.4.6 &lt;2.4.7) - Korrigerar problemet där valideraren kraschar när en importfil som är större än det värde som konfigurerats i `php.ini` överförs.
* **ACSD-54989** (för Adobe Commerce >=2.4.4-p5 &lt;2.4.5) || >=2.4.5-p4 &lt;2.4.6 || >=2.4.6-p2 &lt;2.4.7) - Korrigerar problemet där en företagsadministratör inte kan göra en beställning när *[!UICONTROL Enable Purchase Orders]* är inställd på *[!UICONTROL Yes]* och *[!UICONTROL Purchase Order]* är inställd på *[!UICONTROL No]*.
* **ACSD-54007** (för Adobe Commerce och Magento Open Source >=2.4.0 &lt;2.4.7) - Korrigerar felet *&quot;Odefinierad matrisnyckel &quot;_scope&quot;&quot;* vid import av kunddata.
* **ACSD-55031** (för Adobe Commerce och Magento Open Source >=2.4.5 &lt;2.4.6) - Korrigerar felet *Type &quot;mixad&quot; kan inte vara null* vid kompilering.
* **ACSD-54961** (för Adobe Commerce och Magento Open Source >=2.4.0 &lt;2.4.7) - Korrigerar problemet där en begränsad administratörsanvändare inte kan uppdatera statusen för *produktgranskning*.
* **ACSD-55256** (för Adobe Commerce och Magento Open Source >=2.4.6 &lt;2.4.7) - Korrigerar problemet där endast den första bilden visas korrekt i bildreglaget.
* Uppdaterade patchar: ACSD-52041, ACSD-54106

## v1.1.39 {#v1-1-39}

* **ACSD-53704** (för Adobe Commerce >=2.4.0 &lt;2.4.7) - Korrigerar problemet där historiken för belöningspoängsaldo inte beräknas efter att belöningspoäng har förfallit.
* **ACSD-53583** (för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.4.7) - Förbättrar prestanda för partiell omindexering för *Kategoriprodukter* och *produktkategorier*.
* **ACSD-54026** (för Adobe Commerce >=2.4.6 &lt;2.4.7) - Korrigerar ett felaktigt felmeddelande för en `updateCompanyRole` GraphQL-begäran för en obehörig användare.
* **ACSD-54106** (för Adobe Commerce och Magento Open Source >=2.4.1 &lt;2.4.5) - Korrigerar problemet där produktsortering efter namn för turkiska accenttecken är felaktig.
* **ACSD-52219** (för Adobe Commerce och Magento Open Source >=2.4.5 &lt;2.4.7) - Korrigerar problemet där administratörsrutnät inte fungerar som väntat när du ofta växlar mellan bokmärkesvyer.
* **ACSD-54342** (för Adobe Commerce och Magento Open Source >=2.4.0 &lt;2.4.7) - Korrigerar ett felaktigt felmeddelande *Fel i datastrukturen: värdena blandas* vid import av en CSV-fil utan giltiga data.
* **ACSD-54660** (för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.4.6) - Ett nytt indataattribut har lagts till *sort* för att sortera kundorder i GraphQL efter `sort_field` och `sort_direction`.
* **ACSD-54776** (för Adobe Commerce >=2.4.5 &lt;2.4.7) - Korrigerar problemet där omarkerade *[!UICONTROL Use Default Value]* och icke-standardvärden för produktfält inte sparas för den andra webbplats-, butiks- och butiksvyn.
* **ACSD-53998** (för Adobe Commerce och Magento Open Source >=2.4.4-p2 &lt;2.4.5) || >=2.4.5-p1 &lt;2.4.7) - Korrigerar problemet där en **[!UICONTROL Dynamic Block]** baserad på en **[!UICONTROL Customer Segment]** inte fungerar korrekt efter utloggning från ett kundkonto.
* **ACSD-53204** (för Adobe Commerce och Magento Open Source >=2.4.6 &lt;2.4.7) - Korrigeringar *Produkten kan inte sparas.*-fel vid samtidig begäran om att lägga till bilder i produktgalleriet med slutpunkten `rest/V1/products/<sku>/media`.
* **ACSD-47657** (för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.4.7) - En cachelagringsmekanism för AWS-autentiseringsuppgifter har lagts till. En autentiseringsprovider använder nu cacheminnet i Magento för att cachelagra autentiseringsuppgifter som hämtats från AWS för EC2-konfiguration.
* Uppdaterade patchar: ACSD-51984, ACSD-51574.

## v1.1.38 {#v1-1-38}

* **ACSD-53098** (för Adobe Commerce och Magento Open Source >=2.4.3 &lt;2.4.4) - Korrigerar problemet där produkter som tilldelats till en delad katalog inte visas i butiken när ett partiellt index körs.
* **ACSD-54018** (för Adobe Commerce och Magento Open Source >=2.3.7 &lt;2.4.6) - Korrigerar prestandaproblemen med [!UICONTROL Product List]-widgeten som använder ett icke-globalt attribut i widgetvillkoret.
* **ACSD-54111** (för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.6) - Korrigerar problemet där produktminiatyrbilder inte visas på butiken när vattenstämpelbildens proportioner inte matchar produktbilden.
* **ACSD-47669** (för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.6) - Korrigerar *Överträdelse av integritetsbegränsning: 1452 Det går inte att lägga till eller uppdatera en underordnad rad: en sekundärnyckelbegränsning misslyckas* vid import av produkter från CSV.
* **ACSD-53347** (för Adobe Commerce och Magento Open Source >=2.3.7 &lt;2.4.7) - Korrigerar problemet där prisindexeraren tar för lång tid att köra.
* **ACSD-52287** (för Adobe Commerce >=2.3.7 &lt;2.4.7) - Korrigerar problemet med felaktig ordningsstatus i det arkiverade orderrutnätet när asynkron rutnätsindexering är aktiverat.
* **ACSD-52929** (för Adobe Commerce och Magento Open Source >=2.3.7 &lt;2.4.7) - Korrigerar problemet med redundanta begäranden om att indexera om standardkällobjekt när lagerindexeraren har konfigurerats i asynkront läge.
* **ACSD-53824** (för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.4.7) - Korrigerar problemet där `UpdateMultiselectAttributesBackendTypes` migreringsdatapappen överskrider storleksgränsen för databastransaktion under `setup:upgrade`.

## v1.1.37 {#v1-1-37}

* **ACSD-52613** (för Adobe Commerce och Magento Open Source >=2.4.6 &lt;2.4.7) - Korrigerar problemet där cacheminnen och index uppdateras även när inga uppdateringar görs av `Inventory_source` objekt via REST API.
* **ACSD-51884** (för Adobe Commerce och Magento Open Source >=2.3.7 &lt;2.4.7) - Korrigerar problemet där produktbildens cachesökväg blir felaktig efter att kommandot resize körts.
* **ACSD-53628** (för Adobe Commerce och Magento Open Source >=2.3.7 &lt;2.4.7) - Korrigerar problemet där CSV-försäljningsorderrapporten innehåller felaktiga specialtecken.
* **ACSD-53148** (för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.4.7) - Korrigerar problemet där två parallella begäranden i GraphQL om att lägga till samma konfigurerbara produkt i kundvagnen resulterade i två separata artiklar i varukorgen med samma produkt-SKU.
* **ACSD-52606** (för Adobe Commerce och Magento Open Source >=2.4.0 &lt;2.4.7) - Korrigerar problemet där felmeddelandet *Din beställning inte är klar för hämtning* visas när användaren klickar på **[!UICONTROL Notify Order is Ready for Pickup]**.
* **ACSD-51574** (för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.7) - Korrigerar ett fel där bilden inte uppdateras på frontend efter att den ersatts med en annan bild med samma namn.
* **ACSD-53728** (för Adobe Commerce och Magento Open Source >=2.3.7 &lt;2.4.7) - Korrigerar problemet där produktindexeraren tar längre tid att slutföra.
* **ACSD-53979** (för Adobe Commerce och Magento Open Source >=2.4.6 &lt;2.4.7) - Korrigerar JS-problemet som uppstår på hemsidan om välkomstmeddelandet innehåller ett enkelt citattecken.
* **ACSD-52085** (för Adobe Commerce och Magento Open Source >=2.4.5 &lt;2.4.7) - Korrigerar problemet där en konfigurerbar produkt med ett specialpris inte syns i produktens karusell.
* **ACSD-53795** (för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.7) - Korrigerar problemet med ogiltig datatyp i `indexer_update_all_views` cron-jobb.
* **ACSD-52143** (för Adobe Commerce och Magento Open Source >=2.4.6 &lt;2.4.7) - Korrigerar problemet där anpassade alternativ tas bort efter produktimport.
* **ACSD-53750** (för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.4.7) - Korrigerar felet *Bruten pipe eller stängd anslutning* vid omindexering av flertrådiga `catalog_product_price` .
* **ACSD-49843** (för Adobe Commerce och Magento Open Source >=2.3.7 &lt;2.4.0) || >=2.4.1 &lt;2.4.7) - Korrigerar problemet där länken vid produktnedladdning inte är tillgänglig efter att den beställda artikeln har fakturerats automatiskt med onlinebetalningsmetoden med inställningen **[!UICONTROL Payment Action]** = **[!UICONTROL Sale]** aktiverad.
* **ACSD-47054** (för Adobe Commerce >=2.4.2 &lt;2.4.6) - Korrigerar problemet där omindexering av förhandsgranskning körs om för alla butiker, vilket orsakar långsamhet.
* Lagt till nya versioner för ACSD-46541, ACSD-47079.
* ACSD-49970-v3 ersatt med ACSD-54095.

## v1.1.36 {#v1-1-36}

* **ACSD-53239** (för Adobe Commerce och Magento Open Source >=2.4.3 &lt; 2.4.6) - Korrigerar problemet där lagerindexeraren rensar alla cacheminnen i schemaläge för uppdatering.
* **ACSD-50887** (för Adobe Commerce och Magento Open Source >=2.4.0 &lt;2.4.7) - Korrigerar problemet där produktattributegenskapen *[!UICONTROL Use in Search Results Layered Navigation]* kan ställas in på *Yes* utan att alternativet *[!UICONTROL Use in search]* är inställt på *Yes* .
* **ACSD-51846** (för Adobe Commerce och Magento Open Source >=2.4.3-p2 &lt;2.4.6) - Korrigerar det *interna felet* som inträffar eftersom inte alla nivåer av REST API-nyttolast valideras.
* **ACSD-52906** (för Adobe Commerce >=2.3.7 &lt;2.4.7) - Korrigerar problemet där X-Magento-Vary-cookien inte är korrekt inställd för inloggade kunder som tillhör samma kundsegment, vilket orsakar felaktig cachelagring för vissa sidor.
* **ACSD-52736** (för Adobe Commerce och Magento Open Source >=2.3.7 &lt;2.4.6) - Korrigerar problemet där en *kundprisregel* som innehåller krav för konfigurerbar produktkvantitet inte fungerar som förväntat.
* **ACSD-47875** (för Adobe Commerce och Magento Open Source >=2.3.7 &lt;2.4.7) - Korrigerar problemet där administratörsanvändare inte kan lägga till en produkt i en kundvagn från Admin för ett visst butiksvy med lagerhantering.
* **ACSD-53176** (för Adobe Commerce >=2.3.7 &lt;2.4.5) - Korrigerar problemet där *Relaterad produktregel* med *är ett av* villkoren inte matchar produkter.
* **ACSD-51666** (för Adobe Commerce och Magento Open Source >=2.3.7 &lt;2.4.7) - Korrigerar felet *Sessionen har upphört. Logga in igen.* som inträffar när en kund försöker logga in.
* Nya versioner för MDVA-39305-v2 har lagts till.
* Uppdaterade krav för ACSD-19640.

## v1.1.35 {#v1-1-35}

* **ACSD-51899** (för Adobe Commerce och Magento Open Source >=2.4.0 &lt;2.4.7) - Korrigerar problemet där standardleveransadressen i utcheckningssteget fylls i automatiskt med en tidigare vald adress i butiken.
* **ACSD-52041** (för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.4.7) - Korrigerar problemet där felmeddelandet *[ERROR] [!DNL Page Builder] återgav i 5 sekunder utan att frigöra lås.* visas i Chrome webbläsare när innehåll som redigerats med [!DNL Page Builder] sparas.
* **ACSD-52095** (för Adobe Commerce och Magento Open Source >=2.3.7 &lt;2.4.6) - Korrigerar problemet där värdet `manage_stock` felaktigt angavs till 0 i CSV-filen efter produktexporten.
* **ACSD-51358** (för Adobe Commerce >=2.4.5 &lt;2.4.7) - Korrigerar problemet där borttagning av en schemalagd uppdatering utan slutdatum leder till att andra schemalagda uppdateringar för samma entitet tas bort.
* **ACSD-48070** (för Adobe Commerce >=2.3.7 &lt;2.4.7) - Korrigerar problemet där redigering av en schemalagd uppdatering utlöser ett undantag.
* **ACSD-51890** (för Adobe Commerce och Magento Open Source >=2.4.0 &lt;2.4.7) - Korrigerar problemet där [!UICONTROL Submit review]-knappen kan klickas flera gånger utan [!DNL Google reCAPTCHA] v3-validering.
* **ACSD-51984** (för Adobe Commerce >=2.4.5 &lt;2.4.7) - Korrigerar problemet där omarkerade *[!UICONTROL Use Default Value]* - och *[!UICONTROL non-default product field]* -värden inte sparas för den andra webbplatsen, butiken och butiksvyn.
* **ACSD-52398** (för Adobe Commerce och Magento Open Source >=2.4.0 &lt;2.4.7) - Korrigerar felet *Den begärda kvantiteten är inte tillgänglig* som inträffar när du försöker uppdatera kvantiteten för en paketerad produkt i vagnen på butiken.
* **ACSD-52786** (för Adobe Commerce och Magento Open Source >=2.4.5 &lt;2.4.6) - Korrigerar problemet där katalogregelvillkoret *SKU* gäller för alla produkter som börjar med angiven SKU.
* **ACSD-52921** (för Adobe Commerce och Magento Open Source >=2.4.5 &lt;2.4.7) - Korrigerar problemet när ett internt fel inträffar om kundvagnsinformation begärs från GraphQL när det finns en ej lagerförd konfigurerbar produkt i vagnen.
* **ACSD-51683** (för Adobe Commerce och Magento Open Source >=2.4.6 &lt;2.4.7) - Korrigerar problemet där ett anpassningsbart alternativ inte kan läggas till i kundvagnen med GraphQL.
* **ACSD-52133** (för Adobe Commerce och Magento Open Source >=2.4.6 &lt;2.4.7) - Korrigerar problemet där ett kundkonto inte kan sparas efter en uppgradering.
* **ACSD-52202** (för Adobe Commerce och Magento Open Source >=2.4.3 &lt;2.4.7) - Korrigerar problemet där den säljbara kvantiteten av standardlagret felaktigt ändras till 0 när ett icke-standardlager ändras till 0 kvantitet vid orderleverans.
* **ACSD-51265** (för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.7) - Korrigerar problemet med `catalog_product_price` omindexeringsprestanda när det finns för många paketerade produkter i systemet.
* **ACSD-52831** (för Adobe Commerce >=2.3.7 &lt;2.4.7) - Korrigerar problemet där kunder inte kan göra överlåtbara offertorder när [!DNL Google reCAPTCHA v3 Invisible] är aktiverat.
* **ACSD-51845** (för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.4.7) - Korrigerar problemet där efterföljande produkter med nivåpriser och olika attributuppsättningar inte kan uppdateras via asynkron REST API för bulk.
* **ACSD-52815** (för Adobe Commerce och Magento Open Source >=2.3.7 &lt;2.4.7) - Korrigerar problemet där indata för kvantitetsfältet för en icke-standardkälla endast stöder upp till 6 siffror, till skillnad från 8 för en standardresurs.
* **ACSD-51149** (för Adobe Commerce >=2.3.7 &lt;2.4.7) - Korrigerar problemet där schemalagd importExport med aktiverade katalogbehörigheter gör indexerare ogiltiga och sedan cachelagrar tömningar efter cron.
* **ACSD-50815** (för Adobe Commerce och Magento Open Source >=2.4.5 &lt;2.4.6) - Korrigerar problemet där decimalkvantitet för en enkel produkt inte kan användas för ett nytt produktalternativ.
* Uppdaterade versioner för ACSD-47803.
* Uppdaterad titel för ACSD-51892.
* Uppdaterat ACSD-51379.
* Uppdaterat ACSD-49970-v2.

## v1.1.34 {#v1-1-34}

* **ACSD-52277** (för Adobe Commerce och Magento Open Source >=2.4.0 &lt;2.4.7) - Korrigerar problemet där en administratörsanvändare inte omdirigeras korrekt efter att ha valt en butiksvy när en ny order skapas i Admin.
* **ACSD-50813** (för Adobe Commerce >=2.4.5 &lt;2.4.7) - Korrigerar problemet där Admin inte kunde lägga till paketerade produkter som innehöll ett snedstreck i SKU:n med funktionen [!UICONTROL Add Products by SKU] i administratörsordningen.
* **ACSD-51630** (för Adobe Commerce och Magento Open Source >=2.4.3 &lt;2.4.7) - Korrigerar problemet där ett stort antal systemmeddelanden gör att det går långsammare att hämta administratörssidor.
* **ACSD-51853** (för Adobe Commerce och Magento Open Source >=2.4.1 &lt;2.4.7) - Korrigerar problemet där kopierade textformat inte används när [!UICONTROL Page Builder] används.
* **ACSD-52160** (för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.4.7) - Korrigerar problemet där produktvalideringsresultatet mot kundprisregeln inte utvärderades korrekt baserat på regelvillkoret &#39;Om ett objekt hittas/INTE hittas i vagnen med alla/något av dessa villkor är sant&#39;.
* **ACSD-51636** (för Adobe Commerce >=2.4.5 &lt;2.4.7) - Korrigerar problemet där företagsadministratören inte kan lägga till nya användare från kundkontoavsnittet trots att de har alla nödvändiga roller och behörigheter.
* **ACSD-51739** (för Adobe Commerce >=2.4.6 &lt;2.4.7) - Korrigerar problemet där ett fel returneras när `structure_id` begärs i en CompanyTeam GraphQL-begäran.
* **ACSD-51857** (för Adobe Commerce och Magento Open Source >=2.4.0 &lt;2.4.7) - Korrigerar problemet där den långsamma prestandan för `aggregate_sales_report_bestsellers_data` cron-rapporten på stora sales_order- och `sales_order_item` databastabeller berodde på hur huvuddatafrågan skrevs.
* **ACSD-48448** (för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.7) - Korrigerar problemet där det uppstod ett konkurrensproblem under orderannulleringarna, vilket orsakar en dubblerad post i tabellen `inventory_reservation`.
* **ACSD-52689** (för Adobe Commerce och Magento Open Source >=2.4.3 &lt;2.4.6) - Korrigerar problemet där bilder inte kan överföras till Amazon S3-lagring med REST API.
* **B2B-2674** (för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.4.7) - Lägg till cachelagring i GraphQL-frågan 1customAttributeMetadata1.
* Nya versioner har lagts till för ACSD-44938.
* Ytterligare krav för ACSD-46988.

## v1.1.33 {#v1-1-33}

* **ACSD-50478** (för Adobe Commerce och Magento Open Source >=2.4.0 &lt;2.4.5) - Korrigerar databasåterställningskommandot för ett fall när DB-dumpen innehåller utlösare och ett *avgränsare* SQL-kommando.
* **ACSD-50512** (för Adobe Commerce >=2.4.5 &lt;2.4.7) - Korrigerar *Fel: Den hämtningsbara länken är inte relaterad till produkten. Kontrollera länken och försök igen.*-fel som inträffar när startdatumet för en hämtningsbar mellanlagringsuppdatering för produkten uppdateras.
* **ACSD-50949** (för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.7) - Korrigerar problemet där prisfiltret i den avancerade sökningen inte returnerar korrekta resultat när det används tillsammans med SKU-filtret.
* **ACSD-51645** (för Adobe Commerce och Magento Open Source >=2.4.6 &lt;2.4.7) - Korrigerar felet som uppstod när en ny kundprisregel sparades om tillägget `Magento_OfflineShipping` är inaktiverat.
* **ACSD-50895** (för Adobe Commerce >=2.4.5 &lt;2.4.7) - Korrigerar problemet där [!DNL Google Analytics] 3 GTM-taggar inte utlöses om [!DNL Google Analytics] 4 GTM inte har konfigurerats.
* **ACSD-51102** (för Adobe Commerce >=2.4.2 &lt;2.4.7) - Korrigerar problemet där en katalogregel som tillämpas på ett stort antal produkter inte indexeras korrekt när regeln aktiveras av en schemalagd uppdatering.
* **ACSD-50368** (för Adobe Commerce och Magento Open Source >= 2.4.3 &lt;2.4.5) - Korrigerar problemet där kundens `group_id` ignoreras när en kund skapas via Async REST API eller Async Bulk REST API.
* **ACSD-51497** (för Adobe Commerce och Magento Open Source >=2.3.7 &lt;2.4.0) || >= 2.4.1 &lt;2.4.7) - Korrigerar problemet där en kund inte kan sortera en katalogsida efter anpassat attribut i listrutetypen.
* **ACSD-51408** (för Adobe Commerce och Magento Open Source >=2.3.7 &lt; 2.4.7) - Korrigerar problemet där orderobjektets status felaktigt är inställd på *[!UICONTROL Backordered]*.
* **ACSD-51735** (för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.4.5) - Korrigerar problemet där orderobjektets status är felaktigt inställd på *[!UICONTROL Ordered]* när produktstocken är *0*.
* **ACSD-51792** (för Adobe Commerce och Magento Open Source >=2.4.5 &lt;2.4.6) - Korrigerar problemet där en sida inte har en inställningshändelse när [!DNL Google Tag Manager] 4 är aktiverat.
* **ACSD-51471** (för Adobe Commerce >=2.4.3 &lt;2.4.7) - Korrigerar problemet där en administratörsanvändare inte kan spara en schemalagd uppdatering för en paketerad produkt som använder en enkel produkt som själv har en schemalagd uppdatering.
* **ACSD-51700** (för Adobe Commerce och Magento Open Source >=2.4.3 &lt;2.4.7) - Korrigerar felet som inträffar när butiksvyer växlas på en nedladdningsbar produktredigeringssida i administratören.
* **ACSD-51120** (för Adobe Commerce >=2.3.7 &lt;2.4.3) - Korrigerar problemet där GraphQL GET begär cache inte rensas för CMS-sidor som innehåller CMS-block som uppdateras via en mellanlagringsuppdatering.
* **ACSD-51240** (för Adobe Commerce >=2.4.4 &lt;2.4.6) - Korrigerar problemet där den överförda filen saknas om registreringen görs via företagsregistreringsformuläret.
* **ACSD-51907** (för Adobe Commerce >=2.4.2 &lt;2.4.3) - Korrigerar problemet där en begränsad administratörsanvändare inte kan skapa en kreditnota med en återbetalning offline.
* **ACSD-52148** (för Adobe Commerce och Magento Open Source >=2.4.0 &lt;2.4.4) - Korrigerar problemet när [!DNL Google V3 reCAPTCHA] Admin-inloggningen misslyckas ibland.
* **ACSD-51431** (för Adobe Commerce och Magento Open Source >=2.3.7 &lt;2.4.7) - Korrigerar problemet där en indexerarstatus är *aktiv* även om det inte finns några nya poster i ändringsloggen.
* **ACSD-51892** (för Adobe Commerce och Magento Open Source >=2.4.6 &lt;2.4.7) - Korrigerar prestandaproblemet där konfigurationsfiler läses in flera gånger.
* ACSD-5114 har tagits bort.

## v1.1.32 {#v1-1-32}

* **ACSD-49628** (för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.7) - Korrigerar problemet där [!UICONTROL Page Builder's] flera fel förhindrar att administratören sparar en produkt utan innehållsbehörighet.
* **ACSD-51305** (för Adobe Commerce och Magento Open Source >=2.4.6 &lt;2.4.7) - Korrigerar ett fel där underordnade produkter som inte kan konfigureras som Stock inte är tillgängliga i GraphQL svar.
* **ACSD-50621** (för Adobe Commerce >=2.3.7 &lt;2.4.7) - Korrigerar problemet där [!UICONTROL Tier Prices] för olika webbplatser i den delade katalogen inte visas när du försöker redigera dem i en miljö med flera webbplatser.
* **ACSD-51041** (för Adobe Commerce och Magento Open Source >=2.3.7 &lt;2.4.0) || >=2.4.1 &lt;2.4.6) - Förbättrar prestanda för prisindexerare.
* **ACSD-51379** (för Adobe Commerce och Magento Open Source >=2.3.7 &lt;2.4.7) - Korrigerar problemet där ändringar som gjorts i sidtextinnehåll via [!UICONTROL Page Builder] inte sparas.
* **ACSD-49480** (för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.4.6) - Korrigerar problemet där endast en kundvagnsprisregel tillämpas på vagnen.
* **ACSD-51230** (för Adobe Commerce >=2.3.7 &lt;2.4.7) - Korrigerar problemet där presentkortskontot tas bort när en partiell återbetalning av en enkel produkt bearbetas från en order.
* **ACSD-51238** (för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.4.7) - Korrigerar problemet där lagerkällan tas bort när konfigurerbara produkter uppdateras och priset redigeras.
* **ACSD-50794** (för Adobe Commerce >=2.4.1 &lt;2.4.7) - Korrigerar problemet där presentmeddelandet eller presentationsinformationen inte uppdateras i databasen när den tas bort från GraphQL.
* **ACSD-51528** (för Adobe Commerce och Magento Open Source >=2.4.5 &lt;2.4.7) - Korrigerar problemet där kolumnen *x_requested_for* har null-värden i tabellen *sales_order*.
* **ACSD-50849** (för Adobe Commerce >=2.4.4 &lt;2.4.6) - Korrigerar problemet där en ny produkt läggs till i kategorin efter att cacheminnet rensats resulterar i en felmatchning av positioner och val för befintliga produkter.
* **ACSD-51294** (för Adobe Commerce och Magento Open Source >=2.4.5 &lt;2.4.7) - Korrigerar problemet där GTM/GA-pris, kvantitet, skatt, frakt och intäkter skickas som en sträng till [!DNL Google Analytics] och GTM.
* **ACSD-51204** (för Adobe Commerce och Magento Open Source >=2.4.3 &lt;2.4.7) - Korrigerar problemet där en helt såld produkt inte återgår i lager efter att en kreditnota har skapats.
* **ACSD-51291** (för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.4.4-p4 || >=2.4.5 &lt;2.4.5-p3) - Korrigerar problemet där en begränsad administratör med tillgång till en webbplats kan lägga till bilder/videor till produkten som tilldelats flera webbplatser.
* Nya versioner har lagts till för ACSD-50336.
* Ersatta patchar ACSD-49970.

## v1.1.31 {#v1-1-31}

* **ACSD-50345** (för Adobe Commerce och Magento Open Source >=2.4.3 &lt;2.4.4 || >=2.4.4-p1 &lt;2.4.6) - Korrigerar problemet där Recaptcha v2 inte laddas om efter att en misslyckad betalning har skickats.
* **ACSD-50817** (för Adobe Commerce och Magento Open Source >=2.3.7 &lt;2.4.7) - Optimerar Cron-jobbet `sales_clean_quotes` så att det körs snabbare.
* **ACSD-49392** (för Adobe Commerce och Magento Open Source >=2.3.7 &lt;2.4.0) || >= 2.4.1 &lt;2.4.7) - Korrigerar problemet där orderstatusen ändras till stängd efter en partiell återbetalning för en paketerad produkt.
* **ACSD-51036** (för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.4.5) - Korrigerar problemet där konkurrensvillkoren under samtidiga REST API-anrop leder till att leveransstatusinformationen i tabellen [!UICONTROL Items Ordered] skrivs över.
* **ACSD-50858** (för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.4.7) - Förbättrar prestanda för inläsning av bannerinnehåll.
* Lagt till nya versioner för MDVA-39305-v2, ACSD-45169.
* Uppdaterade patchar ACSD-50260-v2.

## v1.1.30 {#v1-1-30}

* **ACSD-50336** (för Adobe Commerce och Magento Open Source >=2.4.4-p1 &lt;2.4.4-p3) - Korrigerar problemet där produktvarningsmeddelanden inte skickas när en produkt finns i lager igen eller priset ändras.
* **ACSD-50367** (för Adobe Commerce och Magento Open Source >=2.3.7 &lt;2.4.7) - Korrigerar problemet där kundadressexport inte fungerar när ett flervalsattribut för kundadress utan värden skapas.
* **ACSD-49877** (för Adobe Commerce och Magento Open Source >=2.3.7 &lt;2.4.7) - Korrigerar problemet där automatisk uppspelning av video inte fungerar på mobilen [!DNL Safari] när videon är länkad direkt till en fjärrvideofil och inte till en direktuppspelningstjänst.
* **ACSD-50165** (för Adobe Commerce och Magento Open Source >=2.4.0 &lt;2.4.7) - Korrigerar felet *Det går inte att ta bort filen. Varning!unlink: Det finns ingen sådan fil eller katalog* när JS/CSS-cache tömdes från administratören.
* **ACSD-49737** (för Adobe Commerce och Magento Open Source >=2.4.1-p1 &lt;2.4.7) - Korrigerar problemet där en kupong felaktigt markerats som använd efter en misslyckad kortbetalning.
* **ACSD-50814** (för Adobe Commerce och Magento Open Source >=2.4.6 &lt;2.4.7) - Åtgärdar ett problem där en administratörsanvändare inte kan skapa en kreditnota.
* **ACSD-50116** (för Adobe Commerce och Magento Open Source >=2.3.7 &lt;2.4.7) - Korrigerar problemet där en administratörsanvändare inte kan skapa en URL-omskrivning för underkategorierna nivå 3 eller lägre.
* **ACSD-49513** (för Adobe Commerce och Magento Open Source >=2.4.3 &lt;2.4.5) - Korrigerar problemet där fjärrlagringssynkronisering misslyckas på grund av filer på 0 byte.
* **ACSD-46683** (för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.7) - Korrigerar problemet där leveranspriset visar *Inte beräknat än*.
* **ACSD-49129** (för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.6) - Korrigerar problemet där attributet *[!UICONTROL content]* (base64-bildkod) inte returneras i `rest/V1/products/sku/media` API-svar för produktmedia.
* **ACSD-50276** (för Adobe Commerce >=2.4.0 &lt;2.4.7) - Korrigerar problemet där kundregistreringsformuläret inte fungerar i butiken om ett kundattribut med flera val skapas.
* **ACSD-50527** (för Adobe Commerce >=2.3.7 &lt;2.4.7) - Korrigerar felet som inträffar när en sida sparas med ett tomt dynamiskt block.
* **ACSD-49973** (för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.4.5) - Förbättrar prestanda för hämtning av paketerade produkter via GraphQL.
* **ACSD-5114** (för Adobe Commerce och Magento Open Source >=2.4.3 &lt;2.4.7) - Korrigerar problemet där en slumpmässig produkt försvinner från stora kataloger när asynkron indexering är aktiverat. Förbättrar prestanda för asynkron omindexering för stora kataloger.
* **B2B-2598** (för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.4.7) - Lägg till cachelagring i [!UICONTROL availableStores] -, [!UICONTROL countries] -, [!UICONTROL country] -, [!UICONTROL currency] - och [!UICONTROL storeConfig] GraphQL-frågor.
* Lagt till nya versioner för MDVA-42806, ACSD-48627, ACSD-46815.
* Uppdaterade patchmetadata för ACSD-49773, ACSD-47179, ACSD-48300.

## v1.1.29 {#v1-1-29}

* **ACSD-49389** (för Adobe Commerce och Magento Open Source >=2.4.0 &lt;2.4.7) - Korrigerar problemet där ett e-postmeddelande som kan hämtas skickas av API när beställningen inte är klar för hämtning.
* **ACSD-49822** (för Adobe Commerce >=2.3.7 &lt;2.4.7) - Korrigerar problemet där uppdateringar på [!UICONTROL Requisition List] -sidan inte visas på [!UICONTROL Print Requisition List].
* **ACSD-48771** (för Adobe Commerce och Magento Open Source >=2.4.5 &lt;2.4.7) - Korrigerar problemet med uppgradering av kolumnblocksinnehållstypen från äldre [!DNL Page Builder]-versioner.
* **ACSD-49464** (för Adobe Commerce >=2.3.7 &lt;2.4.7) - Korrigerar problemet där fakturor, leveranser och kreditnotor inte flyttas tillbaka från arkivet när orderId är annorlunda.
* **ACSD-49773** (för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.6) - Korrigerar problemet där produktexporten misslyckas när AWS S3 används som fjärrlagring.
* **ACSD-49748** (för Adobe Commerce >=2.3.7 &lt;2.4.7) - Korrigerar problemet där inbjudningar inte kan skickas.
* **ACSD-49502** (för Adobe Commerce >=2.4.3 &lt;2.4.7) - Korrigerar problemet där den hämtningsbara länken inte uppdateras korrekt efter att en mellanlagringsuppdatering har tillämpats på den hämtningsbara produkten.
* **ACSD-49527** (för Adobe Commerce >=2.4.2 &lt;2.4.7) - Korrigerar problemet där GraphQL företagsroller inte visar sidnumreringen korrekt.
* **ACSD-49706** (för Adobe Commerce och Magento Open Source >=2.3.7 &lt;2.4.7) - Korrigerar problemet där standardvärdet sparas för ett visuellt färgruteattribut när inget värde har valts.
* **ACSD-49835** (för Adobe Commerce och Magento Open Source >=2.4.5 &lt;2.4.7) - Korrigerar problemet där kryssrutans standardvärde inte sparas korrekt på en arkivnivå för ett flervalsattribut.
* **ACSD-49898** (för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.4.6) - Korrigerar problemet där produktrutnätet genererar ett undantag när en paketerad produkt har ett specialpris som överstiger 1 000.
* **ACSD-50234** (för Adobe Commerce och Magento Open Source >=2.3.7 &lt;2.4.5) - Korrigerar problemet med fel kundnamn i bekräftelsemeddelandet om en beställning med [!DNL PayPal] görs.
* **ACSD-49960** (för Adobe Commerce och Magento Open Source >=2.4.5 &lt;2.4.7) - Korrigerar problemet där filtrering efter datum inte fungerar för kundorderrastret.
* **ACSD-49849** (för Adobe Commerce och Magento Open Source >=2.3.7 &lt;2.4.6) - Korrigerar problemet där kundens e-post ersattes med [!DNL PayPal] e-post när en beställning gjordes med [!DNL PayPal Express] via GraphQL.
* **ACSD-49839** (för Adobe Commerce >=2.3.7 &lt;2.4.7) - Korrigerar problemet där priser och struktur för delad katalog genererar ett fel i Admin när produkter har enkla eller dubbla citattecken i SKU.
* **ACSD-49970** (för Adobe Commerce och Magento Open Source >=2.4.5 &lt;2.4.7) - Korrigerar felaktig hantering av GraphQL-fel när [!DNL New Relic] -rapportering är aktiverad.
* **ACSD-50260** (för Adobe Commerce och Magento Open Source >=2.4.5 &lt;2.4.7) - Korrigerar problemet där GraphQL produktsökresultat begränsas till endast 10 000 resultat.
* **ACSD-48813** (för Adobe Commerce och Magento Open Source >=2.4.3 &lt;2.4.7) - Korrigerar problemet där sökningen inte visar relevanta resultat baserat på sökvikten för attributen.

## v1.1.28 {#v1-1-28}

* **ACSD-48204** (för Adobe Commerce och Magento Open Source >=2.3.7 &lt;2.4.3) - Korrigerar problemet där en katalogprisregel som skapats baserat på attributet Ja/Nej inte tar hänsyn till det valda omfånget.
* **ACSD-47704** (för Adobe Commerce och Magento Open Source >=2.3.7 &lt;2.4.7) - Korrigerar problemet där priset för den paketerade produkten endast visas för produkter i lager.
* **ACSD-49370** (för Adobe Commerce och Magento Open Source >=2.3.7 &lt;2.4.7) - Korrigerar problemet där produktattributet *Date Time* har en *FilterMatchTypeInput* -typ i GraphQL-schema.
* **ACSD-48807** (för Adobe Commerce och Magento Open Source >=2.4.1 &lt;2.4.7) - Korrigerar problemet där kundproduktrecensioner inte filtreras efter butiksgranskning via GraphQL.
* **ACSD-49433** (för Adobe Commerce och Magento Open Source >=2.4.3 &lt;2.4.7) - Korrigerar problemet där standardbeloppet visas som delsumma i kundvagnen för presentkort med ett öppet belopp.
* **ACSD-48866** (för Adobe Commerce och Magento Open Source >=2.3.7 &lt;2.4.7) - Korrigerar problemet där ett fel inträffar när RSS-feed begärs för kategorier.
* **ACSD-48784** (för Adobe Commerce och Magento Open Source >=2.3.7 &lt;2.4.7) - Korrigerar problemet där kundsegmentpriserna inte cachas korrekt mellan kundgrupper.
* **ACSD-48857** (för Adobe Commerce och Magento Open Source >=2.4.3 &lt;2.4.7) - Korrigerar problemet där en användare inte kan spara ändringar efter redigering med Page Builder.
* **ACSD-49065** (för Adobe Commerce och Magento Open Source >=2.3.7 &lt;2.4.7) - Korrigerar problemet där offertobjekt inte visas i Admin om de bara tilldelats det anpassade arkivet.
* **ACSD-49179** (för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.7) - Korrigerar problemet där orderrapporten visar felaktiga belopp för olika valutor för olika butiker.
* **ACSD-49286** (för Adobe Commerce och Magento Open Source >=2.4.3 &lt;2.4.7) - Korrigerar problemet där en produkt läggs till två gånger i en kundvagn när det finns flera produktwidgetar på sidan.
* **ACSD-49574** (för Adobe Commerce >=2.4.4 &lt;2.4.7) - Lägger till funktioner som stöder produktuppdateringar med presentkort i en kundvagn via GraphQL.
* Uppdaterad patch: ACSD-48694.

## v1.1.27 {#v1-1-27}

* **ACSD-48362** (för Adobe Commerce >=2.4.1 &lt;2.4.7) - Korrigerar problemet där standardleveransadressen används i stället för en ny när en order läggs med en överlåtbar offert.
* **ACSD-48059** (för Adobe Commerce >=2.3.7 &lt;2.4.7) - Korrigerar problemet där handlare inte kan spara [!UICONTROL Match product by rule] i kategorin.
* **ACSD-48216** (för Adobe Commerce och Magento Open Source >=2.3.7 &lt;2.3.8) || >=2.4.0 &lt;2.4.7) - Korrigerar problemet där [!UICONTROL AUTO_INCREMENT] för tabellen [!UICONTROL inventory_source_item] ökar åtgärden [!UICONTROL UPDATE].
* **ACSD-47908** (för Adobe Commerce och Magento Open Source >=2.3.7 &lt;2.3.8) || >=2.4.0 &lt;2.4.7) - Korrigerar felet &quot;Ett värde som är mindre än eller lika med 0 förväntas&quot; när källan och kvantiteten väljs i leveranssteget vid utcheckningen.
* **ACSD-49497** (för Adobe Commerce och Magento Open Source >=2.3.7 &lt;2.4.6) - Korrigerar problemet där en order förblir i bearbetningstillstånd efter leverans och en partiell återbetalning tillämpas.
* **ACSD-48694** (för Adobe Commerce och Magento Open Source >=2.3.7 &lt;2.3.8) || >=2.4.1 &lt;2.4.7) - Korrigerar problemet där felet&quot;Ogiltig tillståndsändring begärd&quot; förhindrar att en kund gör en beställning.
* **ACSD-49013** (för Adobe Commerce och Magento Open Source >=2.4.3 &lt;2.4.7) - Korrigerar problemet där e-postbekräftelse inte översätts till webbplatsens språkområde när du skapar kunder som använder satsvis-API.
* **ACSD-48164** (för Adobe Commerce och Magento Open Source >=2.3.7 &lt;2.4.7) - Korrigerar problemet där en begränsad administratör inte kan spara ett webbplatsnivåvärde.
* **ACSD-48404** (för Adobe Commerce och Magento Open Source >=2.4.0 &lt;2.4.4) - Korrigerar problemet där &quot;Kom ihåg kategorisidindelning = Ja&quot; orsakar ett fel när webbläsarens bakåtknapp trycks ned.
* **ACSD-48634** (för Adobe Commerce och Magento Open Source >=2.3.7 &lt;2.4.7) - Korrigerar JS-fel på en mellanlagringsuppdateringssida när [!UICONTROL Google Analytics Content Experiments] är aktiverat.
* **ACSD-49042** (för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.4.5) - Korrigerar problemet där en produkt med oändlig restorder inte kan beställas från Storefront.
* Uppdaterade patchar: ACSD-48366, ACSD-48661.

## v1.1.26 {#v1-1-26}

* **ACSD-47937** (för Adobe Commerce och Magento Open Source 2.4.4) || >=2.4.5 &lt;2.4.6) - Korrigerar problemet där meddelanden om prisfall inte alltid skickas på grund av cachelagring på programnivå.
* **ACSD-48661** (för Adobe Commerce och Magento Open Source >=2.3.7 &lt;2.4.7) - Korrigerar problemet där företagets kreditgräns är större än 99, där kommaavgränsaren förhindrar att företaget sparas på grund av ett valideringsfel.
* **ACSD-48773** (för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.7) - Korrigerar problemet där e-postmallen för belöningspoäng hämtas från fel butik.
* **ACSD-48587** (för Adobe Commerce och Magento Open Source >=2.3.7 &lt;2.4.7) - Korrigerar problemet där HTML-specialtecken i produktwidgetens matchningsregler förhindrar att de visar matchande produkter.
* **ACSD-48212** (för Adobe Commerce och Magento Open Source >=2.3.7 &lt;2.4.6) - Korrigerar problemet där produktimporten tilldelar produkten fel källa.
* **ACSD-47988** (för Adobe Commerce och Magento Open Source >=2.3.7 &lt;2.4.6) - Korrigerar problemet där produktexport trimmar HTML-taggar från produktbeskrivningen i Page Builder.
* **ACSD-48366** (för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.4.6) - Korrigerar problemet där produktbilden inte visas i e-postmallen Tillbaka till Stock.
* **ACSD-48417** (för Adobe Commerce och Magento Open Source >=2.4.5 &lt;2.4.7) - Korrigerar problemet där ett SQL-fel uppstår när en schemaändring för en produkt har skapats och en annan produkt har sparats.

## v1.1.25 {#v1-1-25}

* **ACSD-48058** (för Adobe Commerce och Magento Open Source >=2.4.5 &lt;2.4.6) - Korrigerar problemet där omindexering av produktpris inte fungerar om paketprodukten inte har tilldelats någon webbplats.
* **ACSD-48262** (för Adobe Commerce och Magento Open Source >=2.4.5 &lt;2.4.6) - Korrigerar problemet där produkter inte visas i förgrunden när inställningen Tillåt alla produkter per sida är inställd på Ja.
* **ACSD-48293** (för Adobe Commerce och Magento Open Source >=2.4.3 &lt;2.4.4) - Korrigerar problemet där de sammansatta produkterna hamnar utanför lagret när de underordnade produkter som sålts returneras till lagret.
* **ACSD-47520** (för Adobe Commerce och Magento Open Source >=2.4.0 &lt;2.4.6) - Korrigerar problemet där kunderna förlorar belöningspoäng när en kreditnota skapas.
* **ACSD-48044** (för Adobe Commerce och Magento Open Source >=2.4.0 &lt;2.4.4) - Korrigerar problemet där användning av flera presentkort på en enda order med flera leveranser förhindrar att beställningar görs.
* **ACSD-48300** (för Adobe Commerce och Magento Open Source >=2.4.0 &lt;2.4.6) - Korrigerar problemet där en retur inte kan skapas om den konfigurerbara produkten tas bort.
* **ACSD-47910** (för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.4.6) - Korrigerar problemet med saknade order, fakturor, leveranser och kreditnotor i respektive entitetsrutnät.
* **ACSD-47292** (för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.4.6) - Korrigerar problemet där paketerade produkter som inte finns i lager inte är tillgängliga i GraphQL-svaret om &quot;show out-of-stock products&quot; är inställd på Ja.
* **ACSD-48234** (för Adobe Commerce och Magento Open Source >=2.4.5 &lt;2.4.6) - Korrigerar problemet där katalogsökresultatet visar ett felaktigt antal kategoriobjekt när alternativet Visa ej i lager är aktiverat.
* **ACSD-48313** (för Adobe Commerce och Magento Open Source >=2.4.0 &lt;2.4.5) - Korrigerar problemet där kolumnen &quot;configurable_variations&quot; inte tolkas om attributvärdet innehåller kommatecken. Samma parsningsalgoritm används för &quot;additional_attributes.
* **ACSD-48627** (för Adobe Commerce och Magento Open Source >=2.4.5 &lt;2.4.6) - Korrigerar problemet där den konfigurerbara produkten som inte finns i lager orsakar ett fel när en GraphQL-begäran skickas för att få kundvagnsinformation.
* Uppdaterad patch: MDVA-39384.

## v1.1.24 {#v1-1-24}

* **ACSD-45168** (för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.6) - Korrigerar problemet där SEO-anpassade URL:er inte genereras för produkter som har *url_key* -attribut åsidosatta på butiksvisningsnivå.
* **ACSD-46865** (för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.4.6) - Korrigerar problemet där rutnätet för utleverans och kreditnota inte fylls i när asynkron indexering är aktiverat.
* **ACSD-47004** (för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.6) - Korrigerar problemet där moms inte tillämpas på en faktureringsadress utan moms-ID.
* **ACSD-47803** (för Adobe Commerce och Magento Open Source >=2.4.0 &lt;2.4.6) - Korrigerar problemet där ej lagrade konfigurerbara produktfärgrutor visas som tillgängliga.
* **ACSD-47137** (för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.4.6) - Förbättrar inläsningshastigheten för bildgalleriet när mappen pub/media är mycket stor.
* **ACSD-46770** (för Adobe Commerce och Magento Open Source >=2.4.0 &lt;2.4.6) - Korrigerar problemet där e-postmeddelanden med administratörsorder skickas även när *bekräftelsen av e-postorder* inte är markerad.
* **ACSD-47955** (för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.4.6) - Korrigerar problemet där GraphQL inte visar kundvagnsrabatten korrekt.
* **ACSD-46617** (för Adobe Commerce och Magento Open Source >=2.4.0 &lt;2.4.6) - Korrigerar problemet där knappen *Fortsätt till utcheckning* är nedtonad även om delsumman är större än det konfigurerade *minimiorderbeloppet*.
* **ACSD-47079** (för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.4.5) - Korrigerar problemet där sammansatta produkter (bundle, grouped och configurable) inte uppdateras när underproduktens lagerstatus ändras via REST API-POSTEN /rest/V1/lager/source-items.
* **ACSD-47336** (för Adobe Commerce och Magento Open Source >=2.4.0 &lt;2.4.6) - Korrigerar *Något gick fel.*-fel när meddelanden i Commerce Admin stängs av.
* **ACSD-47559** (för Adobe Commerce och Magento Open Source >=2.4.0 &lt;2.4.6) - Korrigerar problemet där e-postmallområdet för förhandsgranskning inte är helt synligt.
* **ACSD-47920** (för Adobe Commerce och Magento Open Source >=2.4.0 &lt;2.4.6) - Korrigerar problemet där beställningar kan göras via Rest API som gästanvändare även när *Tillåt gästutcheckning* är inaktiverat.
* Ersatta korrigeringsfiler: MDVA-39305, MDVA-42855.

## v1.1.23 {#v1-1-23}

* **ACSD-47179** (för Adobe Commerce och Magento Open Source >=2.4.0 &lt;2.4.6) - Korrigerar problemet där en administratör med begränsad åtkomst till ett specifikt omfång inte kan ta bort produktrecensioner.
* **ACSD-47107** (för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.5) - Korrigerar problemet där rabatten för katalogprisregel gäller för anpassade produktalternativ.
* **ACSD-47232** (för Adobe Commerce och Magento Open Source >=2.4.0 &lt;2.4.6) - Korrigerar problemet där kuponger med totalviktsvillkor inte kan användas i Admin.
* **ACSD-46519** (för Adobe Commerce och Magento Open Source >=2.4.1 &lt;2.4.6) - Korrigerar problemet där GraphQL categoryList-begäran returnerar ett felaktigt product_count för en ankarkategori.
* **ACSD-47027** (för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.6) - Korrigerar en långsam updateCompanyRole GraphQL-begäran.
* **ACSD-47666** (för Adobe Commerce och Magento Open Source >=2.4.0 &lt;2.4.6) - Korrigerar problemet där filterfunktionen inte fungerar i Admin > System > Behörigheter > Användarroller > en roll > Rutnät för rollanvändare.
* **ACSD-47497** (för Adobe Commerce och Magento Open Source >=2.4.0 &lt;2.4.6) - Korrigerar problemet där fliken Tjänster inte visas i konfigurationen under Admin.
* Uppdaterad patch: ACSD-47743.
* Ersatta korrigeringsfiler: MDVA-42807.

## v1.1.22 {#v1-1-22}

* **ACSD-47444** (för Adobe Commerce och Magento Open Source >=2.4.0 &lt;2.4.3) - Korrigerar _Försök att få åtkomst till matrisförskjutning för typbool_ -fel vid åtkomst till vissa kategorisökvägar som inte finns för kända produkter i PHP 7.4.
* **ACSD-47332** (för Adobe Commerce och Magento Open Source >=2.4.0 &lt;2.4.6) - Korrigerar problemet där kron misslyckas med ett fel som bara rapporteras när den körs mellan 00:00 och 00:59 UTC.
* **ACSD-47280** (för Adobe Commerce och Magento Open Source >=2.4.0 &lt;2.4.6) - Korrigerar problemet där inaktiveringen av den delade katalogfunktionen i ett specifikt omfång inte fungerar korrekt.
* **ACSD-47106** (för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.4.6) - Korrigerar problemet där ett värde inte kan sparas i ett nytt anpassat attribut på en företagsskapandesida.
* Uppdaterad patch: ACSD-45143.

## v1.1.21 {#v1-1-21}

* **ACSD-46809** (för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.6) - Korrigerar problemet där en användare får ett fel när ett stort antal produktkällor tilldelas.
* **ACSD-46856** (för Adobe Commerce och Magento Open Source >=2.4.0 &lt;2.4.6) - Förbättrar prestanda genom att uppdatera nivåpriser via System > Konfiguration > Importera > Avancerade priser.
* **ACSD-46541** (för Adobe Commerce och Magento Open Source >=2.4.0 &lt;2.4.4) - Korrigerar problemet där en administratörsanvändare inte kan skapa en kreditnota om ett orderobjekt tas bort.
* **ACSD-46581** (för Adobe Commerce och Magento Open Source >=2.4.0 &lt;2.4.6) - Korrigerar problemet där den beräknade momssumman inte uppdateras efter att ett land har valts i kundvagnen.
* **ACSD-46618** (för Adobe Commerce och Magento Open Source >=2.4.0 &lt;2.4.6) - Korrigerar problemet där produktlistwidgeten visar felaktiga cachelagrade priser för en inloggad kund.
* **ACSD-46674** (för Adobe Commerce och Magento Open Source >=2.4.0 &lt;2.4.6) - Korrigerar problemet där anpassade alternativ för en bildtyp visas som HTML i kundens e-postmeddelanden.
* **ACSD-46988** (för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.4.6) - Korrigerar problemet där GraphQL &#39;currency&#39; API-begäran returnerar NULL-värden för en anpassad valuta.
* **ACSD-47076** (för Adobe Commerce och Magento Open Source >=2.4.1 &lt;2.4.5) - Korrigerar problemet där Vimeo-videor inte kan spelas upp i butiken.
* **ACSD-45071** (för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.4) - Korrigerar problemet där standardkällan läggs till i produkten under importen.
* **AC-3023** (för Adobe Commerce och Magento Open Source >=2.4.0 &lt;2.4.6) - Uppdatera DHL-schemat till den senaste versionen, 10.0.
* Uppdaterade patchar: MDVA-42584.
* Ersatta korrigeringsfiler: MDVA-36572, ACSD-45241.

## v1.1.20 {#v1-1-20}

* **ACSD-46520** (*för Adobe Commerce och Magento Open Source >=2.4.0 &lt;2.4.5*) - Korrigerar problemet där en användare får en felaktig orderstatus när de återbetalas med butikskrediten.
* **ACSD-46703** (*för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.4.6*) - Korrigerar problemet där det inte går att dra och släppa anpassade alternativ på en produktredigeringssida.
* **ACSD-44851** (*för Adobe Commerce och Magento Open Source >=2.4.0 &lt;2.4.6*) - Korrigerar problemet där en kategori med underkategorier inte kan öppnas eller expanderas.
* **ACSD-46815** (*för Adobe Commerce och Magento Open Source >=2.4.5 &lt;2.4.6*) - Korrigerar problemet där kategoriträdsbegäran är begränsad till 20 kategorier.
* **ACSD-45675** (*för Adobe Commerce och Magento Open Source >=2.4.0 &lt;2.4.6*) - Korrigerar problemet där produktexporten använder kategorinamn från *standardbutiksvyn* .
* **ACSD-46869** (*för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.4.6*) - Korrigerar problemet där en konfigurerbar produkt i en kundvagn inte uppdateras via en *PUT REST API* -begäran utan att produktkvantiteten ändras.
* **MDVA-42768-V2** (*för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.3*) - Korrigerar problemet där den konfigurerbara produkten visar det reguljära priset som *0* när *Visa slut-på-Stock* är *Ja*.
* Uppdaterade patchar: MDVA-44562, ACSD-46213, MDVA-41305, MDVA-38346, MDVA-13203.
* Borttagen patch: MDVA-42768.

## v1.1.19 {#v1-1-19}

* **ACSD-46213** (*för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.3*) - Korrigerar problemet där kategoriträdsbegäran är begränsad till 20 kategorier.
* **ACSD-45781** (*för Adobe Commerce och Magento Open Source >=2.4.1 &lt;2.4.2*) - Korrigerar problemet där sökfältet för butiksskylt inte visas på mobilen.
* **ACSD-46192** (*för Adobe Commerce och Magento Open Source >=2.3.6 &lt;2.4.5*) - Korrigerar problemet med att använda slutpunkten `async/bulk/V1/configurable-products/bySku/options`.
* **ACSD-46404** (*för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.4.5*) - Korrigerar problemet där en administratörsanvändare inte kan logga in efter uppgradering till 2.4.4.
* Uppdaterade patchar: MDVA-41305, MDVA-38626, MDVA-38728, MDVA-41061-V4, MDVA-42269, MDVA-39305.

## v1.1.18 {#v1-1-18}

* **ACSD-45817** (*för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.4*) - Korrigerar problemet där en GraphQL-produktmutation för en viss butik returnerar alla konfigurerbara varianter, inklusive de som inte tilldelats den begärda butiken.
* **ACSD-46146** (*för Adobe Commerce och Magento Open Source >=2.3.0 &lt;2.4.6*) - Korrigerar problemet där två orderbekräftelsemeddelanden skickas efter att en beställning från administratören har gjorts.
* **ACSD-45255** (*för Adobe Commerce >=2.4.3 &lt;2.4.6*) - Korrigerar ett undantag på rapportsidan LågStock för en begränsad administratörsanvändare.
* **ACSD-45488** (*för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.6*) - Korrigerar problemet där en konfigurerbar produkt med flera källor inte returneras till In Stock automatiskt.
* **ACSD-45754** (*för Adobe Commerce och Magento Open Source >=2.3.1 &lt;2.4.6*) - Korrigerar problemet där belöningspunkter inte läggs till efter att en kupong har använts i kundvagnen.
* **ACSD-45849** (*för Adobe Commerce >=2.4.3 &lt;2.4.4*) - Korrigerar problemet där videometadata förloras efter att en mellanlagringsuppdatering har tillämpats.
* **ACSD-45257** (*för Adobe Commerce och Magento Open Source >=2.3.4 &lt;2.4.4*) - Korrigerar problemet där GraphQL inte visar en kundvagnsrabatt korrekt.
* **ACSD-44938** (*för Adobe Commerce och Magento Open Source >=2.4.0 &lt;2.4.4*) - Korrigerar problemet där `VAT_ID` inte kan tillämpas i en GraphQL-begäran för en gästanvändare.
* Uppdaterade patchar: MDVA-43417.

## v1.1.17 {#v1-1-17}

* **ACSD-45241** (*för Adobe Commerce och Magento Open Source >=2.3.5 &lt;2.4.4*) - Korrigerar problemet där lagerkvantiteten för en virtuell produkt inte beräknas efter att en kreditnota har skapats.
* **ACSD-43887** (*för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.5*) - Korrigerar problemet där felaktig information visas på betalningssidan i kassan när inköpsorder för företag är aktiverade.
* **ACSD-45143** (*för Adobe Commerce och Magento Open Source >=2.4.0 &lt;2.4.5*) - Korrigerar problemet där `setShippingAddressesOnCart`-mutationen inte tillåter att numerisk regionkod anges som *region*.
* **ACSD-44591** (*för Adobe Commerce och Magento Open Source >=2.4.3 &lt;2.4.6*) - Korrigerar felet som inträffar när en order placeras utan CAPTCHA-bekräftelse.
* **ACSD-45520** (*för Adobe Commerce och Magento Open Source >=2.3.0 &lt;2.4.6*) - Korrigerar problemet där färgrutealternativ inte är förmarkerade på produktinformationssidan när en användare redigerar konfigurerbara produkter från kundvagnen.
* **ACSD-45169** (*för Adobe Commerce och Magento Open Source >=2.4.1 &lt;2.4.6*) - Korrigerar ett fel där [!DNL Visual Merchandiser] inte visar rätt lager och pris för en konfigurerbar produkt efter att en mellanlagringsuppdatering har tillämpats.
* **ACSD-45424** (*för Adobe Commerce och Magento Open Source >=2.3.4 &lt;2.4.6*) - Korrigerar problemet där en felaktig reservationskompensation skapas efter en partiell återbetalning (kreditnota).
* **MDVA-42807** (*för Adobe Commerce och Magento Open Source >=2.3.1 &lt;2.4.6*) - Korrigerar problemet där den anpassade valutasymbolen inte visas på butikssidan.
* Uppdaterade patchar: MDVA-42689, AC-3022.

## v1.1.16 {#v1-1-16}

* **MDVA-44703** (*för Adobe Commerce och Magento Open Source >=2.4.3 &lt;2.4.4*) - Korrigerar problemet där ordersummor i Orders-rapporten inte beräknas korrekt för den begränsade administratörsanvändaren.
* **MDVA-44940** (*för Adobe Commerce och Magento Open Source >=2.4.3 &lt;2.4.4*) - Korrigerar SQL-felet som inträffar när kategorin sparas från Admin.
* **MDVA-44562** (*för Adobe Commerce och Magento Open Source >=2.4.0 &lt;2.4.2-p2*) - Korrigerar problemet där det icke-förvalda arkiv-ID:t för offertobjekt åsidosätts av standardarkiv-ID:t, trots GraphQL-begäran som kommer från den icke-standardbutiksvyn.
* **MDVA-43167** (*för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.4*) - Korrigerar problemet där massåtgärden för administratörsorderraster inte gäller för flersidiga dokument när administratören väljer alla order.
* **MDVA-44044** (*för Adobe Commerce och Magento Open Source >=2.3.0 &lt;2.4.2-p2*) - Korrigerar problemet där en produkt inte visas på kategorisidan efter att den har tilldelats till en ny webbplats.
* **MDVA-42509** (*för Adobe Commerce och Magento Open Source >=2.3.3 &lt;2.4.4*) - Korrigerar problemet där en CSV inte kunde överföras för en snabborder som resulterade i ett *Det går inte att skicka cookie*-fel.
* Uppdaterade patchar: MDVA-41061, MDVA-42584.
* Prefixet för de nya [!DNL Quality Patches Tool] korrigeringarna ändras från *MDVA* till *ACSD* på grund av interna processändringar.

## v1.1.15 {#v1-1-15}

* **MDVA-40961** (*för Adobe Commerce och Magento Open Source >=2.4.3 &lt;2.4.4*) - Korrigerar problemet där en ytterligare artikel inte kan läggas till i vagnen när den minsta kvantiteten av artikeln redan finns i vagnen.
* **MDVA-44887** (*för Adobe Commerce och Magento Open Source >=2.4.4 &lt;2.4.5*) - Korrigerar det *ej infångade SyntaxError: Oväntat token &#39;const&#39;*-fel i Admin-panelen.
* **MDVA-43718** (*för Adobe Commerce och Magento Open Source >=2.3.0 &lt;2.4.5*) - Korrigeringar *Konsumenten har inte behörighet att komma åt %resources.*-fel som visas vid åtkomst till en delad katalog från en anpassad integrering.
* **MDVA-44660** (*för Adobe Commerce och Magento Open Source >=2.4.2-p1 &lt;2.4.5*) - Korrigerar problemet där det grav accenttecknet ``` ` ``` inte kunde användas för en kunds för- och efternamn.
* **MDVA-40896** (*för Adobe Commerce och Magento Open Source >=2.4.3 &lt;2.4.4*) - Korrigerar *Error: TypeError: Argument 3 som skickades till Magento* i asynkront produktbulk-API.
* **MDVA-38559** (*för Adobe Commerce och Magento Open Source >=2.4.0 &lt;2.4.3*) - Korrigerar */V1/customers/search API* -felet för kunder med mer än en prenumeration.
* **MDVA-44533** (*för Adobe Commerce och Magento Open Source >=2.3.1 &lt;2.4.4*) - Korrigerar problemet där rabatten felaktigt tillämpas på en underordnad paketprodukt.
* Uppdaterade patchar: MDVA-41061, MDVA-42269.

## v1.1.14 {#v1-1-14}

* **MDVA-43983** (*för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.5*) - Korrigerar problemet där produkter *inte visas individuellt* fortfarande visas i katalogernas avancerade sökresultat.
* **MDVA-44100** (*för Adobe Commerce och Magento Open Source >=2.4.3 &lt;2.4.5*) - Korrigerar problemet där alla FPT-filer har tilldelats den sista produkten i kundvagnen och återställts för andra produkter.
* **MDVA-43605** (*för Adobe Commerce och Magento Open Source >=2.3.1 &lt;2.4.5*) - Korrigerar problemet där orderdata returnerar negativa värden för radsummor när Rest API används.
* **MDVA-43102** (*för Adobe Commerce och Magento Open Source >=2.3.1 &lt;2.4.5*) - Korrigerar problemet där den försäljningsbara kvantiteten inte uppdateras korrekt när en återbetalning görs via REST API.
* **MDVA-43178** (*för Adobe Commerce och Magento Open Source >=2.4.3-p2 &lt;2.4.5*) - Korrigerar problemet där en kundtoken för en anpassad butik inte kan hämtas i GraphQL.
* **MDVA-43859** (*för Adobe Commerce och Magento Open Source >=2.4.1 &lt;2.4.5*) - Korrigerar problemet där felet *Ingen sådan entitet med customerId =* loggas när en borttagen kund försöker logga in.
* **MDVA-44147** (*för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.5*) - Korrigerar problemet där en GraphQL-begäran inte returnerar rekvisitionslistor.
* **MDVA-44505** (*för Adobe Commerce och Magento Open Source >=2.4.1 &lt;2.4.3*) - Korrigerar de problem där GraphQL Applying Reward Points inte uppdaterar Totalsumma och där butikskrediter tillämpas flera gånger under orderplaceringen.
* Uppdaterade patchar: MDVA-29148, MDVA-36464-V5, MDVA-42584, MDVA-39993-V2.

## v1.1.13 {#v1-1-13}

* **MDVA-42969** (*för Adobe Commerce och Magento Open Source >=2.4.1 &lt;2.4.3*) - Korrigerar problemet där regeln för relaterade produkter endast fungerar när kundsegmentet är inställt på *Alla*.
* **MDVA-39605** (*för Adobe Commerce och Magento Open Source >=2.3.4 &lt;2.4.5*) - Korrigerar problemet där Redis cache TTL (förfallodatum) har ett felaktigt värde.
* **MDVA-43862** (*för Adobe Commerce och Magento Open Source >=2.3.3 &lt;2.4.5*) - Korrigerar problemet där kunden inte kan uppdatera kundvagnsobjekt på grund av ett GraphQL *UpdateCartItems-mutationsfel*.
* **MDVA-43824** (*för Adobe Commerce och Magento Open Source >=2.3.6 &lt;=2.3.7-p3 || >=2.4.1 &lt;2.4.5*) - Korrigerar problemet där ett fel uppstår när du annullerar order med rabatt.
* **MDVA-43451** (*för Adobe Commerce och Magento Open Source >=2.4.3 &lt;2.4.5*) - Korrigerar problemet där felet *Det begärda arkivet inte hittades. Kontrollera butiken och försök igen.* visas när en delad katalog konfigureras för en viss webbplats.
* **MDVA-43491** (*för Adobe Commerce och Magento Open Source >=2.3.5 &lt;2.4.5*) - Korrigerar ett fel där basbildetiketten inte uppdateras vid import av produkter till en webbplats för flera butiker.
* **MDVA-43601** (*för Adobe Commerce och Magento Open Source >=2.3.0 &lt;2.4.5*) - Korrigerar problemet med saknade utlösare efter fullständig omindexering.
* **MDVA-42046** (*för Adobe Commerce och Magento Open Source >=2.3.4 &lt;=2.3.5-p2 || >=2.4.0 &lt;2.4.5*) - Korrigerar problemet där ett felaktigt värde tilldelas till ett produktattribut med ett datuminmatningsfält när en produkt uppdateras.
* **MDVA-43935** (*för Adobe Commerce och Magento Open Source >=2.4.1 &lt;2.4.5*) - Korrigerar problemet där merförsäljning visas två gånger.
* **MDVA-44188** (*för Adobe Commerce och Magento Open Source >=2.4.3 &lt;2.4.5*) - Korrigerar problemet där systemutfärdade e-postmeddelanden med `.-` i adresser inte skickas.
* **MDVA-42283** (*för Adobe Commerce och Magento Open Source >=2.3.0 &lt;2.4.5*) - Korrigerar problemet där datum- och tidsformatet i administratörsordningens rutnät för den franska språkinställningen är ogiltigt.
* Uppdaterade patchar: MDVA-41061-V2, MDVA-36309, MDVA-30862, MDVA-39713.
* Lagt till metadata för korrigeringsfiler för [!DNL Site-Wide Analysis Tool].

## v1.1.12 {#v1-1-12}

* **MDVA-39713** (*för Adobe Commerce och Magento Open Source >=2.3.0 &lt;2.3.6*) - Korrigerar problemet där användaren kan redigera starttiden för en aktiv schemalagd uppdatering.
* **MDVA-42410** (*för Adobe Commerce och Magento Open Source >=2.3.0 &lt;2.4.5*) - Korrigerar problemet där kupongrapporter endast visar standardbasvalutan.
* **MDVA-41136** (*för Adobe Commerce och Magento Open Source >=2.3.0 &lt;2.4.5*) - Korrigerar problemet där utgångsdatumet för `mage-cache-sessid` inte förlängs, vilket resulterar i rensning av kunddata.
* **MDVA-39993** (*för Adobe Commerce och Magento Open Source >=2.3.5 &lt;=2.3.7-p2 || >=2.4.0 &lt;2.4.4*) - Korrigerar problemet där lagerändringar som gjorts med API inte återspeglas på produktsidan i klientdelen.
* **MDVA-42855** (*för Adobe Commerce och Magento Open Source >=2.4.3 &lt;2.4.5*) - Korrigerar problemet där en ny kundadress inte sparas i adressboken under utcheckningen.
* **MDVA-42645** (*för Adobe Commerce och Magento Open Source >=2.4.3 &lt;2.4.5*) - Korrigerar problemet där administratören inte kan återbetala belöningspoäng om butikskreditfunktionen är inaktiverad.
* **MDVA-43414** (*för Adobe Commerce och Magento Open Source >=2.3.6 &lt;=2.3.7-p2*) - Korrigerar det allvarliga PHP-felet som inträffar när `inventory.reservations.updateSalabilityStatus` -kökonsumenten körs på numeriska SKU:er.
* **MDVA-41628** (*för Adobe Commerce och Magento Open Source >=2.4.0 &lt;2.4.5*) - Korrigerar problemet där befintliga begränsade administratörsanvändare får åtkomst till de nya resurserna när nya moduler läggs till.
* **MDVA-43348** (*för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.5*) - Korrigerar problemet där en GraphQL-begäran om presentkort visar ett fel om `gift_card_options` innehåller *uid*.
* **MDVA-39546** (*för Adobe Commerce och Magento Open Source >=2.3.0 &lt;2.4.5*) - Korrigerar problemet där startdatumet för mellanlagringsuppdateringen kan anges till ett tidigare datum än det aktuella datumet under redigeringen.
* **MDVA-42950** (*för Adobe Commerce och Magento Open Source >=2.3.0 &lt;2.4.5*) - Korrigerar problemet där videoklipp inte spelas upp på produktsidan.
* **MDVA-42689** (*för Adobe Commerce och Magento Open Source >=2.3.0 &lt;2.4.4*) - Korrigerar ett fel där Adobe Commerce genererar ett *integritetsbegränsningsfel* när produktkategorier uppdateras under importen.
* **MDVA-41229** (*för Adobe Commerce och Magento Open Source >=2.3.0 &lt;2.4.5*) - Korrigerar ett fel där bilder som finns på backend inte visas på klientsidan efter konfigureringsbar produktimport.
* **MDVA-43731** (*för Adobe Commerce och Magento Open Source >=2.4.3 &lt;2.4.4*) - Korrigerar ett problem där *Söksynonymer* inte längre fungerar när värdet läggs till i *Minimivillkor som ska matchas*.
* **MDVA-43232** (*för Adobe Commerce och Magento Open Source >=2.3.4 &lt;2.4.5*) - Korrigerar problemet där sortering av produkter i [!DNL Visual Merchandiser] efter specialpris till nederkant/överkant orsakar ett fel när kategorin sparas.
* **MDVA-43726** (*för Adobe Commerce och Magento Open Source >=2.3.3 &lt;2.4.3*) - Korrigerar problemet där katalogprisregeln som baseras på butiksattributsmatchning inte kan tillämpas efter partiell omindexering.
* Uppdaterade patchar: MDVA-36464, MDVA-37478, MDVA-38608.
* Lagt till metadata för korrigeringsfiler för [!DNL Site-Wide Analysis Tool].

## v1.1.11 {#v1-1-11}

* **MDVA-42790** (*för Adobe Commerce och Magento Open Source >=2.4.3 &lt;2.4.5*) - Korrigerar problemet där produktprisattribut inte kan uppdateras för en specifik webbplats via REST API.
* **MDVA-41350** (*för Adobe Commerce och Magento Open Source >=2.3.0 &lt;2.4.5*) - Korrigerar problemet där ett undantag inträffar när en administratörsanvändare med begränsad åtkomst lägger till en produkt utanför sitt rollomfång av SKU i en ordning.
* **MDVA-42269** (*för Adobe Commerce och Magento Open Source >=2.4.3-p1 &lt;2.4.5*) - Korrigerar problemet där en administratörsanvändare inte kan logga in i administratören på grund av *TypeError: strtotime() förväntar att parameter 1 ska vara sträng, null angivet*-fel.
* **MDVA-40830** (*för Adobe Commerce och Magento Open Source >=2.3.0 &lt;2.4.5*) - Korrigerar problemet där butikskrediten tillämpas flera gånger under orderplacering.
* **MDVA-42237** (*för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.5*) - Korrigerar problemet där ett specialpris för en konfigurerbar produkt inte uppdateras efter ändringar i dess underproduktspris.
* **MDVA-42520** (*för Adobe Commerce och Magento Open Source >=2.4.3 &lt;2.4.4*) - Korrigerar problemet där momssatsen tillämpas två gånger om *Aktivera gränsöverskridande handel* används.
* Uppdaterade patchar: MDVA-27239, MDVA-39305, MDVA-41236, MDVA-36832.
* Borttagen patch: MDVA-37725.

## v1.1.10 {#v1-1-10}

* **MDVA-38728** (*för Adobe Commerce och Magento Open Source >=2.3.2 &lt;2.4.5*) - Korrigerar problemet där massattributsuppdatering skapar URL-omskrivning för standardlagring endast efter ändring av *Produktsynlighet*.
* **MDVA-43091** (*för Adobe Commerce och Magento Open Source >=2.4.3 &lt;2.4.4*) - Korrigerar problemet där beställning av en paketprodukt från administratören i serverdelen ger felet *Du kan inte använda decimalkvantitet för den här produkten*.
* **MDVA-40816** (*för Adobe Commerce och Magento Open Source >=2.3.0 &lt;2.4.5*) - Korrigerar problemet där relaterade produktregler visar produkter från kategorier som inte definierats i regelvillkoren.
* **MDVA-41305** (*för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.5*) - Korrigerar problemet där GraphQL-mutation inte returnerar konfigurerbara produktalternativ efter att den har lagts till i önskelistan.
* **MDVA-39181** (*för Adobe Commerce och Magento Open Source >=2.4.1 &lt;2.4.5*) - Korrigerar problemet där relaterade produktregler visar produkter från kategorier som inte definierats i regelvillkoren.
* **MDVA-42584** (*för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.3*) - Korrigerar ett problem där konfigurerbar lagerstatus i serverdelen inte uppdateras efter att kvant- och lagerstatus har ändrats via Import eller API.
* **MDVA-40175** (*för Adobe Commerce och Magento Open Source >=2.4.0 &lt;2.4.3*) - Korrigerar ett problem där *Klicka för att ändra leveransmetod* inte visar alternativknappar för att välja leveransmetoder i administratören under omsorteringen.
* **MDVA-42768** (*för Adobe Commerce och Magento Open Source >=2.3.4 &lt;2.4.5*) - Korrigerar problemet där det konfigurerbara priset visas som 0 när *Visa ej i lager* är Ja.
* **MDVA-43201** (*för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.4*) - Korrigerar problemet när ett fel inträffar i kundinloggningen när DOB-attribut används med vissa språkområden.
* Uppdaterade patchar: MDVA-35092, MDVA-33970.

## v1.1.9 {#v1-1-9}

* **MDVA-38346** (*för Adobe Commerce och Magento Open Source >=2.3.0 &lt;2.4.5*) - Korrigerar problemet där datumfilter inte fungerar korrekt när Adobe Commerce tidszon inte är samma som den lokala miljöns tidszon.
* **MDVA-42657** (*för Adobe Commerce och Magento Open Source >=2.4.1 &lt;2.4.5*) - Korrigerar problemet där administratörsanvändaren inte kan välja kategorier under kundsegmentsvillkoren.
* **MDVA-42806** (*för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.4*) - Korrigerar problemet där ett *nytt företagsregistreringsmeddelande* skickas varje gång ett befintligt företag uppdateras via REST API.
* **MDVA-37984** (*för Adobe Commerce och Magento Open Source >=2.4.1 &lt;2.4.5*) - Korrigerar problemet där funktionen [!DNL Visual Merchandiser] *Matcha produkten efter regel* inte filtrerar produkter med mellanlagringsuppdateringar korrekt.
* **MDVA-40488** (*för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.4*) - Korrigerar problemet där konfigurerbara produkter med underordnade produkter utanför lagret inte visas i rätt prisintervall.
* **MDVA-42507** (*för Adobe Commerce och Magento Open Source >=2.4.3 &lt;2.4.5*) - Korrigerar det problem där helsidescachen rensas efter att en mellanlagringsuppdatering har tillämpats för kundvagnsregeln.
* **MDVA-39163** (*för Adobe Commerce och Magento Open Source >=2.3.5 &lt;2.4.5*) - Korrigerar problemet där leveransmetoder inte är tillgängliga när en ny användare registreras och produkter i kundvagnen kommer från gästsessionen.
* **MDVA-38626** (*för Adobe Commerce och Magento Open Source >=2.3.3 &lt;2.4.5*) - Korrigerar ett fel där administratörsanvändaren inte kan lägga en order i backend-komponenten med betalningen [!DNL PayPal Payflow Pro].
* **MDVA-38666** (*för Adobe Commerce och Magento Open Source >=2.3.2 &lt;2.3.6*) - Korrigerar problemet där administratörsanvändaren inte kan ändra de konfigurerbara produktalternativen i kundvagnen.
* **MDVA-38526** (*för Adobe Commerce och Magento Open Source >=2.4.1 &lt;2.4.4*) - Korrigerar problemet där administratörsanvändaren inte kan komma åt [!DNL Site-Wide Analysis tool].
* Uppdaterade patchar: MDVA-40101.

## v1.1.8 {#v1-1-8}

* **MDVA-41215** (*för Adobe Commerce och Magento Open Source >=2.3.0 &lt;2.4.4*) - Korrigerar problemet där användare får felmeddelandet 500 efter att ha angett *image-messages* -cookien om den redan finns, men det finns inga nya meddelanden.
* **MDVA-41139** (*för Adobe Commerce och Magento Open Source >=2.4.3 &lt;2.4.4*) - Korrigerar problemet där konfigurerbara produkter blir utanför lagret efter produktimport när en enkel produkts kvantitet=0 för en av dess källor.
* **MDVA-42326** (*för Adobe Commerce och Magento Open Source >=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*) - Korrigerar problemet där kunderna får ett felmeddelande vid utcheckning efter en sessionstimeout även om den beständiga kundvagnen är aktiverad.
* **MDVA-42341** (*för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.4*) - Korrigerar problemet där `categoryList` GraphQL-frågan inte filtrerar resultat om en begäran har Store-rubriken.
* **MDVA-38393** (*för Adobe Commerce och Magento Open Source >=2.3.0 &lt;2.4.4*) - Korrigerar problemet där katalogregler slutar att fungera för en konfigurerbar produkt om dess enkla produkt namnges på nytt.
* **MDVA-39153** (*för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.4*) - Korrigerar problemet där ett rabattbelopp beräknas felaktigt vid omsortering i Admin.
* Uppdaterade patchar: MDVA-28993, MDVA-41061, MDVA-35984.

## v1.1.7 {#v1-1-7}

* **MDVA-39711** (*för Adobe Commerce och Magento Open Source >=2.3.0 &lt;2.4.3*) - Korrigerar problemet där administratörsanvändare inte kan komma åt kundens rutnät efter att webbplatsen har tagits bort.
* **MDVA-40311** (*för Adobe Commerce och Magento Open Source >=2.4.2-p2 &lt;2.4.4*) - Korrigerar problemet där administratörsanvändare får felmeddelandet *Ogiltig säkerhets- eller formulärnyckel. Uppdatera sidan* efter inloggning till administratören om den anpassade administratörssökvägen är konfigurerad och den hemliga nyckeln är aktiverad.
* **MDVA-41631** (*för Adobe Commerce och Magento Open Source >=2.4.1 &lt;2.4.4*) - Korrigerar ett problem där användare får ett fel när de försöker hämta orderinformation utan ett valfritt *telefon* -värde via GraphQL.
* **MDVA-27239** (*för Adobe Commerce och Magento Open Source >=2.3.0 &lt;2.3.6*) - Korrigerar problemet där korsförsäljningsprodukter inte visas.
* Uppdaterade patchar: MDVA-37068, MDVA-35254, MDVA-41164, MDVA-37916, MDVA-37478, MDVA-34551, MDVA-3179 1.

## v1.1.6 {#v1-1-6}

* **MDVA-40550** (*för Adobe Commerce och Magento Open Source >=2.3.5 &lt;2.4.4*) - Korrigerar problemet med saknade produkter på klientsidan vid omindexering.
* **MDVA-40120** (*för Adobe Commerce och Magento Open Source >=2.4.1 &lt;2.4.4*) - Korrigerar problemet där GraphQL sortering efter DESC/ASC inte fungerar med produkter med samma relevans eller pris.
* **MDVA-41399** (*för Adobe Commerce och Magento Open Source >=2.3.3 &lt;2.4.2*) - Korrigerar ett problem där administratörsanvändare inte kan komma åt sidan *Hantera kundvagn* om en kund lägger till en produkt i önskelistan.
* **MDVA-40609** (*för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.3*) - Korrigerar problemet där inaktiverade produktdata saknas i indextabellen `cataloginventory_stock_status`, vilket visar felaktiga inaktiverade produktkvantiteter.
* **MDVA-39031** (*för Adobe Commerce och Magento Open Source >=2.4.1 &lt;2.4.4*) - Korrigerar problemet där det går att lägga till en produkt i kundvagnen via GraphQL även om den inte har tilldelats målwebbplatsen.
* **MDVA-41597** (*för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.4*) - Korrigerar ett problem där användare får ett fel när fler än en konfigurerbar produkt läggs till i kundvagnen med GraphQL.
* **MDVA-27456** (*för Adobe Commerce och Magento Open Source >=2.3.5 &lt;2.3.7*) - Korrigerar problemet där användare får ett fel när de försöker läsa in [!DNL Swagger].
* **MDVA-32776** (*för Adobe Commerce och Magento Open Source >=2.4.0 &lt;2.4.2*) - Korrigerar problemet där lagerstatus inte uppdateras när en order placeras men inte skickas.
* **MDVA-30862** (*för Adobe Commerce och Magento Open Source >=2.3.4 &lt;2.4.0*) - Korrigerar problemet med fel orderdatum på den utskrivna PDF-fakturan.
* Förbättrade indexsidan för [!DNL Quality Patch Tool]. Lade till bekväm sökning och filtrering för [!DNL quality patches] i den senaste versionen av verktyget.
* Uppdaterade patchar: MDVA-33382, MDVA-39482.

## v1.1.5 {#v1-1-5}

* **MDVA-41236** (*för Adobe Commerce och Magento Open Source >=2.3.0 &lt;2.4.4*) - Korrigerar problemet där det inte går att skapa en ny eller redigera en befintlig schemalagd uppdatering för en produkt om slutdatumet har tagits bort tidigare.
* **MDVA-41046** (*för Adobe Commerce och Magento Open Source >=2.3.0 &lt;2.4.4*) - Korrigerar problemet där enkla produkter med anpassade alternativ kan tilldelas till konfigurerbara/grupperade produkter.
* **MDVA-40545** (*för Adobe Commerce och Magento Open Source >=2.3.0 &lt;2.4.4*) - Korrigerar problemet där endast den första noden för en sida hämtades, även om det fanns mer än en nod för samma sida.
* **MDVA-41164** (*för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.3-p1*) - Korrigerar problemet där en administratörsanvändare inte kan spara eller redigera ett företag med ett anpassat kundattribut för fil- eller bildtyp.
* **MDVA-39229** (*för Adobe Commerce och Magento Open Source >=2.3.0 &lt;2.4.4*) - Korrigerar problemet som orsakar att följande fel visas efter uppdatering av starttid för uppdatering av katalogregel: *Cron Job staging_synchronize_entities_period har ett fel: Den aktiva uppdateringen kan inte tas bort.*
* **MDVA-40619** (*för Adobe Commerce och Magento Open Source >=2.3.0 &lt;2.4.4*) - Korrigerar ett problem där ändringar i CMS sidhierarki orsakar ett 500-fel vid infogad redigering på en CMS-sida.
* **MDVA-41061** (*för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.3*) - Korrigerar problemet där Stock-statusen återställs till försäljningsbar när en produkt sparas från Admin.
* **MDVA-31763** (*för Adobe Commerce och Magento Open Source >=2.3.0 &lt;2.4.4*) - Korrigerar problemet där katalogprisreglerna återställs (eller inte tillämpas) tills den manuella indexeringen görs om.
* **MDVA-37748** (*för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.3*) - Korrigerar problemet där en GraphQL-fråga returnerar produkter som inte har tilldelats till en delad katalog.

## v1.1.4 {#v1-1-4}

* **MDVA-40399** (*för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.4*) - Korrigerar problemet där delfakturor för samma order inte kan skapas samtidigt via REST API.
* **MDVA-40101** (*för Adobe Commerce och Magento Open Source >=2.3.2 &lt;2.4.0*) - Korrigerar problemet där objekt inte tas bort från mini-vagnen efter en genomförd orderplacering med [!DNL PayPal Express] Checkout.
* **MDVA-40401** (*för Adobe Commerce och Magento Open Source >=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*) - Korrigerar problemet där kuponganvändningsvärdet ändras även om en beställning misslyckas.
* **MDVA-40537** (*för Adobe Commerce och Magento Open Source >=2.3.4 &lt;=2.4.0-p1*) - Korrigerar det problem där användare får ett fel när de skapar en butiksvy om det finns flera CMS-sidor med samma URL-nyckel.
* **MDVA-37725** (*för Adobe Commerce och Magento Open Source >=2.3.0 &lt;=2.4.3-p1*) - Korrigerar problemet där asynkrona e-postmeddelanden om beställningar som skickas från icke-standardwebbplatser innehåller URL-adresser från standardwebbplatsen.
* **MDVA-39482** (*för Adobe Commerce och Magento Open Source >=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*) - Korrigerar problemet där en produkt inte finns i lager om den importeras med kvantiteten &quot;0&quot; när restorder är aktiverade.
* **MDVA-40435** (*för Adobe Commerce och Magento Open Source >=2.3.4 &lt;2.4.4*) - Korrigerar problemet med felaktig rabatt på paketprodukter med dynamiska priser när de tillämpas via GraphQL.
* **MC-42528** (*för Adobe Commerce och Magento Open Source >=2.4.3 &lt;=2.4.3-p1*) - Korrigerar problemet där `categoryList` GraphQL-frågan returnerar både tilldelade och ej tilldelade kategorier.
* **MDVA-29400** (*för Adobe Commerce och Magento Open Source >=2.3.0 &lt;=2.3.7-p1 || >=2.4.0 &lt;=2.4.0-p1*) - Korrigerar problemet med duplicerade order som placerats med [!DNL PayPal Express Checkout].
* **MDVA-26005** (*för Adobe Commerce och Magento Open Source >=2.3.4 &lt;=2.3.5-p2*) - Korrigerar problemet där det inte går att välja en kategori i ett kategoriträd för villkoren för kundprisregel.
* **MDVA-25631** (*för Adobe Commerce och Magento Open Source >=2.3.3 &lt;=2.3.5-p2*) - Förbättrar prestanda för redigering och sparande av kundsegment som innehåller ett stort antal kunder.

## v1.1.3 {#v1-1-3}

* **MDVA-40262** (*för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.4*) - Korrigerar problemet där GraphQL sökfrågor inte visas i vanliga söktermer i Admin.
* **MDVA-40601** (*för Adobe Commerce och Magento Open Source >=2.3.1 &lt;=2.4.2-p2*) - Korrigerar problemet där användare får ett fel när de försöker få information om kategorin ändrad genom en schemalagd uppdatering via GraphQL.
* **MDVA-37234** (*för Adobe Commerce och Magento Open Source >=2.3.5 &lt;2.4.0 || >=2.4.1 &lt;=2.4.2-p2*) - Korrigerar problemet där ett objekt i vagnen läggs till flera gånger (parallell begäran) för samma SKU skapar ett dubblettobjekt för samma kundvagn-ID.
* **MDVA-33606** (*för Adobe Commerce och Magento Open Source >=2.4.1 &lt;=2.4.2-p2*) - Korrigerar problemet där användare får ett *Unikt begränsningsfel* när en CMS-sida som tilldelats en hierarki sparas.
* **MDVA-31590** (*för Adobe Commerce och Magento Open Source >=2.4.0 &lt;=2.4.1-p1*) - Korrigerar problemet där användare inte kan uppdatera attribut i grupp med MySQL async-köer.
* **MDVA-36309** (*för Adobe Commerce och Magento Open Source >=2.4.2 &lt;=2.4.2-p2*) - Korrigerar problemet där produktsökning efter attribut är långsam i administratörsrutnätet.

## v1.1.2 {#v1-1-2}

* **MDVA-38929** (*för Adobe Commerce och Magento Open Source >=2.3.0 &lt;2.4.4*) - Korrigerar problemet där fakturan med FPT visar fel totalsumma när ordern betalas från butikskrediten.
* **MDVA-37364** (*för Adobe Commerce och Magento Open Source >=2.4.0 &lt;=2.4.3*) - Korrigerar problemet där det anpassade kundattributet av datumtyp bryter kundens rutnätsgränssnitt.
* **MDVA-39195** (*för Adobe Commerce och Magento Open Source >=2.4.2 &lt;=2.4.2-p2*) - Korrigerar problemet där knappen *Lägg till i kundvagnen* var inaktiv på kategorisidan när omdirigering till kundvagnen är aktiverad.
* **MDVA-37115** (*för Adobe Commerce och Magento Open Source >=2.4.2 &lt;=2.4.2-p2*) - Korrigerar problemet där ett onödigt meddelande om *Endast 0 kvar* visas på den konfigurerbara produktsidan.
* **MDVA-39521** (*för Adobe Commerce och Magento Open Source >=2.4.0 &lt;2.4.4*) - Korrigerar problemet där användaren inte kan ange leveransadresser i kundvagnen med ett tomt telefonnummer via GraphQL.
* **MDVA-39384** (*för Adobe Commerce och Magento Open Source >=2.3.1 &lt;=2.3.6 || >=2.4.1 &lt;=2.4.3*) - Korrigerar problemet där det anpassade kundattributet för en företagsanvändare inte sparas.
* **MDVA-39043** (*för Adobe Commerce och Magento Open Source >=2.3.4 &lt;=2.4.3*) - Korrigerar ett fel där administratörsanvändaren med begränsad åtkomst får ett fel när han försöker lägga till *Products* -widgeten på CMS-sidan.
* **MDVA-39966** (*för Adobe Commerce och Magento Open Source >=2.3.0 &lt;=2.3.5-p2 || >=2.4.0 &lt;=2.4.0-p1*) - Korrigerar problemet med distribution av felaktiga språkinställningar.
* **MDVA-38852** (*för Adobe Commerce och Magento Open Source >=2.3.0 &lt;=2.3.5-p2*) - Korrigerar problemet där kataloginventeringen efter design låser tabeller för uppdateringar som avsevärt försämrar prestanda vid flera parallella order.
* **MDVA-39986** (*för Adobe Commerce och Magento Open Source >=2.4.1 &lt;2.4.3*) - Korrigerar ett fel där användaren inte kan göra en beställning i Admin i MacOS via webbläsaren Safari.
* **MDVA-38447** (*för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.4*) - Korrigerar två problem: där *Inte synlig individuellt* konfigurerbara underordnade produkter returneras i GraphQL-svar och optimerar MySQL-frågan för GraphQL-produktfråga med kategorifilter.
* **MDVA-40134** (*för Adobe Commerce och Magento Open Source >=2.4.2 &lt;2.4.3*) - Korrigerar problemet där GraphQL inte returnerar relaterade produkter när den delade katalogen är aktiverad.
* **MDVA-39935** (*för Adobe Commerce och Magento Open Source >=2.4.1 &lt;2.4.4*) - Korrigerar problemet där GraphQL returnerar konfigurerbara underordnade produkter som är inaktiverade på webbplatsnivå.

## v1.1.1 {#v1-1-1}

* **MDVA-36021** (*för Adobe Commerce och Magento Open Source >=2.4.0 &lt;2.4.4*) - Korrigerar problemet där felet *Anrop till en medlemsfunktion getId()* visas på sidan med orderinformation i Admin.
* **MDVA-34948** (*för Adobe Commerce och Magento Open Source >=2.3.6 &lt;=2.3.6-p1 || >=2.4.0 &lt;=2.4.0-p1*) - Korrigerar problemet med långvariga frågor, som `GET_LOCK`.
* **MDVA-39305** (*för Adobe Commerce och Magento Open Source >=2.4.0 &lt;=2.4.2-p1*) - Korrigerar problemet där registrerade kunder inte kan logga in med aktiverad Google ReCaptcha.
* **MDVA-37897** (*för Adobe Commerce och Magento Open Source >=2.3.0 &lt;2.4.4*) - Korrigerar problemet med en felaktig omdirigering när en kund försöker lägga till produkter med alternativ från widgeten Senast visade.

## v1.1.0 {#v1-1-0}

* Korrigeringskategorierna introducerades för att förbättra användarupplevelsen och göra det enklare för kunderna att söka efter nödvändiga korrigeringsfiler.
* Filen `patches.json` har bytt namn till `support-patches.json`.
* **MDVA-38799** (*för Adobe Commerce >=2.3.0 &lt;2.4.3*) - Korrigerar problemet där hämtningsbara produkter inte sparades efter att en mellanlagringsuppdatering skapades.
* **MDVA-37592** (*för Adobe Commerce >=2.3.6 &lt;=2.4.2-p1*) - Korrigerar problemet när sortering efter pris inte fungerar korrekt för produkter med ett nollpris tilldelat den delade katalogen.
* **MDVA-38827** (*för Adobe Commerce >=2.3.3-p1 &lt;2.4.4*) - Korrigerar problemet där kunderna får ett e-postmeddelande med ett felmeddelande.

## v1.0.26 {#v1-0-26}

* **MDVA-38468** (*för Adobe Commerce >=2.3.2 &lt;=2.3.5-p2*) - Korrigerar felet när CMS-sidor sparas: *Objekt med samma ID PAGE_ID finns redan*.
* **MDVA-34680** (*för Adobe Commerce >=2.3.6 &lt;=2.3.7 || >=2.4.1 &lt;2.4.3*) - Korrigerar problemet där kundkontots skapade tid inte filtreras korrekt i kundrutnätet.
* **MDVA-37068** (*för Adobe Commerce >=2.3.1 &lt;2.4.4*) - Korrigerar problemet där fel momssats visas när kundvagnen bara har virtuella produkter.
* **MDVA-38608** (*för Adobe Commerce >=2.3.0 &lt;2.4.3*) - Korrigerar problemet där temporära tabeller inte tas bort när omindexeringen inte har slutförts.
* **MDVA-38308** (*för Adobe Commerce >=2.3.5 &lt;=2.3.6-p1 || >=2.4.0 &lt;=2.4.1-p1 || >=2.4.2 &lt;2.4.4*) - Korrigerar problemen med att lägga till [!DNL Vimeo] videofilmer i produkter.

## v1.0.25 {#v1-0-25}

* **MDVA-37916** (*för Adobe Commerce >=2.3.6 &lt;2.4.3*) - Korrigerar problemet där kunden inte kommer till sidan Betalningsbekräftelse när metoden [!DNL Paypal Payment Advanced] används.
* **MDVA-37082** (*för Adobe Commerce >=2.3.0 &lt;2.4.3*) - Korrigerar problemet när du sparar den anpassade versionen av grupperade produkter så att produkten inte finns i lager i förgrunden.
* **MDVA-36572** (*för Adobe Commerce >=2.3.5 &lt;2.4.3*) - Korrigerar problemet när kreditnotan uppdateras inte längre orsakar dubblerade produktreservationsuppdateringar i databasen.
* **MDVA-38132** (*för Adobe Commerce >=2.3.3 &lt;2.4.3*) - Korrigerar problemet när administratörspanelen inte kan nås på grund av ett *för många omdirigeringsfel* .
* **MDVA-38270** (*för Adobe Commerce >=2.4.1 &lt;2.4.3*) - Korrigerar problemet med att information om presentkort saknas i ordersumman i GraphQL.

## v1.0.24 {#v1-0-24}

* **MDVA-37779** (*för Adobe Commerce >=2.4.2 &lt;=2.4.4*) - Korrigerar problemet med att lägga till en konfigurerbar produkt i kundvagnen via GraphQL när webbplats-ID:t inte sammanfaller med butiks-ID:t.
* **MDVA-36832** (*för Adobe Commerce >=2.3.4 &lt;=2.4.2-p1*) - Korrigerar problemet där bilder dupliceras på sidor när visningsbredden är 768 px.
* **MDVA-37874** (*för Adobe Commerce >=2.3.6 &lt;=2.3.7 || >=2.4.1 &lt;=2.4.2-p1*) - Korrigerar problemet där *Fast rabattbelopp för hel kundvagn* felaktigt tillämpas på en paketprodukt som innehåller mer än ett alternativ.
* **MDVA-37913** (*för Adobe Commerce >=2.3.0 &lt;=2.4.0-p1*) - Korrigerar problemet där hämtningsbara länkar försvinner om den hämtningsbara produkten uppdateras via API.
* **MDVA-34330** (*för Adobe Commerce >=2.3.1 &lt;=2.4.2-p1*) - Korrigerar problemet där order i orderrastret inte filtreras enligt administratörens tidszon.

## v1.0.23 {#v1-0-23}

* **MDVA-37478** (*för Adobe Commerce >=2.3.0 &lt;=2.3.7*) - Korrigerar problemet där Adobe Commerce genererar ett fel när en delfaktura skapas för order som har placerats med betalningsmetoden *Betalning på konto* via REST API.
* **MDVA-37362** (*för Adobe Commerce >=2.3.4 &lt;=2.4.2-p1*) - Korrigerar problemet där konfigurerbara produktalternativvärden och variantattributvärden var tomma i GraphQL-svar.
* **MDVA-37288** (*för Adobe Commerce 2.4.2*) - Korrigerar problemet där felaktiga nivåpriser returnerades efter GraphQL begäran.
* **MDVA-37225** (*för Adobe Commerce >=2.4.1 &lt;=2.4.2-p1*) - Korrigerar problemet där överföringsprocessen fastnar när snabbordningen skapas när det finns ett heltalsvärde i importerade SKU:er.
* **MDVA-37224** (*för Adobe Commerce >=2.3.3 &lt;=2.4.2-p1*) - Korrigerar problemet där kunder inte kan betala för överlåtbar offert med [!DNL PayFlow Pro] med en annan produkt i kundvagnen.
* **MDVA-36286** (*för Adobe Commerce >=2.3.6 &lt;=2.4.2-p1*) - Korrigerar ett problem där förhandsvisningen av Page Builder-produkter bryts om samma SKU har en annan position i underkategorier.
* **MDVA-30186** (*för Adobe Commerce >=2.3.4 &lt;=2.3.5-p2, >=2.4.0 &lt;=2.4.0-p1, >=2.4.2 &lt;=2.4.2-p1*) - Korrigerar problemet där attributalternativen sorteras efter alternativvärde i stället för attributobjektet räkna i GraphQL svar.

## v1.0.22 {#v1-0-22}

* **MDVA-36718** (*för Adobe Commerce >=2.3.0 &lt;=2.4.2*) - Korrigerar problemet där de gamla anpassade alternativen kvarstår efter att de har ändrats via API.
* **MDVA-35773** (*för Adobe Commerce >=2.3.6 &lt;=2.3.6-p1 || >=2.4.1 &lt;=2.4.2*) - Korrigerar problemet med att totalsumman inte visas som noll på fakturan för order med 100 % rabatt.
* **MDVA-36833** (*för Adobe Commerce 2.4.2*) - Korrigerar problemet med sökresultat som visar slumpmässiga antal produkter per sida efter att vissa produkter har utelämnats från en delad katalog.
* **MDVA-37182** (*för Adobe Commerce >=2.4.1 &lt;=2.4.2*) - Korrigerar problemet med felaktiga sökresultat i både [!DNL Elasticsearch] version 6 och version 7.
* **MDVA-36253** (*för Adobe Commerce >=2.4.0 &lt;=2.4.1-p1*) - Korrigerar problemet där fel delsumma visas i minikorgen efter att objekt har tagits bort.
* **MDVA-36853** (*för Adobe Commerce 2.4.2*) - Korrigerar problemet med att inga bilder visas vid inläsning av stora mediegallerier.

## v1.0.21 {#v1-0-21}

* **MDVA-34665** (*för Adobe Commerce >=2.3.4 &lt;=2.3.4-p2*) - Korrigerar problemet med saknade paketerade produkter på kategorisidor.
* **MDVA-36615** (*för Adobe Commerce 2.4.2*) - Korrigerar problemet med felaktigt produktantal i Admin-produktstödrastret.
* **MDVA-36464** (*för Adobe Commerce >=2.4.0 &lt;=2.4.2*) - Korrigerar problemet där e-postmeddelandekonfigurationen inte fungerar på butiksvisningsnivå.
* **MDVA-36138** (*för Adobe Commerce ^2.3.2*) - Korrigerar problemet där leveranspriset inte justeras och där det fulla fraktpriset visas för kunderna om inte alla artiklar i vagnen berättigar till frakt.
* **MDVA-36424** (*för Adobe Commerce >=2.3.0 &lt;=2.3.3-p1 || >=2.0.0 &lt;2.2.0*) - Korrigerar problemet där mediabilder som är kopplade till sidbyggarelement försvinner när innehållet redigeras upprepade gånger om backend-bas-URL:en skiljer sig från storefront-URL:en.
* **MDVA-35984** (*för Adobe Commerce ^2.4.0*) - Korrigerar problemet med felaktig produktkvantitet och säljbar kvantitet efter att flera samtidiga leveranser har skapats för samma produkt.

## v1.0.20 {#v1-0-20}

* **MDVA-36170** (*för Adobe Commerce >=2.3.4 &lt;2.4.2*) - Detta åtgärdar ett problem där GraphQL-frågan inte cachelagras med cachetaggen för kategorin.
* **MDVA-33168** (*för Adobe Commerce >=2.3.3 &lt;2.4.2*) - Korrigerar problemet när ett produktattribut uppdateras via API. Alla andra attribut ändras till ett tomt värde.
* **MDVA-19640** (*för Adobe Commerce >=2.3.0*) - Korrigerar problemet där [!DNL Advanced Reporting] inte visar några data.
* **MDVA-11189** (*för Adobe Commerce >=2.3.0 &lt;2.3.5*) - Korrigerar problemet när en CSV-fil för uppdatering av produktpaketet har importerats och rader från tabellen `cataloginventory_stock` tas bort.
* **MDVA-26639** (*för Adobe Commerce >=2.3.3-p1 &lt;2.3.6*) - Korrigerar problemet där orderobjekten saknas i orderpostmeddelandet om en ny mall för orderbekräftelse skapas.
* **MDVA-15546** (*för Adobe Commerce >=2.3.0*) - Korrigerar problemet där ett *Column entity_id-uttryck där -satsen är tvetydig* visas i undantagsloggen när en ordning har skapats.
* **MDVA-21095** (*för Adobe Commerce >=2.3.0 &lt;2.3.5*) - Korrigerar problemet när en fråga `INSERT INTO search_tmp` inte slutar efter att massattributvärdet har uppdaterats.
* **MDVA-23845** (*för Adobe Commerce >=2.3.2-p2 &lt;2.3.5*) - Korrigerar problemet där e-postmallar inte kan förhandsgranskas när JavaScript minification är aktiverat.
* **MDVA-22026** (*för Adobe Commerce >=2.3.2 &lt;2.3.4*) - Korrigerar problemet där det inte går att importera produkter från CSV-filer, inklusive bilder från externa URL:er.
* **MDVA-22383** (*för Adobe Commerce >=2.3.0 &lt;2.3.4*) - Korrigerar problemet där det tar lång tid att spara en produkt och sidan avbryts.
* **MC-41359** (*för Adobe Commerce >=2.3.6-p1 &lt;2.3.7, >=2.4.2 &lt;2.4.3*) - Korrigerar problemet med felaktiga inställningar för cookie-parametrar för SameSite.

## v1.0.19 {#v1-0-19}

* **MDVA-33614** (*för Adobe Commerce 2.4.1*) - Korrigerar problemet där Page Builder orsakar följande fel: *Ett fel uppstod när Page Builder startades. Kontakta din tekniska supportkontakt.*
* **MDVA-35356** (*för Adobe Commerce >=2.3.0 &lt;2.4.3*) - Korrigerar problemet med felaktig avkastning på butikskrediter efter delvis fakturerad orderannullering.
* **MDVA-33289** (*för Adobe Commerce >=2.4.0 &lt;2.4.3*) - Korrigerar problemet där rå JavaScript-kod visas i faktureringsadressgränssnittet vid utcheckning om [!DNL Google Tag Manager] är aktiverat.
* **MDVA-35982** (*för Adobe Commerce >=2.3.0 &lt;2.4.3*) - Korrigerar problemet där administratörsanvändare som är begränsade till en viss webbplats inte kan skapa en leverans för den beställning som finns på samma webbplats.
* **MDVA-35155** (*för Adobe Commerce >=2.3.0 &lt;2.3.6*) - Korrigerar problemet där det inte går att köpa en paketprodukt om alternativtiteln har ändrats.
* **MDVA-35910** (*för Adobe Commerce >=2.4.1 &lt;2.4.3*) - Korrigerar problemet där det inte går att skapa ett nytt kundkonto efter att inloggningen har inaktiverats som kundfunktion.
* **MDVA-34474** (*för Adobe Commerce >=2.3.0 &lt;2.4.3*) - Korrigerar problemet med att lägga till en produkt i rekvisitionslistan med API:t.
* **MDVA-34591** (*för Adobe Commerce >=2.3.0 &lt;2.4.3*) - Korrigerar problemet med en felaktig beräkning av kundvagnsrabatt för *maximal kvantitetsrabatt används för* och *Rabattsteg (Köp X)*.
* **MDVA-33704** (*för Adobe Commerce >=2.4.0 &lt;2.4.3*) - Korrigerar problemet där leveransalternativet *I butik-hämtning* inte visas, trots att det är konfigurerat att vara tillgängligt.
* **MDVA-34928** (*för Adobe Commerce >=2.3.5 &lt;2.3.5-p2*) - Korrigerar problemet där sidinläsaren visas oavbrutet när butikskrediten har tagits bort från betalningen.
* **MDVA-35254** (*för Adobe Commerce >=2.3.1 &lt;2.4.3*) - Korrigerar problemen med CAPTCHA vid utcheckning.
* **MDVA-35569** (*för Adobe Commerce >=2.3.4 &lt;2.4.2*) - Korrigerar problemet där fältet *Fasta produktskatter* inte fylls i i i GraphQL-svar när tillstånd anges.
* **MDVA-35847** (*för Adobe Commerce >=2.4.1 &lt;2.4.3*) - Korrigerar B2B-problemet där företagsanvändare skapar radbrytningar om ett anpassat kundattribut används.
* **MDVA-31307** (*för Adobe Commerce >=2.4.0 &lt;2.4.2*) - Korrigerar problemet där det finns *Slut på minne* i vissa kategorier på grund av problem med dynamisk CSP-vitlistning för cachelagrade block.

## v1.0.18 {#v1-0-18}

* **MDVA-32655** (*för Adobe Commerce >=2.3.0 &lt;2.4.3*) - Korrigerar den felaktiga *progress* -meddelandestatusen till rätt *complete* -meddelande för konsumenten `quoteItemCleaner` efter att flera produkter har tagits bort.
* **MDVA-34102** (*för Adobe Commerce >=2.3.0 &lt;2.4.3*) - Korrigerar antalet standardlager som är noll för inaktiverade produkter i produktstödrastret och Redigera produktsidor i administratörsområdet.
* **MDVA-35286** (*för Adobe Commerce >=2.4.0 &lt;2.4.2*) - Korrigerar problemet där det uppstår ett fel om en kund har paketerat produkter i kundvagnen och växlar från utcheckning av flera adresser till utcheckning av en sida.
* **MDVA-35312** (*för Adobe Commerce >=2.4.1-p1 &lt;2.4.2*) - Korrigerar svarskod 500 när en tom GraphQL-begäran skickas.
* **MDVA-34189** (*för Adobe Commerce >=2.3.4 &lt;2.4.3*) - Korrigerar timeout för första byte för [!DNL Visual Merchandiser] -frågor vid inläsning av sidan Admin Category.
* **MDVA-34695** (*för Adobe Commerce >=2.3.0 &lt;2.4.1*) - Korrigerar negativ `children_count` efter att kategorier har tagits bort.

## v1.0.17 {#v1-0-17}

* **MDVA-34012** (*för Adobe Commerce >=2.3.1 &lt;2.4.3*) - Korrigerar problemet där kryssrutan *Använd standardvärde* rensas när de schemalagda ändringarna har tillämpats. Problemet uppstår när de schemalagda ändringarna inte längre gäller.
* **MDVA-35064** (*för Adobe Commerce >=2.3.3 &lt;2.4.3*) - Korrigerar problemet där URL-omskrivningar inte genereras för konfigurerbara produkter som skapats via API.
* **MDVA-34943** (*för Adobe Commerce >=2.3.0 &lt;2.4.2*) - Korrigerar problemet där snabbsortering cachelagrar de SKU:er som angetts tidigare.
* **MDVA-35197** (*för Adobe Commerce >=2.3.5 &lt;2.4.0*) - Korrigerar ett fel när du lägger till i kundvagnen med GraphQL om tidigare tillagda produkter inte finns i lager.
* **MDVA-34850** (*för Adobe Commerce >=2.3.1 &lt;2.4.0*) - Korrigerar problemet där optioner som inte finns på lager för en konfigurerbar produkt inte visas i stället för att visas som genomstruken.
* **MDVA-34867** (*för Adobe Commerce >=2.3.0 &lt;2.4.3*) - Korrigerar problemet där värden för ett villkorsfält som angetts för en schemalagd uppdatering inte sparas.
* **MDVA-35092** (*för Adobe Commerce >=2.3.5 &lt;2.4.3*) - Korrigerar ett problem där användare inte kan lägga till [!DNL Vimeo] videor på grund av det inaktuella [!DNL Vimeo] API:t.

## v1.0.16 {#v1-0-16}

* **MDVA-33453** (*för Adobe Commerce >=2.3.6 &lt;2.4.3*) - Korrigerar problemet där förhandsvisningen av Page Builder-produkters innehållstyp bryts om matchande produkter har olika priser för varje webbplats.
* **MDVA-32634** (*för Adobe Commerce ^2.3.1*) - Korrigerar problemet där `url_path` för den kategori som tilldelats till all butik inte ändras efter att kategorin har flyttats i hierarkin.
* **MDVA-33344** (*för Adobe Commerce ^2.3.0*) - Korrigerar problemet där ID för den hårdkodade `rma_item`-entitetens standardattributuppsättning används i stället för värdet från databasen.
* **MDVA-34192** (*för Adobe Commerce >=2.3.4 &lt;2.4.3*) - Korrigerar problemet där det inte går att ändra/ange kundens födelsedatum i formatet dd/mm/åååå.
* **MDVA-34847** (*för Adobe Commerce ^2.3.0*) - Korrigerar konvertering av lagrings-ID:n till heltal för SQL-villkor i Admin-samlingar för Admin User med anpassade behörigheter.
* **MDVA-34886** (*för Adobe Commerce ^2.3.2*) - Korrigerar problemet där sökningen inte returnerar resultat om produktattributet *weight* är konfigurerat som sökbart.

## v1.0.15 {#v1-0-15}

* **MDVA-33559** (*för Adobe Commerce >=2.3.0 &lt;2.4.3*) - Korrigerar problemet med att [!DNL PayPal Payflow Pro] betalning misslyckades med formatfel för omdirigeringsparameterlista.
* **MDVA-34023** (*för Adobe Commerce >=2.3.0 &lt;2.4.3*) - Korrigerar problemet där felet *Ingen sådan entitet med addressId* visas slumpmässigt i besökarens webbläsare.
* **MDVA-32759** (*för Adobe Commerce >=2.3.1 &lt;2.4.3 med B2B-tillägg*) - Korrigerar problemet där delade kataloger tar bort befintliga nivåpriser.
* **MDVA-33482** (*för Adobe Commerce ^2.3.5*) - Korrigerar problemet där en kreditnota genereras mot en partiell faktura och leder till moms för den totala ordern i stället för moms för den partiella fakturan.
* **MDVA-33393** (*för Adobe Commerce >=2.3.0 &lt;2.4.2*) - Korrigerar felet *Angivet countryId finns inte*.
* **MDVA-33632** (*för Adobe Commerce >=2.3.0 &lt;2.3.7*) - Tillhandahåller en korrigering där undantagsmeddelandet *Produkten är inte i lager* visas nu för en administratörsanvändare när de försöker beställa om en produkt som inte finns i lager.
* **MDVA-34469** (*för Adobe Commerce >=2.4.1 &lt;2.4.2*) - Korrigerar problemet där GraphQL-mutationer i kundvagnen misslyckas när flera butiksvyer används.
* **MDVA-33976** (*för Adobe Commerce >=2.3.0 &lt;2.3.7*) - Korrigerar problemet där paketprodukten visas utanför lagret efter att det andra alternativet tagits bort från paketprodukten.
* **MDVA-33894** (*för Adobe Commerce >=2.4.0 &lt;2.4.1 med B2B-tillägg*) - Korrigerar flera problem för snabbordningsfunktionen, inklusive tillägg och borttagning av flera produkter och SKU-skiftlägeskänslighet.
* **MDVA-27664** (*för Adobe Commerce >=2.3.4 &lt;2.3.6*) - Korrigerar problemet i kundregistreringsformuläret som orsakar ett fel: *FEL - Födelsedatumet får inte vara senare än idag.*
* **MDVA-33970** (*för Adobe Commerce >=2.3.4 &lt;2.4.2*) - Korrigerar problemet där det finns fel valutatecken i kreditnotan när prisattributets omfång är inställt på webbplats.
* **MDVA-33992** (*för Adobe Commerce >=2.3.0 &lt;2.4.2*) - Korrigerar problemet med B2B-specialpriser som visas felaktigt vid utcheckning.
* **MDVA-34100** (*för Adobe Commerce >=2.3.4 &lt;2.4.2 med B2B-tillägg*) - Korrigerar problemet där ett företagskonto inte kan skapas från företagsstruktursidan.

## v1.0.14 {#v1-0-14}

* **MDVA-31969** (*för Adobe Commerce >=2.3.3 &lt;2.3.5, >=2.4.0 &lt;2.4.2*) - Korrigerar problemet med duplicerade bilder efter produktimport från en CSV-fil.
* **MDVA-33382** (*för Adobe Commerce >=2.3.0 &lt;2.4.2*) - Korrigerar problemen med indexerarogiltigförklaring efter att produkter har tagits bort från en kategori.
* **MDVA-28511** (*för Adobe Commerce >=2.3.5 &lt;2.3.6*) - Korrigerar problemet där det inte går att slutföra [!DNL PayPal]-utcheckningen om namnfältet innehåller vissa tecken (som versaler med accent).
* **MDVA-31519** (*för Adobe Commerce >=2.3.5 &lt;2.3.6*) - Korrigerar problemet med timeout i gästutcheckning när en platsövergripande försäljningsregel används.
* **MDVA-33281** (*för Adobe Commerce >=2.3.4 &lt;2.3.6*) - Korrigerar problemet där det finns ett allvarligt fel i `inventory:reservation:list-inconsistencies` på grund av fel SKU-parametertyp.
* **MDVA-24201** (*för Adobe Commerce >=2.3.0 &lt;2.3.5*) - Korrigerar problemet där priserna inte återspeglar den schemalagda kundprisregeln förrän manuellt indexerat om.
* **MDVA-32694** (*för Adobe Commerce >=2.3.0 &lt;2.3.6 || >= 2.4.0 &lt;2.4.2*) - Korrigerar problemet där en administratörsanvändare inte kan lägga till en produkt i en överlåtbar offert om den är relaterad till ett lager som inte är standard.
* **MDVA-33516** (*för Adobe Commerce >=2.3.0 &lt;2.3.6*) - Korrigerar problemet där redigering av en paketprodukt i en rekvisitionslista leder till ett fel.
* **MDVA-33975** (*för Adobe Commerce >=2.3.4 &lt;2.4.2*) - Korrigerar flera problem relaterade till prisberäkning i GraphQL-begäranden.

## v1.0.13 {#v1-0-13}

* **MDVA-30858** (*för Adobe Commerce >=2.3.0 &lt;2.4.2*) - Korrigerar problemet med att [!DNL PayPal] kvittningsrapporter inte är tillgängliga under **Rapporter** > **Försäljning** > **[!DNL PayPal]** Kvittning som förväntat.
* **MCP-87** (*för Adobe Commerce >=2.3.1 &lt;2.4.2*) - Förbättrad indexeringstid för kategoriprodukter och aktieindexerare för stora profiler.
* **MDVA-33106** (*för Adobe Commerce >=2.3.0 &lt;2.4.2*) - Korrigerar det problem där de schemalagda produktändringarna raderas efter att cron `run`-kommandot har körts.
* **MDVA-19391** (*för Adobe Commerce >=2.3.0 &lt;2.3.5*) - Korrigerar problemet där `analytics_collect_data` genererar ett fel på grund av NULL-beskrivningsposter i tabellen `catalog_category_entity_text`.
* **MDVA-20376** (*för Adobe Commerce >=2.3.2 &lt;2.3.4*) - Korrigerar problemet med *Ingen sådan entitet med customerId = 1* fel i `exception.log` för inloggade kunder efter orderplacering.
* **MDVA-23764** (*för Adobe Commerce >=2.3.2 &lt;2.3.5*) - Korrigerar felet i `JsFooterPlugin.php` som påverkar visningen av dynamiska block.
* **MDVA-13203** (*för Adobe Commerce >=2.3.0 &lt;2.4.2*) - Korrigerar problemet där felet *Integritetsbegränsning i search_tmp_ table* inträffar efter en fullständig indexering.
* **MDVA-23426** (*för Adobe Commerce >=2.3.3 &lt;2.3.5*) - Korrigerar problemet där e-postmeddelanden som skickas av Adobe Commerce innehåller en tom brödtext med innehåll som läggs till som bilaga.
* **MDVA-22150** (*för Adobe Commerce >=2.3.1 &lt;2.3.4*) - Korrigerar problemet där kunder med en konfigurerbar produkt i kundvagn och en kupong som används inte kan logga in om den konfigurerbara produkten är inaktiverad i administratören.
* **MDVA-32545** (*för Adobe Commerce >=2.3.0 &lt;2.4.2*) - Korrigerar problemet där fakturor inte skickas ut automatiskt när beställningar skapas från administratören.
* **MDVA-32714** (*för Adobe Commerce >=2.3.4 &lt;2.4.1*) - Korrigerar problemet där kundgruppspriset inte fungerar i GraphQL-produktfrågan.

## v1.0.12 {#v1-0-12}

* **MDVA-31399** (*för Adobe Commerce >=2.3.2 &lt;2.4.2*) - Lägger till delsumman *Incl. Moms)*-alternativ till prisregelvillkor.
* **MDVA-31236** (*för Adobe Commerce >=2.4.0 &lt;2.4.2*) - Korrigerar problemet där administratörer med anpassad resursåtkomst inte kan konfigurera 2FA eller logga in.
* **MDVA-30845** (*för Adobe Commerce >=2.3.5 &lt;2.3.7*) - Korrigerar problemet där *Inga citattecken för den här beställningen för tillfället* visas när det inte går att ansluta till UPS XML/USPS/DHL, och ingen annan leveransmetod är tillgänglig.
* **MDVA-32133** (*för Adobe Commerce >=2.4.0 &lt;2.4.1*) - Korrigerar problemet där mediegalleriet inte läses in från Page Builder i vissa fall.
* **MDVA-12304** (*för Adobe Commerce >=2.3.0*) - Ökar det maximala antalet cookies från 50 till 200.
* **MDVA-32632** (*för Adobe Commerce >=2.3.2 &lt;2.3.5*) - Korrigerar problemet där order visas i betalningssystemet, men inte i Adobe Commerce.
* **MDVA-32449** (*för Adobe Commerce >=2.3.0 &lt;2.3.6 || 2.4.0 || >=2.4.1 &lt;2.4.2 med B2B-tillägg*) - Korrigerar problemet där orderhistoriken läses in mycket långsamt eller inte läses in alls.
* **MDVA-32739** (*för Adobe Commerce >=2.3.0 &lt;2.4.2*) - Korrigerar problemet där Asynkrona e-postmeddelanden skickar gamla e-postmeddelanden.

## v1.0.11 {#v1-0-11}

* **MC-38509** (*för Adobe Commerce 2.3.6, 2.4.1*) - Korrigerar problemet där knappen *Skapa ett konto* inte längre är aktiverad efter att ogiltiga data i formuläret *Skapa nytt kundkonto* har korrigerats.
* **MDVA-31006** (*för Adobe Commerce 2.3.0, 2.3.1*) - Korrigerar problemet där dubblettorder visas efter att en beställning har gjorts med betalningen [!DNL Paypal Express].
* **MDVA-25602** (*för Adobe Commerce 2.3.0*) - Korrigerar problem med betalningsmetoden [!DNL PayPal Payflow Pro] och behandlar cookies som `SameSite=Lax` som standard i webbläsaren Chrome 80 och API-svar omdirigeras till kundinloggningssidan.

## v1.0.10 {#v1-0-10}

Mindre korrigeringar för korrigeringsversioner

## v1.0.9 {#v1-0-9}

* **MDVA-31363** (*för Adobe Commerce >=2.3.2 &lt;2.4.2*) - Korrigerar problemet där kundprisregeln med kupong inte gäller via GraphQL när *Fast beloppsrabatt för hela kundvagnen* används.
* **MDVA-30889** (*för Adobe Commerce >=2.3.0 &lt;2.4.2*) - Korrigerar problemet där ett fel inträffar efter att ett paket med virtuella och enkla produkter har anropats som alternativ.
* **MDVA-31791** (*för Adobe Commerce >=2.3.4 &lt;2.3.5*) - Förbättrar produktsidans prestanda om målregler eller länkade produkter används.
* **MDVA-31168** (*för Adobe Commerce >=2.3.0 &lt;2.4.2*) - Korrigerar problemet där produktexportens CSV-fil inte visas, och det finns ett minnesallokeringsfel.
* **MDVA-32313** (*för Adobe Commerce >=2.3.0 &lt;2.3.4*) - Korrigerar problemet där konfigurerbara produkter kan läggas till i önskelistan med fel konfigurationsalternativ.
* **MDVA-31759** (*för Adobe Commerce >=2.3.0 &lt;2.4.2*) - Korrigerar problemet där produkter inte uppdateras med attributvärdena *dropdown* och *textarea* vid CSV-import.
* **MDVA-32012** (*för Adobe Commerce >=2.3.0 &lt;2.4.2*) - Korrigerar problemet där postnummer i Korea och Argentina inte kan valideras.
* **MDVA-31640** (*för Adobe Commerce >=2.3.1 &lt;2.3.6 || >=2.4.0 &lt;2.4.1*) - Korrigerar problemet där ett specialpris inte kan uppdateras via REST API.
* **MDVA-28651** (*för Adobe Commerce >=2.3.0 &lt;2.3.6 || >2.4.0 med B2B-tillägg*) - Korrigerar problemet där prestandaproblem uppstår vid inläsning av överlåtbara offerter via REST API.

## v1.0.8 {#v1-0-8}

* **MDVA-31242** (*för Adobe Commerce >=2.3.0 &lt;2.4.1 med B2B-tillägg*) - Korrigerar problemet där en felaktig valutasymbol visas i kreditnotsrutnätet.
* **MDVA-31295** (*för Adobe Commerce >=2.3.0 &lt;2.4.2*) - Korrigerar problemet där belöningspunkter inte beräknas när en delorder har slutförts och artiklarna beskattas.
* **MDVA-30112** (*för Adobe Commerce >=2.3.4 &lt;2.4.2*) - Korrigerar problemet där om antalet order överstiger värdet för *bundstorlek* betraktar Adobe Commerce order med statusen *pending* som inkonsekvenser.
* **MDVA-31150** (*för Adobe Commerce >=2.3.0 &lt;2.4.2*) - Korrigerar problemet där butikskreditsaldon och presentkortsaldon inte returneras av GET Invoice Rest API-anropet, när fakturan bokfördes av Rest API-anrop och ordern delvis betalades av butikskreditkort och presentkortskonton.
* **MDVA-30963** (*för Adobe Commerce >=2.3.2 &lt;2.4.2*) - Korrigerar problemet där produktfiltreringsresultat bara innehåller värden som angetts för omfattningen *Alla butiksvyer* i Admin, inkluderar produkter med värden som åsidosatts på visningsnivån för butiken.
* **MDVA-29954** (*för Adobe Commerce >=2.3.0 &lt;2.3.6 || 2.4.0 || 2.4.2 med B2B-tillägg*) - Korrigerar problemet där *Ny registreringsbegäran* och *Du har länkats till ett företags* e-postmeddelanden skickas från fel adress.
* **MDVA-28357** (*för Adobe Commerce >=2.3.2 &lt;2.3.6 || >=2.4.0 &lt;2.4.1*) - Ersätter standardanalyseraren med en anpassad analyserare med en nyckelordstokenerare för SKU-fältet i [!DNL ElasticSearch] -indexet så att sökfrågor med jokertecken fungerar med SKU:er som innehåller ett bindestreck (&quot;-&quot;).

## v1.0.7 {#v1-0-7}

* **MDVA-30972** (*för Adobe Commerce >=2.3.0 &lt;2.4.2*) - Korrigerar problemet där status för anpassad order ändrades till *Bearbetning* efter att en del av leveransen skapats med WebApi.
* **MDVA-30428** (*för Adobe Commerce >=2.3.4 &lt;2.3.5*) - Korrigerar problemet där kunder inte kan lägga till en produkt i önskelistan om den här produkten har tilldelats en anpassad lagerkälla.
* **MDVA-30594** (*för Adobe Commerce >=2.3.0 &lt;2.4.2*) - Korrigerar problemet där det inte gick att spara en order med flera adresser vid utcheckning när FPT har konfigurerats.
* **MDVA-29148** (*för Adobe Commerce >=2.3.0 &lt;2.4.2*) - Korrigerar problemet när en produkt skapas via ett API-anrop. Det anpassade produktattributet för typen `\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend` (som Multiselect) använder inte standardvärdet om inget värde angavs i nyttolasten.
* **MDVA-30837** (*för Adobe Commerce >=2.3.1 &lt;2.3.5*) - En konfigurationsinställning har lagts till *Inkludera moms till belopp: Ja/Nej* i konfiguration av kostnadsfri leveransmetod. När *Inkludera skatt till belopp* är inställt på *Ja* beräknas minimiorderbelopp som Delsumma + moms. När *Inkludera moms till belopp* är inställt på *Nej* beräknas minimiorderbelopp som delsumma
* **MDVA-25028** (*för Adobe Commerce >=2.3.2 &lt;2.3.3 || >=2.3.5 &lt;2.3.6*) - Korrigerar problemet när order som placeras med [!DNL PayPal Payflow Pro] inte har statusen Misstänkt bedrägeri när bedrägerifilter aktiveras.
* **MDVA-31224** (*för Adobe Commerce >=2.3.3 &lt;2.3.5*) - Förbättrar prestandan för omindexeringsåtgärden `catalog_product_price` för paketprodukter.
* **MDVA-31321** (*för Adobe Commerce >=2.3.2 &lt;2.3.5*) - Korrigerar en tom sida (fel) när *Visa alla* är markerat. [!DNL Elasticsearch] returnerar en stor lista över produkt-ID:n. I det här fallet konverteras order by-satsen till ett felaktigt SQL-format.
* **MDVA-30815** (*för Adobe Commerce >=2.3.2 &lt;2.3.4*) - Korrigerar problemet där Adobe Commerce visar en tom sida när du ändrar hur många sökresultat som ska visas på sökresultatsidan. [!DNL Elasticsearch] visar nu resultat från kategorisidor korrekt när du ändrar antalet sökresultat som visas per sida.
* **MDVA-30782** (*för Adobe Commerce >=2.3.5 &lt;2.4.2*) - Korrigerar problemet där dynamiskt block visas oavsett kundvagnsregel.
* **MDVA-31021** (*för Adobe Commerce >=2.3.0 &lt;2.4.2*) - Korrigerar problemet där det finns prestandaproblem i `module-catalog-import-export/Model/Import/Product/Option.php`. Om det finns fler än ~100 kB poster i tabellen `catalog_product_option` tar det mindre än 10 sekunder att validera en ny CSV med en enskild produkt.
* **MDVA-31007** (*för Adobe Commerce >=2.4.0 &lt;2.4.1*) - Korrigerar problemet där anpassade adressattribut inte visas korrekt på sidan med orderinformation i mitt kontoområde och i serverdelen.
* **MDVA-29389** (*för Adobe Commerce >=2.3.0 &lt;2.4.2*) - Korrigerar problemet med avancerad rapportering där `analytics_collect_data` cronjob säger: *Port måste konfigureras i värdparametern (som localhost:3306)*.
* **MDVA-31343** (*för Adobe Commerce >=2.3.4 &lt;2.3.6*) - Korrigerar problemet med den borttagna brödklassen `page-layout-category-full-width` när en kategori har schemalagts.
* **MDVA-30945** (*för Adobe Commerce >=2.3.0 &lt;2.4.2*) - Korrigerar ett fel där du får ett allvarligt felmeddelande när du uppdaterar kundvagnar `Call to a member function getValue() on null in module-configurable-product CartItemProcessor.php`.

## v1.0.6 {#v1-0-6}

* **MDVA-28993** (*för Adobe Commerce >=2.3.4 &lt;2.4.0*) - Implementerar funktionen *Minimum ska matcha* och partiell sökning för motorn [!DNL Elasticsearch]. Löser problem med bindestreck i sökfrågor.
* **MDVA-30102** (*för Adobe Commerce >=2.3.2 &lt;=2.4.0*) - Korrigerar problemet där Redis-cachen växer snabbt eftersom layoutcachen inte har TTL.
* **MDVA-30599** (*för Adobe Commerce >=2.3.4 &lt;=2.4.0*) - Korrigerar problemet där gästcitat som skapats med API felaktigt markeras som citattecken för inloggade kunder.
* **MDVA-29446** (*för Adobe Commerce >=2.3.3 &lt;=2.4.0*) - Korrigerar problemet där priset för ej tillämplig leveransmetod visas som noll vid utcheckning.
* **MDVA-30357** (*för Adobe Commerce >=2.3.2 &lt;=2.4.0*) - Korrigerar problemet med fel bild-URL:er som skapas när en platskarta genereras av cron.
* **MDVA-30565** (*för Adobe Commerce >=2.3.2 &lt;=2.3.3-p1*) - Korrigerar problemet där *Ingen sådan entitet med cartid = 0*-fel visas för gästkund i kassan på butiken om en beständig kundvagn är aktiverad.
* **MDVA-29787** (*för Adobe Commerce >=2.3.0 &lt;=2.4.0*) - Korrigerar problemet där målregeln för relaterade produkter inte fungerar när *är ett av* -villkoren används för att definiera produkter som ska visas.
* **MDVA-30977** (*för Adobe Commerce >=2.3.4 &lt;=2.3.5-p2*) - Korrigerar problemet med slumpmässiga produkter som saknas i kategorier efter omindexering.
* **MDVA-28202** (*för Adobe Commerce >=2.3.4 &lt;=2.4.2*) - Korrigerar problemet där lagernavigering inte filtrerar konfigurerbara produkter korrekt när MSI används.
* **MDVA-28300** (*för Adobe Commerce >=2.3.0 &lt;2.3.6*) - Korrigerar problemet där GQL-begäran inte återspeglar prisförändringar från katalogprisregler.
* **MDVA-31006** (*för Adobe Commerce >=2.3.2 &lt;=2.4.2*) - Korrigerar problemet där dubblettorder visas efter att en beställning har gjorts med betalningen [!DNL Paypal Express].

## v1.0.5 {#v1-0-5}

* **MDVA-30841** (*för Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*) - Korrigerar problemet med lagerstyrd navigering, där *No* -värdet för booleska typproduktattribut inte inkluderades i lagerstyrd navigering om [!DNL Elasticsearch] användes som sökmotor.
* **MDVA-28191** (*för Adobe Commerce >=2.3.3 &lt;2.4.2*) - Korrigerar problemet där inga betalningsmetoder läses in när beställningar skapas via Admin.
* **MDVA-29959** (*för Adobe Commerce >=2.3.0 &lt;=2.3.3-p1 med B2B-tillägg*) - Korrigerar problemet där begränsade administratörsanvändare med *Företag* -behörigheter inte får ta bort företagskonto.
* **MDVA-30265** (*för Adobe Commerce >=2.3.3 &lt;2.4.2*) - Korrigerar problemet där länken för leveransspårning slutar fungera efter att fakturan har skapats.
* **MDVA-28409** (*för Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*) - Korrigerar problemet där `sales_clean_quotes` cron-jobbet misslyckas med felet *slut på minne* när antalet utgångna citattecken i databasen är stort.
* **MDVA-30593** (*för Adobe Commerce >=2.3.0 &lt;2.3.4*) - Korrigerar problemet där offerter som har gått ut enligt inställningen för Offerts livstid inte rensas.
* **MDVA-30107** (*för Adobe Commerce >=2.3.0 &lt;2.3.6*) - Korrigerar problemet där butiksväljaren inte fungerar som förväntat om olika bas-URL:er används för butiksvyer.
* **MDVA-28763** (*för Adobe Commerce >=2.3.2 &lt;2.3.4*) - Korrigerar problemet där produktavbildningen dupliceras efter att produktinformationen uppdaterats med REST API mer än en gång.
* **MDVA-30284** (*för Adobe Commerce >=2.3.0 &lt;2.4.2*) - Korrigerar problemet där katalogsökningsindexeraren misslyckas på grund av följande *[!DNL Elasticsearch]-fel: gränsen för det totala antalet indexfält har överskridits.*
* **MDVA-29042** (*för Adobe Commerce >=2.3.3 &lt;=2.3.4-p2 med B2B-tillägg*) - Korrigerar problemet där katalogbehörigheter ändrades till *Tillåt* automatiskt efter att en ny produkt lades till i den delade katalogen.
* **MDVA-30428** (*för Adobe Commerce >=2.3.3 &lt;2.4.2*) - Korrigerar problemet där kunder inte kan lägga till en produkt i önskelistan om den här produkten har tilldelats en anpassad lagerkälla.
* **MDVA-28661** (*för Adobe Commerce >=2.3.0 &lt;2.4.2 med B2B-tillägg*) - Korrigerar problemet där ett fel uppstår i företagsanvändarkontoavsnittet efter att företagsadministratören har ändrats.

## v1.0.4 {#v1-0-4}

* **MDVA-30195** (*för Adobe Commerce 2.3.1 - 2.3.4-p2*) - Korrigerar problemet där cron-jobb misslyckas om databasnamnet är för långt, vilket resulterar i att kategorier inte uppdateras i förgrunden.
* **MDVA-30106** (*för Adobe Commerce ^2.3.0*) - Korrigerar ett fel där betalningar under utcheckning inte läses in med *Det går inte att läsa egenskapen length för felet null* i JS-konsolen.
* **MDVA-28656** (*för Adobe Commerce >=2.3.1 &lt;2.3.6 || >=2.4.0 &lt;2.4.2*) - Korrigerar problemet där orderstatusen ändras till *Stängd* i stället för Fullständigt om en order placerades utan betalningsinformation (t.ex. med 100 % rabatt) och en faktura skapades för ordern.
* **MDVA-30209** (*för Adobe Commerce 2.3.0 - 2.3.3-p1*) - Korrigerar problemet där kundgruppen ändrades till standard om kunden uppdaterade sin kontoinformation.
* **MDVA-30123** (*för Adobe Commerce >=2.3.4 &lt;2.4.2*) - Korrigerar problemet där attributalternativetiketter inte översätts korrekt för GraphQL-frågor.
* **MDVA-29996** (*för Adobe Commerce >=2.3.3 &lt;2.4.2*) - Korrigerar problemet där kategorisidan inte cachelagras av helsidescache när kategoribehörighet har aktiverats.
* **MDVA-30164** (*för Adobe Commerce >=2.3.1 &lt;2.4.2*) - Korrigerar problemet där kundposter inte kan exporteras från kundrutnätet om det finns anpassade kundattribut.
* **MDVA-30444** (*för Adobe Commerce >=2.3.0 &lt;2.4.1*) - Korrigerar problemet där inga bekräftelsemeddelanden skickas för beställningar som gjorts med GraphQL.
* **MDVA-30490** (*för Adobe Commerce 2.3.4 - 2.3.5-p2*) - Korrigerar problemet där produktjämförelsen genererar felsidan 500 om en av produkterna har en tom kort beskrivning.
* **MDVA-30232** (*för Adobe Commerce >=2.3.1 &lt;2.4.1*) - Korrigerar problemet där det inte går att beställa om den ursprungliga ordern innehåller ett presentkort.
* **MDVA-29965** (*för Adobe Commerce >=2.3.3 &lt;2.4.0*) - Korrigerar problemet där kunderna får ett ogiltigt formulärnyckelfel när en produkt läggs till i kundvagnen.
* **MDVA-30008** (*för Adobe Commerce >=2.3.0 &lt;2.4.2*) - Korrigerar B2B-problemet där det inte går att göra beställningar via Admin API för en produkt som finns i en offentlig katalog.
* **MDVA-22469** (*för Adobe Commerce 2.3.2-p2 - 2.3.3-p1*) - Korrigerar problemet där Page Builder inte fungerar på Admin-panelen när du har uppgraderat till Adobe Commerce 2.3.3 och vissa JS- och CSS-filer inte läses in.
* **MC-35984** (*för Adobe Commerce >=2.4.0 &lt;2.4.1*) - Korrigerar problemet där handlare inte kunde interagera med några sidelement på retursidan efter att ha skapat en leveransetikett för en RMA (Return Merchandise Authorization).

## v1.0.3 {#v1-0-3}

* **MDVA-25602** (*för Adobe Commerce 2.3.0 - 2.3.4*) - Korrigerar problemet med [!DNL PayPal Payflow Pro]-betalningsmetoden och behandlar cookies som `SameSite=Lax` som standard i webbläsaren Chrome 80 och API-svaret omdirigeras till kundinloggningssidan.
* **MDVA-26694** (*för Adobe Commerce >=2.3.0 &lt;2.3.6 || 2.4.0*) - Korrigerar problemet med att produkt- och katalogcacheminnen förfaller dagligen, även om de schemalagts att förfalla annorlunda.
* **MDVA-27825** (*för Adobe Commerce >=2.3.0 &lt;2.4.1*) - Korrigerar problemet där stora mängder data inte kunde exporteras på grund av minnesläckage.
* **MDVA-29085** (*för Adobe Commerce >=2.3.0 &lt;=2.3.5-p1*) - Korrigerar B2B-problemet där inga nödvändiga nya företagsmeddelanden skickas ut om ett företag har skapats med API.
* **MDVA-29344** (*för Adobe Commerce >=2.3.5 &lt;=2.4.0-p1*) - Korrigerar problemet där Page Builder fastnar efter att text kopierats från ett rubrikelement till ett textelement.
* **MDVA-29835** (*för Adobe Commerce >2.3.1 &lt;2.4.2*) - Korrigerar problemet där presentkortsbeställningar innehöll två koder i stället för en.
* **MDVA-30052** (*för Adobe Commerce >=2.3.2-p2 &lt;2.3.5*) - Korrigerar problemet med att privat innehåll (lokal lagring) inte fylls i korrekt, vilket resulterade i prestandaproblem.
* **MDVA-30131** (*för Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*) - Korrigerar problemet med lagerstyrd navigering, där *No* -värdet för booleska typproduktattribut inte inkluderades i lagerstyrd navigering om [!DNL Elasticsearch] användes som sökmotor.
* **MDVA-35514** (*för Adobe Commerce >=2.4.0 &lt;2.4.1*) - Korrigerar problemet med att skapa en leveransetikett och lägga till beställda produkter i ett paket i det modala fönstret Skapa paket.
