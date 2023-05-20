---
title: Förhindra och hantera säkerhetstillbud
description: Lär dig mer om de bästa sätten att undvika och hantera säkerhetsincidenter i ditt Adobe Commerce-projekt för molninfrastruktur.
role: Admin, Developer, Leader, User
feature-set: Commerce
feature: Best Practices
exl-id: 77275d37-4f1d-462d-ba11-29432791da6a
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1073'
ht-degree: 0%

---

# Bästa metoder för att förebygga och hantera säkerhetstillbud

Adobe Commerce säkerhetsverksamhet [Delat ansvar](https://www.adobe.com/content/dam/cc/en/trust-center/ungated/whitepapers/experience-cloud/adobe-commerce-shared-responsibility-guide.pdf) modell. Det är viktigt att förstå vad Adobe och era tekniska team ansvarar för. Nedan sammanfattas [Bästa praxis för säkerhet](https://www.adobe.com/content/dam/cc/en/security/pdfs/Adobe-Magento-Commerce-Best-Practices-Guide.pdf) för att säkerställa att ditt projekt har de bästa säkerhetskontrollerna och hur du bäst hanterar en säkerhetsincident.

## Berörda produkter och versioner

[Alla versioner som stöds](../../../release/versions.md) av:

- Adobe Commerce i molninfrastruktur

## Svara på en incident

Det finns många saker du bör tänka på när du reagerar på en säkerhetsincident. Om du misstänker att du nyligen har råkat ut för en säkerhetsincident i ditt Adobe Commerce-infrastrukturprojekt i molnet är det viktigt att du granskar alla administratörsbehörigheter, aktiverar avancerade MFA-kontroller (multi-factor authentication), bevarar viktiga loggar och granskar säkerhetsuppgraderingar för din version av Adobe Commerce.

Fler rekommendationer finns nedan. De kan hjälpa till att förhindra obehörig åtkomst och påbörja processen för ytterligare incidentanalys.

## Hur man förhindrar säkerhetsincidenter

Följ de här bästa säkerhetsrutinerna för att proaktivt förhindra säkerhetsincidenter som påverkar Adobe Commerce webbplatser och butiker:

- [Aktivera 2FA för administratörsåtkomst](https://docs.magento.com/user-guide/stores/security-two-factor-authentication.html).
Tvåfaktorsautentisering används ofta och det är vanligt att generera åtkomstkoder för olika webbplatser i samma app. Detta garanterar att bara du kan logga in på ditt användarkonto. Om du tappar bort ditt lösenord eller om någon gissar det lägger tvåfaktorsautentisering till ett skyddslager.
- [Aktivera MFA för SSH-åtkomst](https://devdocs.magento.com/cloud/project/project-enable-mfa-enforcement.html).
När MFA är aktiverat i ett projekt måste alla Adobe Commerce-konton för molninfrastruktur med SSH-åtkomst följa ett autentiseringsarbetsflöde som kräver antingen en tvåfaktorsautentiseringskod (2FA) eller en API-token och ett SSH-certifikat för att få tillgång till miljön.
- Uppgradera till den senaste utgåvan av Adobe Commerce.
Adobe släpper säkerhets- och funktionspatchar för varje version av Adobe Commerce som stöds.
- Konfigurera och använda en [icke-standardadministratörs-URL](https://docs.magento.com/user-guide/stores/store-urls-custom-admin.html).
Adobe rekommenderar att du använder en unik, anpassad Admin-URL i stället för standardadressen `admin` eller en vanlig term som *serverdel*. Även om den här konfigurationsändringen inte direkt skyddar din webbplats från en bestämd skadad skådespelare kan den minska exponeringen för skript som försöker få obehörig åtkomst.
- Förhindra att konfigurationsvärden redigeras eller uppdateras i administratören med hjälp av  [`bin/magento config:set` CLI-kommando med `lock env` konfigurationsalternativ](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/configuration-management/set-configuration-values.html#set-configuration-values-that-cannot-be-edited-in-the-admin). Det här alternativet låser antingen konfigurationsvärdet så att det inte kan redigeras i administratören, eller förhindrar ändringar i en inställning som redan är låst. När du använder det här alternativet skrivs konfigurationsändringarna till `<Commerce base dir>/app/etc/env.php` -fil.
- Konfigurera och kör [Adobe Commerce Security Scan Tool](https://docs.magento.com/user-guide/magento/security-scan.html).
Med den förbättrade säkerhetssökningen kan du övervaka var och en av dina Adobe Commerce-sajter, inklusive PWA, för att upptäcka kända säkerhetsrisker och skadlig kod samt få korrigeringsuppdateringar och säkerhetsmeddelanden.
- [Granska och uppdatera administratörsanvändaråtkomst](https://docs.magento.com/user-guide/system/permissions-users-all.html) och [säkerhetsinställningar](https://docs.magento.com/user-guide/stores/security-admin.html).
   - Vi rekommenderar att du tar bort gamla, oanvända eller misstänkta konton och roterar lösenord för alla administratörsanvändare.
   - Granska och uppdatera de avancerade säkerhetsinställningarna&lt; för ditt projekt. Med säkerhetskonfigurationen för Admin kan du lägga till en hemlig nyckel till URL:er, kräva att lösenord är skiftlägeskänsliga och begränsa längden på Admin-sessioner, inklusive lösenordens livstid och antalet inloggningsförsök som kan göras innan Admin-användarkontot låses. För ökad säkerhet kan du konfigurera längden på tangentbordsinaktivitet innan den aktuella sessionen förfaller och kräva att användarnamnet och lösenordet är skiftlägeskänsliga.
- Granska Adobe Commerce på [användare av molnprojekt](https://devdocs.magento.com/cloud/project/user-admin.html).
Vi rekommenderar att du tar bort gamla, oanvända eller misstänkta konton och begär att användarna ska ändra sina lösenord.
- Granskning [SSH-nycklar](https://devdocs.magento.com/cloud/before/before-workspace-ssh.html) för Adobe Commerce om molninfrastruktur.
Vi rekommenderar att du granskar, tar bort och roterar SSH-nycklar.
- Implementera ACL (Access Control List) för Admin.
Du kan använda en ACL-lista med fast kant i kombination med en anpassad [VCL-kodfragment](https://devdocs.magento.com/cloud/cdn/fastly-vcl-allowlist.html#vcl) för att filtrera inkommande begäranden och tillåta åtkomst via IP-adress till administratören.

## Analysera en incident

Det första steget i incidentanalysen är att samla in så många fakta du kan, så snabbt du kan. Genom att samla in information kring incidenten kan du fastställa den potentiella orsaken till incidenten. Adobe Commerce tillhandahåller verktygen nedan som kan underlätta incidentanalysen.

- [Granska administratörsåtgärdsloggar](https://docs.magento.com/user-guide/system/action-log-report.html).
Rapporten Åtgärdsloggar innehåller en detaljerad beskrivning av alla administratörsåtgärder som har aktiverats för loggning. Varje post är tidstämplad och registrerar användarens IP-adress och namn. Logginformationen innehåller administratörsanvändardata och relaterade ändringar som gjordes under åtgärden.
- Analysera händelser med [Observera för Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-operations/tools/observation-for-adobe-commerce/intro.html?lang=en).
Med verktyget Observation for Adobe Commerce kan du analysera komplexa problem för att identifiera rotorsaker. Istället för att spåra olika data kan ni lägga tid på att korrelera händelser och fel för att få djupare insikter i orsakerna till flaskhalsar i prestandan.
Verktyget är avsett att ge en tydlig bild av några av de potentiella platsproblemen så att du kan identifiera grundorsaken och se till att webbplatserna fungerar optimalt. Klicka på länken till dokumentationen för verktyget Observation for Adobe Commerce ovan om du vill visa verktygets dokumentation. Det finns ett avsnitt i dokumentationen som innehåller all information som finns på sidan **Säkerhet** -fliken.
- Analysera loggar med [New Relic Logs](https://devdocs.magento.com/cloud/project/new-relic.html#new-relic-logs). Adobe Commerce om molninfrastruktur Pro-projekten innefattar [New Relic Logs](https://docs.newrelic.com/docs/logs/new-relic-logs/get-started/introduction-new-relic-logs) service. Tjänsten är förkonfigurerad för att samla alla loggdata från dina förproduktionsmiljöer så att de kan visas på en central kontrollpanel för logghantering.
Du kan använda tjänsten New Relic Logs för att utföra följande uppgifter:
   - Använd [New Relic-frågor](https://docs.newrelic.com/docs/logs/new-relic-logs/ui-data/query-syntax-logs) om du vill söka efter aggregerade loggdata.
   - Visualisera loggdata via programmet New Relic Logs.

## Ytterligare information

- [Rotorsaksanalysramverk](https://sansec.io/kb/incident-response/magento-root-cause-analysis).
