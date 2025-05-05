---
title: 'ACSD-61895: [!DNL GraphQL] kategorifrågan misslyckades för privat delad katalog med begränsad vy'
description: Använd ACSD-61895-korrigeringen för att åtgärda Adobe Commerce-problemet där  [!DNL GraphQL] svar för gästkunder (med en offentlig delad katalog med alla tillåtna kategorier) inte returnerade några kategorier när en privat delad katalog med begränsningar skapades för samma kategorier.
feature: Categories, GraphQL, Roles/Permissions
role: Admin, Developer
source-git-commit: f929f76dbe79c3764e2c157576b4f6db867673cf
workflow-type: tm+mt
source-wordcount: '544'
ht-degree: 0%

---


# ACSD-61895: [!DNL GraphQL] `categories`-frågan misslyckas för privat delad katalog med begränsad vy

Korrigeringen ACSD-61895 åtgärdar ett problem där [!DNL GraphQL] svar för gästkunder (med en offentlig delad katalog med alla tillåtna kategorier) inte returnerade några kategorier när en privat delad katalog med begränsningar skapades för samma kategorier.

Efter korrigeringen returneras alla kategorier med tillåtna behörigheter (offentlig delad katalog) för gästanvändare, även om rotkategorin inte tillåter behörighet i omfattningen för en privat delad katalog.

Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57 är installerad. Korrigerings-ID är ACSD-61895. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

[!DNL GraphQL] svar för gästkunder (med en offentlig delad katalog med alla tillåtna kategorier) returnerar inga kategorier när en privat delad katalog med begränsningar skapas för samma kategorier.

<u>Steg som ska återskapas</u>:

1. Installera Adobe Commerce med B2B och exempeldata.
1. Kontrollera att B2B-funktionerna är aktiverade.
1. Skapa två delade kataloger: en offentlig och en privat.

   * Offentlig delad katalog:

      * Tilldela alla kategorier till den offentliga katalogen.

   * Privat delad katalog:

      * Tilldela bara kategorin `Gear` och dess underordnade kategorier till den privata katalogen.
      * Tilldela den privata katalogen till ett testföretag.

1. Skapa en företagsanvändare:

   * Skapa en användare som är associerad med testföretaget som är länkat till den privata delade katalogen.
   * Kontrollera att användaren bara kan komma åt kategorin `Gear` och dess underordnade kategorier på klientsidan när han/hon är inloggad.

1. Frågekategorier via API:

   * Använd API-klienten för att köra följande [!DNL GraphQL]-fråga utan en kundtoken:

   ```graphql
   query Categories { 
       categories { 
           items { 
               children_count 
               children { 
                   uid 
                   name 
                   children_count 
                   children { 
                   uid 
                   name 
                   } 
               } 
           } 
       } 
   }
   ```

1. Observera svaret och verifiera om kategorin `Gear` och andra kategorier returneras.
1. Frågekategorier med kundtoken:

   * Logga in som testföretagsanvändare.
   * Kör samma [!DNL GraphQL]-kategorifråga, men inkludera kundtoken för den inloggade användaren.
   * Observera svaret och kontrollera om bara kategorin `Gear` och dess underordnade kategorier returneras.


<u>Förväntade resultat</u>:

När du frågar som gästföretagsanvändare ska alla kategorier returneras (som förväntat).

<u>Faktiska resultat</u>:

Svaret från frågan `categories` visar inga kategorier.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.


## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.

