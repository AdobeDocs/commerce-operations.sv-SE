---
title: 'ACSD-59280: Fel i "ReflectionUnionType::getName()" i 2.4.4-pX-installationer'
description: Använd patchen ACSD-59280 för att åtgärda Adobe Commerce-problemet där felet "anrop till undefined method ReflectionUnionType::getName()" inträffar under installationen av version 2.4.4-pX.
feature: Install, Upgrade
role: Admin, Developer
exl-id: 5a47dad4-4490-4e3d-93f2-9b176fb144d9
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 0%

---

# ACSD-59280: `ReflectionUnionType::getName()`-fel i 2.4.4-pX-installationer

Korrigeringen ACSD-59280 åtgärdar ett problem där felet `call to undefined method ReflectionUnionType::getName()` inträffar under installationen av 2.4.4-pX-versioner. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.50 är installerad. Korrigerings-ID är ACSD-59280. Observera att problemet har åtgärdats i Adobe Commerce 2.4.5.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4-p8

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.4-p10

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

`ReflectionUnionType::getName()` fel under 2.4.4-pX-installation.

<u>Steg som ska återskapas</u>:

Utför en ny installation med *[!UICONTROL Composer]*.

<u>Förväntade resultat</u>:

Installationsprocessen slutförs utan fel.

<u>Faktiska resultat</u>:

Följande fel visas under `setup:upgrade`-processen:

`Call to undefined method ReflectionUnionType::getName()`

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
