---
title: 'ACSD-51845: Det går inte att uppdatera efterföljande produkter med nivåpriser och olika attributuppsättningar via en synkroniserad bulk [!DNL API]'
description: Använd korrigeringsfilen ACSD-51845 för att åtgärda Adobe Commerce-problemet, där du inte kan uppdatera efterföljande produkter med nivåpriser och olika attributuppsättningar via asynkron bulk [!DNL REST API].
feature: REST, Products
role: Admin
exl-id: 83d97946-83da-4c1b-8f2a-21a64ee84e93
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# ACSD-51845: Det går inte att uppdatera efterföljande produkter med nivåpriser och olika attributuppsättningar via en synkroniserad bulk [!DNL API]

Korrigeringen ACSD-51845 åtgärdar ett problem där du inte kan uppdatera efterföljande produkter med nivåpriser och olika attributuppsättningar via asynkron bulk [!DNL REST API]. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.35 har installerats. Korrigerings-ID är ACSD-51845. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.6-p1

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Uppdateringen misslyckas för efterföljande produkter med nivåpriser och olika attributuppsättningar via asynkron bulk [!DNL REST API].

<u>Steg som ska återskapas</u>:

1. Konfigurera [!DNL RabbitMQ].
1. Skapa två attribut.
1. Skapa två **enkla produkter** och tilldela varje produkt till en annan attributuppsättning.
1. Lägg till ett **kundgruppspris** för varje produkt.
1. Uppdatera båda produkterna i samma [!DNL API]-gruppuppdatering.
1. Kontrollera att kommandot `bin/magento queue:consumers:start async.operations.all` körs.
1. Kontrollera massstatus för [!DNL API].

<u>Förväntade resultat</u>:

Tjänsten har körts.

<u>Faktiska resultat</u>:

Systemet returnerar felmeddelandet: *Produkten kunde inte sparas. Försök igen.*

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
