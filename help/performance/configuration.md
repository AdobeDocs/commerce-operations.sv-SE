---
title: Bästa praxis för konfiguration
description: Optimera svarstiden för driftsättningen av Adobe Commerce eller Magento Open Source med hjälp av dessa metodtips.
source-git-commit: 20c4f55162b25be8906562c395abf4671437992b
workflow-type: tm+mt
source-wordcount: '959'
ht-degree: 0%

---


# Bästa praxis för konfiguration

I Commerce finns många inställningar och verktyg som du kan använda för att förbättra svarstiden på sidorna samt för att ge högre dataflöde.

## Kronjobb

Alla asynkrona åtgärder i [!DNL Commerce] utförs med Linux `cron` -kommando. Se [Konfigurera och kör cron](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html) för att konfigurera det korrekt.

## Indexerare

En indexerare kan köras i **[!UICONTROL Update on Save]** eller **[!UICONTROL Update on Schedule]** läge. The **[!UICONTROL Update on Save]** indexeras omedelbart när katalogen eller andra data ändras. I det här läget används låg intensitet för uppdaterings- och bläddringsåtgärder i din butik. Det kan leda till betydande förseningar och otillgänglighet av data vid höga belastningar. Vi rekommenderar att du använder **Uppdatera enligt schema** i produktionen eftersom information om datauppdateringar lagras och indexeras av delar i bakgrunden via ett specifikt kroniskt jobb. Du kan ändra läge för varje [!DNL Commerce] indexeraren separat på  **[!UICONTROL System]** > [!UICONTROL Tools] > **[!UICONTROL Index Management]** konfigurationssida.

Omindexering av MariaDB 10.4 tar längre tid jämfört med andra MariaDB eller [!DNL MySQL] versioner. Som en tillfällig lösning föreslår vi att du ändrar standardkonfigurationen för MariaDB och anger följande parametrar:

* [`optimizer_switch='rowid_filter=off'`](https://mariadb.com/kb/en/optimizer-switch/)
* [`optimizer_use_condition_selectivity = 1`](https://mariadb.com/products/skysql/docs/reference/es/system-variables/optimizer_use_condition_selectivity/)

## Cacheminnen

Aktivera alla cacheminnen från **[!UICONTROL System]** > [!UICONTROL Tools] > **[!UICONTROL Cache Management]** sida. Vi rekommenderar att du använder [!DNL Varnish], eftersom det är en effektiv cachelösning för produktionssidor.

## Asynkrona e-postmeddelanden

Om du aktiverar inställningen&quot;Asynkrona e-postmeddelanden&quot; flyttas processer som hanterar utcheckning och beställer e-postmeddelanden till bakgrunden. Om du vill aktivera den här funktionen går du till **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Sales] > [!UICONTROL Sales Emails] > [!UICONTROL General Settings] >[!UICONTROL Asynchronous Sending]**. Se [Försäljningsmejl](https://docs.magento.com/user-guide/configuration/sales/sales-emails.html) i _Användarhandbok för Magento Open Source_ för mer information.

## Asynkron bearbetning av orderdata

Det kan finnas tillfällen då intensiv försäljning sker samtidigt som [!DNL Commerce] utför intensiv orderbehandling. Du kan konfigurera [!DNL Commerce] för att särskilja dessa två trafikmönster på databasnivå för att undvika konflikter mellan läs- och skrivåtgärder i motsvarande tabeller. Du kan lagra och indexera orderdata asynkront. Beställningar läggs i tillfällig lagring och flyttas gruppvis till orderhanteringsrutnätet utan några kollisioner. Du kan aktivera det här alternativet från **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Advanced] > [!UICONTROL Developer] > [!UICONTROL Grid Settings] >[!UICONTROL Asynchronous indexing]**. Se [Schemalagda uppdateringar av stödraster](https://docs.magento.com/user-guide/sales/order-grid-updates-schedule.html) i _Användarhandbok för Magento Open Source_ för mer information.

>[!WARNING]
>
>The **[!UICONTROL Developer]** och alternativ är bara tillgängliga i [Utvecklarläge](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-mode.html). [Adobe Commerce i molninfrastruktur](https://devdocs.magento.com/cloud/requirements/cloud-requirements.html#cloud-req-test) stöder inte `Developer` läge.

## Uppskjuten lageruppdatering

I tider med intensiv försäljning [!DNL Commerce] kan skjuta upp lageruppdateringar relaterade till order. Detta minimerar antalet åtgärder och snabbar upp orderplaceringsprocessen. Det här alternativet är dock riskabelt och kan bara användas när restorder aktiveras i butiken, eftersom det här alternativet kan leda till negativa lagerkvantiteter. Det här alternativet kan ge avsevärda prestandaförbättringar i utcheckningsflöden för butiker som enkelt kan fylla i sitt lager på begäran. Om du vill aktivera fördröjda Stock-uppdateringar på din webbplats går du till **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Catalog] > [!UICONTROL Inventory] > [!UICONTROL Product Stock Options] >[!UICONTROL Use Deferred Stock Update]**. Se [Hantera lager](https://docs.magento.com/user-guide/catalog/inventory.html) i _Adobe Commerce Användarhandbok_ för mer information.

>[!INFO]
>
>Det här alternativet är bara tillgängligt om **[!UICONTROL Backorder with any mode]** är aktiverat.

## Optimeringsinställningar på klientsidan

För att förbättra svarstiderna på marknaden [!DNL Commerce] Gå till Admin i standardläge eller utvecklarläge och ändra följande inställningar:

**[!UICONTROL Stores]-> [!UICONTROL Configuration] -> [!UICONTROL Advanced] -> [!UICONTROL Developer]:**

| Inställningsgrupp | Inställning | Värde |
| ------------------- | -------------------------- | ------ |
| Stödrasterinställningar | Asynkron indexering | Aktivera |
| CSS-inställningar | Minimera CSS-filer | Ja |
| [!DNL JavaScript] Inställningar | Minify [!DNL JavaScript] Filer | Ja |
| [!DNL JavaScript] Inställningar | Aktivera [!DNL JavaScript] Paket | Ja |
| Mallinställningar | Minfy HTML | Ja |

>[!INFO]
>
>The **[!UICONTROL Developer]** och alternativ är bara tillgängliga i [Utvecklarläge](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-mode.html). [Adobe [!DNL Commerce] om molninfrastruktur](https://devdocs.magento.com/cloud/requirements/cloud-requirements.html#cloud-req-test) stöder inte `Developer` läge.

När du aktiverar **[!UICONTROL Enable [!DNL JavaScript] Bundling]** kan du tillåta att Commerce sammanfogar alla JS-resurser till ett eller flera paket som är inlästa på butikssidor. Paketeringen av JS resulterar i färre begäranden till servern, vilket förbättrar sidans prestanda. Det hjälper även webbläsaren att cachelagra JS-resurser vid det första anropet och återanvända dem för all vidare surfning. Det här alternativet ger även en lat utvärdering eftersom all JS läses in som text. Den initierar bara analys och utvärdering av kod efter att specifika åtgärder har utlösts på sidan. Den här inställningen rekommenderas dock inte för butiker där den första sidans laddningstid är extremt viktig eftersom allt JS-innehåll läses in vid det första anropet.

>[!INFO]
>
>Se [Optimering av CSS- och Javascript-filer på Adobe Commerce i molninfrastrukturen och Adobe Commerce](https://support.magento.com/hc/en-us/articles/360044482152) i Adobe Commerce Help Center_ om du vill ha mer information om hur du optimerar CSS och Javascript.

### Pakettips

* Vi rekommenderar att du använder verktyg från tredje part för miniatyr- och paketering (som [r.js](http://requirejs.org/)). [!DNL Commerce] Inbyggda mekanismer är inte optimala och levereras som reservalternativ.
* Att aktivera HTTP2-protokollet kan vara ett bra alternativ till att använda JS-paketering. Protokollet ger i stort sett samma fördelar.
* Vi rekommenderar inte att du använder föråldrade inställningar som att sammanfoga JS- och CSS-filer, eftersom de bara är utformade för synkront inläst JS i sidans HEAD-avsnitt. Om du använder den här tekniken kan paketeringen och requireJS-logiken fungera felaktigt.

## Databasunderhållsschema {#database}

Vi rekommenderar att du gör regelbundna databassäkerhetskopieringar för instanserna Staging och Production. På grund av I/O-intensiva säkerhetskopieringsåtgärder kan det uppstå långsammare säkerhetskopiering och potentiella problem. Att köra databasprocesser för flera miljöer samtidigt kan eventuellt gå långsammare på grund av att det finns invändningar mot tillgängliga resurser.

För bättre prestanda bör du schemalägga säkerhetskopieringar så att de körs i följd, en åt gången, vid låg belastning. Med den här metoden undviker du I/O-problem och förkortar tiden för slutförande, särskilt för mindre instanser, större databaser och så vidare.

Vi rekommenderar till exempel att du schemalägger en säkerhetskopia av din produktionsdatabas som följs av mellanlagringsdatabasen när dina butiker stöter på lägre besök.
