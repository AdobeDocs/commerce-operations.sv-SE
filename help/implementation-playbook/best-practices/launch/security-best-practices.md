---
title: Säkra din Commerce webbplats och infrastruktur
description: Upprätthåll säkerheten genom att implementera säkerhetspraxis när du konfigurerar, konfigurerar och uppdaterar Adobe Commerce-installationer.
feature: Best Practices
exl-id: 50d8a464-6496-4e9a-b642-0c6d0eb51ba0
source-git-commit: ee7551374aa6d4ad462dd64ee3d05b934b43ce45
workflow-type: tm+mt
source-wordcount: '2000'
ht-degree: 0%

---

# Säkra din Commerce webbplats och infrastruktur

Att skapa och underhålla en säker miljö för Adobe Commerce-projekt som körs i molninfrastruktur är ett ansvar som delas mellan Adobe Commerce kunder, lösningspartners och Adobe. Syftet med den här guiden är att ge bästa praxis för kundens sida av ekvationen.

Även om du inte kan eliminera alla säkerhetsrisker, så blir säkerhetspositionen för Commerce-installationer svårare om du använder dessa bästa metoder. En säker plats och infrastruktur gör att målsättningen för skadliga attacker blir mindre attraktiv, garanterar säkerheten för lösningen och kundens känsliga information och minimerar säkerhetsrelaterade incidenter som kan orsaka störningar på platsen och kostsamma utredningar.

>[!NOTE]
>
>Mer information om roller och ansvar för att skydda och underhålla Adobe Commerce-projekt i molninfrastrukturen finns i [Delad ansvarsmodell](https://experienceleague.adobe.com/sv/docs/commerce-operations/security-and-compliance/shared-responsibility#security-responsibilities-chart)) i _Adobe Commerce Security and Compliance Guide_.

[Alla versioner som stöds](../../../release/versions.md) av:

- Adobe Commerce i molninfrastruktur
- Adobe Commerce lokalt

## Prioriterade rekommendationer

Adobe anser att följande rekommendationer har högsta prioritet för alla kunder. Implementera dessa viktiga säkerhetsrutiner för alla Commerce-installationer:

![Checklista](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Aktivera tvåfaktorautentisering för administratören och alla SSH-anslutningar**

- [Säkerhet för Commerce Admin](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/2fa/security-two-factor-authentication.html?lang=sv-SE)

- [Säkra SSH-anslutningar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/multi-factor-authentication.html?lang=sv-SE) (molninfrastruktur)

När MFA är aktiverat i ett projekt måste alla Adobe Commerce på molninfrastrukturkonton med SSH-åtkomst följa ett autentiseringsarbetsflöde. Det här arbetsflödet kräver antingen en tvåfaktorsautentiseringskod (2FA) eller en API-token och ett SSH-certifikat för att komma åt miljön.

![Checklista](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Skydda administratören**

- [Konfigurera en icke-standard-admin-URL](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/store-urls.html?lang=sv-SE#use-a-custom-admin-url) i stället för att använda standardvärdet `admin` eller en vanlig term som `backend`. Den här konfigurationen minskar exponeringen för skript som försöker få obehörig åtkomst till din plats.

- [Konfigurera avancerade säkerhetsinställningar](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-admin.html?lang=sv-SE) - Lägg till en hemlig nyckel till URL:er, ange att lösenord ska vara skiftlägeskänsliga och begränsa administratörens sessionslängd, tidsintervall för lösenordsanvändning och antalet inloggningsförsök som tillåts innan ett administratörskonto låses. Om du vill öka säkerheten konfigurerar du längden på tangentbordsinaktivitet innan den aktuella sessionen förfaller och kräver att användarnamnet och lösenordet är skiftlägeskänsliga.

- [Aktivera ReCAPTCHA](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/captcha/security-google-recaptcha.html?lang=sv-SE) om du vill skydda administratören från automatiska attacker med råstyrka.

- Följ principen om lägsta behörighet när du tilldelar [administratörsbehörigheter](https://experienceleague.adobe.com/docs/commerce-admin/systems/user-accounts/permissions.html?lang=sv-SE) till roller och roller till administratörsanvändarkonton.

![Checklista](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Uppgradera till den senaste utgåvan av Adobe Commerce**

Håll koden uppdaterad genom att [uppgradera ditt Commerce-projekt till den senaste utgåvan](#upgrade-to-the-latest-release) av Adobe Commerce, Commerce Services och tillägg, inklusive säkerhetsuppdateringar, snabbkorrigeringar och andra korrigeringar från Adobe.

![Checklista](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Skydda känsliga konfigurationsvärden**

Använd [konfigurationshantering](../../../configuration/cli/set-configuration-values.md) för att låsa kritiska konfigurationsvärden.

Kommandona `lock config` och `lock env` CLI konfigurerar miljövariabler så att de inte kan uppdateras från administratören. Kommandot skriver värdet till filen `<Commerce base dir>/app/etc/env.php`. (Information om Commerce i molninfrastrukturprojekt finns i [Lagra konfigurationshantering](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html?lang=sv-SE#sensitive-data).)

![Checklista](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Kör säkerhetssökningar**

Använd [Commerce-tjänsten för säkerhetssökning](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html?lang=sv-SE) för att övervaka alla Adobe Commerce-webbplatser för kända säkerhetsrisker och skadlig kod, och registrera dig för att få korrigeringsuppdateringar och säkerhetsmeddelanden.

## Säkerställ säkerheten för tillägg och anpassad kod

När du utökar Adobe Commerce genom att lägga till tillägg från tredje part från Adobe Commerce Marketplace, eller lägger till anpassad kod, ska du se till att anpassningarna är säkra genom att använda följande metodtips:

![Checklista](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Välj en partner- eller lösningsintegrator (SI) som är väl insatt i säkerhet** - Säkerställ säkra integreringar och säker leverans av anpassad kod genom att välja organisationer som följer säkra utvecklingsmetoder och som har en gedigen erfarenhet av att förebygga och åtgärda säkerhetsproblem.

![Checklista](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Använd säkra tillägg** - Identifiera de lämpligaste och säkraste tilläggen för Commerce-distributioner genom att konsultera lösningens integratör eller utvecklare och följa [god praxis för Adobe-tillägg](../planning/extensions.md).

- Endast källtillägg från Adobe Commerce Marketplace eller via lösningsintegratören. Om tillägget kommer från en integratör måste du se till att ägandet av tilläggslicensen kan överföras om integratorn ändras.

- Minska riskexponeringen genom att begränsa antalet tillägg och leverantörer.

- Om det är möjligt bör du granska tilläggskoden för att se om det finns säkerhet innan du integrerar med Commerce.

- Se till att PHP-utvecklare följer Adobe Commerce riktlinjer, processer och bästa säkerhetspraxis. Utvecklarna måste i synnerhet undvika att använda PHP-funktioner som kan leda till fjärrexekvering av kod eller svag kryptografi. Se [Säkerhet](https://developer.adobe.com/commerce/php/best-practices/security/) i *Best Practices for Extension Developers Guide*.

![Checklista](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Granskningskod** - Granska server- och källkodsdatabasen för att se om det finns utvecklingsrester. Kontrollera att det inte finns några tillgängliga loggfiler, offentliga Git-kataloger, tunnlar för att köra SQL-satser, databasdumpar, PHP-informationsfiler eller andra oskyddade filer som inte behövs och som kan användas i en attack.

## Uppgradera till den senaste versionen

Adobe släpper kontinuerligt uppdaterade komponenter för att förbättra säkerheten och bättre skydda kunderna mot eventuella kompromisser. Uppgradering till den senaste versionen av Adobe Commerce-programmet, installerade tjänster och tillägg och användning av aktuella korrigeringsfiler är den första och bästa skyddsåtgärden mot säkerhetshot.

Commerce släpper vanligtvis säkerhetsuppdateringar varje kvartal, men förbehåller sig rätten att göra programfixar för större säkerhetshot baserat på prioritet och andra faktorer.

Följande resurser innehåller information om tillgängliga Adobe Commerce-versioner, releasecykler samt uppgraderings- och korrigeringsprocessen:

- [Frisläppta versioner](../../../release/versions.md)
- [Produkttillgänglighet](../../../release/product-availability.md) (Adobe Commerce-tjänster och tillägg som skapats av Adobe)
- [Adobe Commerce livscykelpolicy](../../../release/lifecycle-policy.md)
- [Uppgraderingshandbok](../../../upgrade/overview.md)
- [Tillämpa patchar](../../../upgrade/patches/overview.md)

>[!TIP]
>
>Hämta den senaste säkerhetsinformationen och åtgärda kända säkerhetsproblem genom att prenumerera på [Adobe Security Notification Service](https://www.adobe.com/subscription/adbeSecurityNotifications.html).

## Utveckla en plan för katastrofåterställning

Om Commerce-sajten är hotad kan du snabbt åtgärda skador och återställa normal affärsverksamhet genom att utveckla och implementera en omfattande katastrofåterställningsplan.

Om en kund behöver återställa en Commerce-instans på grund av ett haveri kan Adobe förse kunden med säkerhetskopior. Kunden och lösningsintegratören kan utföra återställningen, om tillämpligt.

Som en del av en katastrofåterställningsplan rekommenderar Adobe starkt att kunder [exporterar sin Adobe Commerce-programkonfiguration](../../../configuration/cli/export-configuration.md) för att underlätta omdistributionen om det krävs för affärskontinuitet. Den främsta orsaken till att exportera konfigurationen till filsystemet är att systemkonfigurationen har företräde framför databaskonfigurationen. I ett skrivskyddat filsystem måste programmet distribueras om för att ändra känsliga konfigurationsinställningar, vilket ger ett extra skydd.

### Ytterligare information

**Adobe Commerce har distribuerats i molninfrastruktur**

- [Säkerhetskopiering och katastrofåterställning](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/pro-architecture.html?lang=sv-SE#backup-and-disaster-recovery)

- [Lagra konfigurationshantering för Adobe Commerce i molninfrastruktur](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html?lang=sv-SE)

**Adobe Commerce har distribuerats lokalt**

- [Exportera konfigurationsinställningar](../../../configuration/cli/export-configuration.md)

   - [Importera konfigurationsinställningar](../../../configuration/cli/import-configuration.md)

   - [Säkerhetskopiera och återställa filsystemet, mediet och databasen](../../../installation/tutorials/backup.md)

## Underhåll en säker plats och infrastruktur

I det här avsnittet sammanfattas de effektivaste strategierna för underhåll av plats- och infrastruktursäkerhet för en Adobe Commerce-installation. Många av dessa bästa metoder fokuserar på att skydda datorinfrastrukturen i allmänhet, så vissa rekommendationer kanske redan har implementerats.

![Checklista](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Blockera obehörig åtkomst** - Arbeta med din värdpartner för att konfigurera en VPN-tunnel så att obehörig åtkomst till Commerce webbplats och kunddata blockeras. Konfigurera en SSH-tunnel för att blockera obehörig åtkomst till Commerce-programmet.

![Checklista](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Använd en brandvägg för webbprogram** - Analysera trafik och upptäcka misstänkta mönster, t.ex. kreditkortsinformation som skickas till en okänd IP-adress med hjälp av en Brandvägg för webbprogram.

Adobe Commerce-installationer som distribueras i molninfrastruktur kan använda inbyggda WAF-tjänster som är tillgängliga med [Snabb integrering av tjänster](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly.html?lang=sv-SE)

![Checklista](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Konfigurera avancerade säkerhetsinställningar för lösenord** - Konfigurera starka lösenord och ändra dem minst var 90:e dag, vilket rekommenderas av PCI-datasäkerhetsstandarden i avsnitt 8.2.4. Se [Konfigurera säkerhetsinställningar för administratörer](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-admin.html?lang=sv-SE).

![Checklista](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Använd HTTPS** - Om Commerce-webbplatsen nyligen har implementerats startar du hela webbplatsen med HTTPS. Google använder inte bara HTTPS som rangordningsfaktor, utan många användare överväger inte ens att köpa från en webbplats om den inte är skyddad med HTTPS.

## Skydda mot skadlig kod

Det är alldeles för vanligt att angripa skadlig kod på e-handelsplatser, och hotskådespelare utvecklar ständigt nya sätt att få ut kreditkort och personlig information från transaktioner.

Adobe har dock funnit att de flesta webbplatskonger inte beror på en innovativ hackare. I stället utnyttjar hotskådespelare ofta befintliga, ej patchade säkerhetsluckor, dåliga lösenord och svaga ägar- och behörighetsinställningar i filsystemet.

I de vanligaste attackerna injiceras skadlig kod i en kunds absoluta sidhuvud eller absoluta sidfot. Där samlar koden in formulärdata som kunden anger i butiken, inklusive inloggningsuppgifter och utcheckningsdata för formulär. Sedan skickas dessa data till en annan plats för skadliga syften i stället för till Commerce serverdel. Dessutom kan skadlig kod utgöra ett hot mot administratören när det gäller att köra kod som ersätter det ursprungliga betalningsformuläret med ett falskt formulär som åsidosätter eventuella skydd som anges av betalningsleverantören.

Kreditkortskannrar på klientsidan är en typ av skadlig kod som bäddar in kod i handlarens webbplatsinnehåll som kan köras i en användares webbläsare, vilket visas i följande bild.

![Dataflöde för skadliga programattacker mot e-handelswebbplatser](../../../assets/playbooks/malware-data-flow.svg)

När vissa åtgärder har utförts, t.ex. en användare som skickar ett formulär eller ändrar ett fältvärde, serialiseras data och skickas till slutpunkter från tredje part. Dessa slutpunkter är vanligtvis andra komprometterade webbplatser som fungerar som ett relä för att skicka data till den slutliga destinationen.


>[!TIP]
>
>Om en Commerce-webbplats påverkas av en skadlig kod-attack följer du Adobe Commerce bästa praxis för [att svara på en säkerhetsincident](../maintenance/respond-to-security-incident.md).

### Lär känna de vanligaste attackerna

Nedan följer en lista över vanliga kategorier av attacker som Adobe rekommenderar alla Commerce-kunder att känna till och vidta åtgärder för att skydda mot:

- **Webbplatsdepåer** - En angripare skadar en webbplats genom att ändra webbplatsens visuella utseende eller lägga till egna meddelanden. Även om åtkomsten till webbplatsen och användarkontona har komprometterats är betalningsinformationen ofta skyddad.

- **Boten** - Kundens Commerce-server blir en del av ett nät som skickar skräppost. Även om användardata vanligtvis inte äventyras kan kundens domännamn blocklist av skräppostfilter, vilket förhindrar att e-post skickas från domänen. Alternativt blir kundens webbplats en del av ett botnät som orsakar en DoS-attack på en annan plats eller andra platser. Det nedre nätet kan blockera inkommande IP-trafik till Commerce-servern, vilket förhindrar att kunderna kan handla.

- **Direktserverattacker** - Data har komprometterats, bakdörrar och skadlig kod har installerats och webbplatsåtgärderna påverkas. Det är mindre troligt att betalningsinformation som inte lagras på servern äventyras genom dessa attacker.

- **Silent card capture** - I den här mest katastrofala attacken installerar inkräktare dold skadlig programvara eller programvara för kortregistrering, eller ännu värre, ändrar du kassaprocessen för att samla in kreditkortsdata. Informationen skickas sedan till en annan webbplats för försäljning på den mörka webben. Sådana attacker kan passera obemärkta under en längre period och kan leda till stora kompromisser med kundkonton och finansiell information.

- **Tyst nyckelloggning** - Hotskådespelaren installerar nyckelloggningskoden på kundservern för att samla in administratörsanvändaruppgifter så att de kan logga in och starta andra attacker utan att identifieras.

### Skydda mot lösenordsgissningsattacker

Brute force-attacker för lösenordsgissning kan leda till obehörig administratörsåtkomst. Skydda din webbplats från dessa attacker genom att följa dessa rutiner:

- Identifiera och skydda alla punkter där Commerce-installationen kan nås från utsidan.

  Du kan skydda åtkomsten till Admin, som vanligtvis kräver mest skydd, genom att följa Adobe [prioritetsrekommendationer](#priority-recommendations) när du konfigurerar ditt Commerce-projekt.

- Kontrollera åtkomsten till Commerce webbplats genom att konfigurera en åtkomstkontrollista som endast tillåter åtkomst för användare som kommer från en viss IP-adress eller ett visst nätverk.

  Du kan använda en snabb Edge ACL med ett anpassat VCL-kodfragment för att filtrera inkommande begäranden och tillåta åtkomst via IP-adress. Se [Anpassad VCL för att tillåta begäranden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-allowlist.html?lang=sv-SE).


  >[!TIP]
  >
  >Om du har en fjärransluten arbetsstyrka måste du se till att IP-adresserna för fjärranställda finns med i listan över adresser som har behörighet att komma åt Commerce webbplats.

### Förhindra clickjacking-attacker

Adobe skyddar din butik från clickjacking-attacker genom att tillhandahålla HTTP-begärandehuvudet `X-Frame-Options` som du kan inkludera i begäranden till din butik. Se [Förhindra clickjacking-attacker](../../../configuration/security/xframe-options.md) i *Adobe Commerce Configuration Guide*.
