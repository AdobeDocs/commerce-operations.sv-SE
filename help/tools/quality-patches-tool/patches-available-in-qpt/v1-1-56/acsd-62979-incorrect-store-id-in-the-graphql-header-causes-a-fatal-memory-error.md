---
title: 'ACSD-62979: Felaktigt arkiv-ID i GraphQL-huvudet orsakar ett allvarligt minnesfel'
description: Använd korrigeringsfilen ACSD-62979 för att åtgärda Adobe Commerce-problemet där fel lagrings-ID i GraphQL-huvudet orsakar ett allvarligt minnesfel
feature: GraphQL
role: Admin, Developer
source-git-commit: 16875f95ab23559d4e1081b8cfe0374e1394d87d
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 0%

---


# ACSD-62979: Felaktigt arkiv-ID i GraphQL-huvudet orsakar ett allvarligt minnesfel

Korrigeringen ACSD-62979 åtgärdar ett problem där fel lagrings-ID i GraphQL-huvudet orsakar ett allvarligt minnesfel. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56 har installerats. Korrigerings-ID är ACSD-62979. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p7, 2.4.6

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.6-p8

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Korrigerar problemet där felaktigt arkiv-ID i GraphQL-huvudet orsakar ett allvarligt minnesfel.

<u>Steg som ska återskapas</u>:

1. Navigera till **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Web]** > **[!UICONTROL Url Options]**). Aktivera **[!UICONTROL Add Store Code to Urls]**.
1. Kör nedan GraphQL-fråga med fel värde för butikshuvudet.

```graphql
{
  categoryList(filters: { ids: { eq: "2" } }) {
    uid
    level
    name
    url_path
    image
    children {
      uid
      level
      name
      url_path
      image
      children {
        uid
        level
        name
        url_path
        image
        children {
          uid
          level
          name
          url_path
          image
        }
      }
    }
  }
}
```

<u>Förväntade resultat</u>:

Felmeddelande:&quot;Det gick inte att hitta det begärda arkivet. Verifiera butiken och försök igen&quot;

<u>Faktiska resultat</u>:

Allvarligt fel som:

```Allowed memory size of 792723456 bytes exhausted```

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.

