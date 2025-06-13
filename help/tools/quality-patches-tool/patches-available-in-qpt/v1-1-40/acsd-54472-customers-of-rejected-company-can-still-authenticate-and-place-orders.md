---
title: 'ACSD-54472: Kunder i ett avvisat företag kan fortfarande autentisera'
description: Använd patchen ACSD-54472 för att åtgärda Adobe Commerce-problemet där kunderna i ett avvisat företag fortfarande kan autentisera och kunder i ett blockerat och avvisat företag fortfarande kan göra beställningar.
feature: B2B
role: Admin, Developer
exl-id: c0bd960f-609b-4253-9fc8-dc47fbbddc93
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---

# ACSD-54472: Kunder i ett avvisat företag kan fortfarande autentisera

Korrigeringen ACSD-54472 åtgärdar ett problem där kunder i ett avvisat företag fortfarande kan autentisera och kunder i ett blockerat och avvisat företag fortfarande kan göra beställningar. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.40 har installerats. Korrigerings-ID är ACSD-54472. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Kunderna i ett avvisat företag kan fortfarande autentisera, och kunder i ett blockerat och avvisat företag kan fortfarande göra beställningar.

<u>Steg som ska återskapas</u>:

1. Skapa ett företag.
1. Lägg till produkter i kundvagnen via [!DNL GraphQL].
1. Ändra företagsstatus till *Blockerad*.
1. Skicka en [!DNL GraphQL]-begäran om att lägga ordern och skapa en överlåtbar offert.
1. Ändra företagsstatus till *Avvisad*.
1. Skicka en [!DNL GraphQL]-begäran för att hämta företagets token för användarauktorisering.
1. Ange kundstatus till *Inaktiv*.
1. Skicka en [!DNL GraphQL]-begäran för att hämta företagets token för användarauktorisering.

<u>Förväntade resultat</u>:

* Beställning och överlåtbar offert placeras inte av användaren av företaget *Blocked*.
* Ingen auktoriseringstoken har hämtats för användaren av företaget *Rejected*.
* Ingen auktoriseringstoken har hämtats för kunden *Inaktiv*.

<u>Faktiska resultat</u>:

* Beställning och överlåtbar offert görs av användaren av företaget *Blocked*.
* Auktoriseringstoken hämtas för användaren av företaget *Rejected*.
* Auktoriseringstoken hämtas för kunden *Inaktiv*.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
