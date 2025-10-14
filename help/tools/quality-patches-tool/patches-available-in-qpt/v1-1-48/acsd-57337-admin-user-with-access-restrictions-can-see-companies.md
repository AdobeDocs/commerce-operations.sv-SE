---
title: 'ACSD-57337: Administratörsanvändare med åtkomstbegränsningar kan visa alla företag i rutnätet *Företag*'
description: Använd patchen ACSD-57337 för att åtgärda Adobe Commerce-problemet där en administratörsanvändare med åtkomstbegränsningar för specifika webbplatser kan visa företag från alla webbplatser i rutnätet *Companies*.
feature: Companies, B2B, Configuration
role: Admin, Developer
exl-id: 7a05d335-5ed8-460e-80c4-dbc51d06c5bd
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# ACSD-57337: Administratörsanvändare med åtkomstbegränsningar kan visa alla företag i stödrastret *Företag*

Korrigeringen ACSD-57337 åtgärdar ett problem där en administratörsanvändare med åtkomstbegränsningar för specifika webbplatser kan visa företag från alla webbplatser i rutnätet *Companies*. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.48 har installerats. Korrigerings-ID är ACSD-57337. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.5.0.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.5-p6

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

En administratörsanvändare med åtkomstbegränsningar för specifika webbplatser kan visa företag från alla webbplatser i stödrastret *Företag* .

<u>Steg som ska återskapas</u>:

1. Skapa ytterligare en webbplats, lagra och förvara.
1. Skapa några företag som har tilldelats olika webbplatser.
1. Skapa en administratörsanvändarroll och ange rollomfånget till den skapade webbplatsen.
1. Skapa en administratör och tilldela den till den skapade rollen.
1. Logga in med en ny administratör.
1. Öppna **[!UICONTROL Customers]** > **[!UICONTROL Companies]** och observera listan över företag.

<u>Förväntade resultat</u>:

De företag som har tilldelats den extra webbplatsen visas i rutnätet *Företag* .

<u>Faktiska resultat</u>:

Alla företag visas i rutnätet *Företag*.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning &#x200B;](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
