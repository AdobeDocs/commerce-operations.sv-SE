---
title: 'ACSD-56858: Skillnad i rollbehörigheter i B2B-företagsadministratör'
description: Använd patchen ACSD-56858 för att åtgärda Adobe Commerce-problemet där rollbehörigheter visas felaktigt för en företagsadministratör med begränsat tillstånd i B2B-miljön.
feature: Companies, B2B, Roles/Permissions
role: Admin, Developer
exl-id: 28f90c8b-5d8b-4444-99ef-c91cfb5d6081
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '436'
ht-degree: 0%

---

# ACSD-56858: Skillnad i rollbehörigheter i B2B-företagsadministratör

Korrigeringen ACSD-56858 åtgärdar ett problem där rollbehörigheter felaktigt visas för en företagsadministratör med begränsat tillstånd i B2B-miljön. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.47 har installerats. Korrigerings-ID är ACSD-56858. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p3

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2 - 2.4.6-p4

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Rollbehörigheterna för en begränsad företagsadministratör i B2B-miljön visas felaktigt.

<u>Steg som ska återskapas</u>:

1. Börja med att konfigurera ett företag och lägga till en företagsadministratör och företagsanvändare.
1. Logga in som företagsadministratör i butiken och skapa olika roller för olika användare.
1. Tilldela de här rollerna efter behov, till exempel för att begränsa åtkomsten för vissa uppgifter samtidigt som du ger fullständig åtkomst för andra.
1. Tilldela de här rollerna fullständig åtkomst till en annan användare än företagsadministratören.
1. Logga in på en icke-företagsanvändare, t.ex. en company_manager.
1. Navigera till **[!UICONTROL Roles and permission]** och redigera rollen.
1. Observera att behörigheterna som visas inte matchar behörigheterna som anges i företagets databas för det roll-ID:t.

<u>Förväntade resultat</u>:

Roller och behörigheter visas korrekt för den icke-företagsinterna administratörsanvändaren.

<u>Faktiska resultat</u>:

Rollerna visas inte korrekt för den icke-företagsinterna administratörsanvändaren enligt databasposterna i behörighetstabellen.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool]
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i guiden för Commerce om molninfrastruktur

## Relaterad läsning

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool]
* [Metodtips för att ändra databastabeller](https://experienceleague.adobe.com/sv/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) i Commerce Implementeringspellbook

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
