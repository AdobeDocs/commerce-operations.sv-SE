---
title: 'ACSD-56515: Administratör med webbplatsbehörighet kan inte redigera [!UICONTROL Dynamic Block]'
description: Använd korrigeringsfilen ACSD-56515 för att åtgärda Adobe Commerce-problemet där administratören med behörighet på webbplatsnivå inte kan lägga till eller redigera [!UICONTROL Dynamic Block].
feature: Roles/Permissions, Admin Workspace
role: Admin, Developer
exl-id: dd3e61a4-aba4-4f86-b4fe-88ca4276ace5
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---

# ACSD-56515: Administratör med webbplatsbehörighet kan inte redigera [!UICONTROL Dynamic Block]

ACSD-56515-korrigeringen åtgärdar ett problem där administratören med behörighet på webbplatsnivå inte kan lägga till eller redigera [!UICONTROL Dynamic Block]. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.45 har installerats. Korrigerings-ID är ACSD-56515. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p4

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Administratören med behörighet på webbplatsnivå kan inte lägga till eller redigera [!UICONTROL Dynamic Block].

<u>Steg som ska återskapas</u>:

1. Skapa en sekundär webbplats med butiker och butiksmaterial.
1. Gå till **[!UICONTROL System]** > **[!UICONTROL Permissions]** > **[!UICONTROL User Roles]** och skapa en användarroll som är begränsad till den sekundära webbplatsomfånget med alla tillgängliga resurser.
1. Skapa en administratörsanvändare med rollen som skapas ovan.
1. Logga in med den begränsade administratörsanvändaren och skapa en [!UICONTROL Dynamic Block].

<u>Förväntade resultat</u>:

Administratörsanvändaren med begränsningar för webbplatsen kan skapa en [!UICONTROL Dynamic Block].

<u>Faktiska resultat</u>:

Du får följande fel: *Fler behörigheter krävs för att visa objektet*.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
