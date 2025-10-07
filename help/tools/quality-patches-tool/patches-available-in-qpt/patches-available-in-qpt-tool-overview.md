---
title: Patchar tillgängliga i QPT-verktyget - översikt
description: Den här artikeln innehåller en översikt över  [!DNL Quality Patches Tool] (QPT) och länkar till resurser som förklarar hur den används.
feature: Support, Tools and External Services
role: Admin
exl-id: e67e5823-d878-4efc-90af-c7bb8c59d654
type: Troubleshooting
source-git-commit: 4caabd1578e56b74600441c9c779b7b2dfd06987
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# Patchar tillgängliga i QPT-verktyget - översikt

Den här artikeln innehåller en översikt över [!DNL Quality Patches Tool] (QPT) och länkar till resurser som förklarar hur den används.

## Berörda produkter och versioner

* Adobe Commerce lokalt, alla [versioner som stöds](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)
* Adobe Commerce i molninfrastrukturen, alla [versioner som stöds](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Vad är kvalitetsverktyget?

[[!DNL Quality Patches Tool]](https://github.com/magento/quality-patches) (QPT) är ett verktyg som gör att du kan använda enskilda kvalitetspatchar som utvecklats av Adobe och Magento Open Source-communityn.

Du kan:

* lägg in kvalitetspatchar i paketet
* återställa tidigare använda patchar
* visa allmän information om kvalitetsuppdateringar för den installerade versionen av Adobe Commerce.

Här är ett exempel på statustabellen som du kan hämta för att visa tillgängliga korrigeringar:

![Statustabell för kvalitetspatchar som visar tillgängliga korrigeringar och deras installationsstatus](/help/assets/tools/status_table.png)

Verktyget är avsett att göra det möjligt för dig att använda korrigeringsfiler för problem som du kan uppleva hos Adobe Commerce, eller att enkelt tillämpa korrigeringsfiler som Adobe Commerce support föreslår.

>[!NOTE]
>
>QPT är endast till för kvalitetspatchar. Säkerhetsuppdateringar finns i [versionsinformationen för Adobe Commerce och Magento Open Source](https://experienceleague.adobe.com/docs/commerce-operations/release/notes/overview.html?lang=sv-SE).

## Patchar tillgängliga i [!DNL Quality Patches Tool]

I det här avsnittet av Adobe Commerce Support Knowledge Base hittar du detaljerade beskrivningar av de problem som åtgärdats med QPT-korrigeringar, grupperade efter QPT-version.
Du kan också se en lista över tillgängliga QPT-korrigeringar och filtrera efter komponent med hjälp av den dynamiskt genererade tabellen på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i vår kunskapsbas för support.

## Så här installerar och använder du [!DNL Quality Patches Tool]

Installations- och användningskommandona skiljer sig åt för Adobe Commerce lokalt och Adobe Commerce i molninfrastrukturen, eftersom QPT-paketet ingår i paketet med komponentverktyg för molnet.

### Installera och använda QPT för Adobe Commerce lokalt

Mer information om hur du installerar och använder QPT för att tillämpa och återställa korrigeringsfiler finns i [Commerce > Verktyg > Användning](../usage.md) i utvecklardokumentationen.

### Installera och använda QPT för Adobe Commerce i molninfrastrukturen

Mer information om hur du installerar och använder QPT för att tillämpa och återställa korrigeringsfiler på Adobe Commerce i molninfrastrukturen finns i [Commerce i molninfrastrukturguiden > Tillämpa korrigeringsfiler](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i utvecklardokumentationen.

## Relaterad läsning

* [[!DNL Quality Patches Tool] versionsinformation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/release-notes.html?lang=sv-SE) i utvecklardokumentationen.
