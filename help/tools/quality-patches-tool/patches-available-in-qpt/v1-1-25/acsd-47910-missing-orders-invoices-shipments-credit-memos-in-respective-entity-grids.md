---
title: 'ACSD-47910: saknade order, fakturor, leveranser, kreditnotor i respektive entitetsnät'
description: Använd patchen ACSD-47910 för att åtgärda Adobe Commerce-problemet där det saknas order, fakturor, leveranser och kreditnotor i respektive enhetsrutnät.
feature: Admin Workspace, Invoices, Orders, Returns, Shipping/Delivery
role: Admin
exl-id: 09115cf3-62c3-425e-bc99-e8971398dd20
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-47910: saknade order, fakturor, leveranser och kreditnotor i respektive enhetsrutnät

Korrigeringen för ACSD-47910 åtgärdar ett problem där det saknas order, fakturor, leveranser och kreditnotor i respektive enhetsrutnät. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.25 är installerad. Korrigerings-ID är ACSD-47910. Versionen där problemet kommer att åtgärdas är inte tillgänglig än.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**
* Adobe Commerce (alla distributionsmetoder) 2.4.4-p1

**Kompatibel med Adobe Commerce-versioner:**
* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.5-p4

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Ordernummer, fakturor, leveranser och kreditnotor saknas i respektive entitetsrutnät.

<u>Steg som ska återskapas</u>:

1. Aktivera **[!UICONTROL Asynchronous indexing]** på **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Developer]** > **[!UICONTROL Grid Settings]**.
1. Beställ två.
1. Kör kronen för att synkronisera beställningarna till rutnätet.
1. Öppna en av beställningarna och gör den klar för fakturering. SKICKA INTE FAKTURAN ÄN.
1. Gör en ny beställning klar att placeras på frontend. KLICKA INTE PÅ PLATSORDNINGSKNAPPEN ÄN.
1. Lägg till en `sleep(30)` i `foreach` vid `NotSyncedDataProvider::L43`.
1. Kör `bin/magento cron:run`.
1. Beställ nu.
1. Fakturera föregående order.
1. Kör kron igen och väntar på att den nya ordern ska synkroniseras.
1. Gå till orderrastret i Admin.

<u>Förväntade resultat</u>:

Den nya ordningen ska visas i orderrastret.

<u>Faktiska resultat</u>:

Den tidigare orderuppdateringen har synkroniserats med rutnätet (**[!UICONTROL status: Processing]**). Den nya ordningen visas aldrig i rutnätet.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
