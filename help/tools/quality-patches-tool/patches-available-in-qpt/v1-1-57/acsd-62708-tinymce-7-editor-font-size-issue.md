---
title: 'ACSD-62708: [!DNL TinyMCE] 7-redigerarens teckensnittsstorlek i administratörspanelen visar PT'
description: Använd patchen ACSD-62708 för att åtgärda Adobe Commerce-problemet där  [!DNL TinyMCE]  7-redigerarens teckensnittsstorlek i administratören visar PT och inte PX. Nu kan du även ange teckenstorleken i PX i stället för PT.
feature: Admin Workspace
role: Admin, Developer
exl-id: 037a5831-dbc7-4834-ab8e-9b1f765b92b2
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 0%

---

# ACSD-62708: [!DNL TinyMCE] 7-redigerarens teckensnittsstorlek i administratörspanelen visar PT

Korrigeringen ACSD-62708 åtgärdar ett problem där teckensnittsstorleken för redigeraren [!DNL TinyMCE] 7 i administrationspanelen visas i PT i stället för i PX. Med den här korrigeringen kan du ange teckenstorleken i PX. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57 är installerad. Korrigerings-ID är ACSD-62708. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7-p3

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4-p11, 2.4.5-p10, 2.4.6-p8

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Teckensnittsstorleken i PT visas i stället för PX i [!DNL TinyMCE] 7-redigeraren på admin-panelen.

<u>Steg som ska återskapas</u>:

1. Öppna produktredigeringssidan på adminpanelen.
1. Expandera avsnittet [!UICONTROL Content].
1. Kontrollera teckensnittskontrollerna i [!DNL TinyMCE]-redigeraren.

<u>Förväntade resultat</u>:

Teckensnittsstorleken ska vara i PX.

<u>Faktiska resultat</u>:

Teckensnittsstorleken är i PT.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
