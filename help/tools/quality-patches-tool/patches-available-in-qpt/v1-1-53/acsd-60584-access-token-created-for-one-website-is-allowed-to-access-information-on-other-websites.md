---
title: 'ACSD-60584: Åtkomsttoken som skapats för en webbplats har åtkomst till information på andra webbplatser'
description: Använd korrigeringsfilen ACSD-60584 för att åtgärda problemet där åtkomsttoken som skapats för användaren på en webbplats kan få åtkomst till eller ändra kundinformation på andra webbplatser.
feature: Customers, GraphQL
role: Admin, Developer
exl-id: ea30ba92-4b7b-44f9-a1b1-97946061d9e6
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---

# ACSD-60584: Åtkomsttoken som skapats för en webbplats har åtkomst till information på andra webbplatser

Korrigeringen ACSD-60584 åtgärdar ett problem där den åtkomsttoken som skapats för användaren på en webbplats kan komma åt eller ändra kundinformation på andra webbplatser. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=sv-SE) 1.1.53 är installerad. Korrigerings-ID är ACSD-60584. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5 - 2.4.6-p8

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Med API-token som skapats för användaren på en webbplats kan du få tillgång till kundinformation, skapa en kundvagn och lägga till produkter i kundvagnen på andra webbplatsvyer.

<u>Steg som ska återskapas</u>:

1. Kontrollera att **[!DNL Share Customer Accounts configuration]** är inställt på **[!UICONTROL Per Website]**.
1. Skapa ytterligare *webbplats*, *butik* och *storeview*.
1. Skapa två kunder med samma e-postadress på *huvudwebbplatsen* och *webbplatsen* från föregående steg.
1. Generera en kundtoken via [!DNL GraphQL] på huvudwebbplatsen.
1. Använd den genererade token och skicka en kundfråga **[!DNL GraphQL]** med den andra webbplatsen i huvudet för att hämta kundinformation.
1. Observera det returnerade resultatet.

<u>Förväntade resultat</u>:

Kundinformation från huvudwebbplatsen *webbplatsen* returneras eftersom token från huvudwebbplatsen *webbplatsen* används i [!DNL GraphQL]-frågan.

<u>Faktiska resultat</u>:

Kundinformation från den andra webbplatsen returneras.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning &#x200B;](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
