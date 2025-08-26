---
title: 'ACSD-66311: Företagsrutnät läses in långsamt för användare med begränsade administratörer'
description: Använd korrigeringsfilen ACSD-66311 för att åtgärda problemet med Adobe Commerce där stödrastret laddas långsamt för adminanvändare med begränsad åtkomst till webbplatser.
role: Admin, Developer
feature: B2B
type: Troubleshooting
source-git-commit: 841e660136354800dd9758d8c10e86c966be3a1e
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 2%

---


# ACSD-66311: Företagsrutnät läses in långsamt för användare med begränsade administratörer

Korrigeringen ACSD-66311 åtgärdar ett problem där företagsrutnätet laddas långsamt för administratörer med begränsad webbplatsåtkomst. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69 har installerats. Korrigerings-ID är ACSD-66311. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.9.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7-p4

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7-p4 - 2.4.8-p1

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Företagets rutnät läses in långsamt för administratörer med begränsad webbplatsåtkomst.

<u>Steg som ska återskapas</u>:

1. Installera Adobe Commerce med **[!UICONTROL B2B features]**.
1. Skapa ytterligare två webbplatser (utöver huvudwebbplatsen) med butiker/vyer:
   * Huvudwebbplats (skapas under installationen)
   * Webbplats 2 → Butik 2 → Butik 2
   * Webbplats 3 → Lagra 3 → Lagra vy 3
1. Skapa användarrollen **[!UICONTROL Admins in Scope]**:
   * Scope: endast två butiker: *Huvudwebbplats* + *Webbplats 3/Store*.
   * Resurser: endast *Instrumentpanel* + *Företag*.
1. Skapa en administratörsanvändare med rollen **[!UICONTROL Admins in Scope]**, till exempel **adminscope**.
1. Generera specifika distribuerade kund- och företagsdata:
   1. **Kunder som tilldelats webbplatser**

      | Webbplats-ID | Antal kunder |
      |------------|---------------------|
      | 1 | 600 000 |
      | 2 | 1 500 |
      | 3 | 500 |


   1. Kör följande fråga för att verifiera distributionen:

      ```
           SELECT website_id, COUNT(*) 
           FROM customer_entity 
           GROUP BY website_id; 
      ```

   1. **Kunder som har tilldelats företag**

      | Antal kunder | Antal företag |
      |---------------------|---------------------|
      | 1 | 4 500 |
      | 2 | ~1 000 |
      | ~595 kB | 1 |

   1. Kör följande fråga för att verifiera distributionen:

      ```
            SELECT customer_count, COUNT(*) AS number_of_companies
            FROM (
      
            SELECT company_id, COUNT(customer_id) AS customer_count
            FROM company_advanced_customer_entity
            GROUP BY company_id
) AS-underfråga
GROUP BY customer_count
ORDER BY customer_count;
&quot;

1. Indexera om alla data för att generera poster i **customer_grid_flat**.
1. Logga in som **adminscope**.
1. Gå till **[!UICONTROL Customers]** > **[!UICONTROL Companies]**.

<u>Förväntade resultat</u>:

Sidan läses in under 1 sekund.

<u>Faktiska resultat</u>:

Det tar mer än 14 minuter att läsa in sidan.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
