---
title: "ACSD-60804: Om du redigerar en kund som är associerad med ett borttaget företag uppstår ett fel"
description: Använd patchen ACSD-60804 för att åtgärda Adobe Commerce-problemet där redigering av en kund som är associerad med ett borttaget företag orsakar ett fel *Anrop till medlemsfunktionen getSuperUserId() på null*.
feature: Companies, Customers, B2B
role: Admin, Developer
source-git-commit: 1231dac065565ff636424673a15ae4148a5f84dd
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 0%

---

# ACSD-60804: Om du redigerar en kund som är associerad med ett borttaget företag uppstår ett fel

Korrigeringen ACSD-60804 åtgärdar ett problem där redigering av en kund som är associerad med ett borttaget företag orsakar felet *Anrop till en medlemsfunktion getSuperUserId() på null*. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.53 har installerats. Korrigerings-ID är ACSD-60804. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

Adobe Commerce (alla distributionsmetoder) 2.4.6-p2

**Kompatibel med Adobe Commerce-versioner:**

Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Om du redigerar en kund som är associerad med ett borttaget företag uppstår felet *Anrop till en medlemsfunktion getSuperUserId() på null*.

<u>Krav:</u>:

Installera och aktivera Adobe Commerce B2B-moduler.

<u>Steg som ska återskapas</u>:

1. Gå till **[!UICONTROL Settings]** > **[!UICONTROL B2B]** > **[!UICONTROL Enable Company]**.
1. Gå till **[!UICONTROL Customers]** > **[!UICONTROL Company]** > **[!UICONTROL Create New Company]**.
1. Logga in på `mysql` för instansen.
1. Ta bort företaget där `entity_id` = *1*.
1. Gå till **[!UICONTROL Customers]** > **[!UICONTROL All Customers]**.
1. Redigera kunden som skapades automatiskt när du skapade företaget.

<u>Förväntade resultat</u>:

Kunden redigeras utan ett undantagsfel.

<u>Faktiska resultat</u>:

Ett fel inträffar: *Anrop till en medlemsfunktion getSuperUserId() på null* om inget företag är associerat med kunden.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.