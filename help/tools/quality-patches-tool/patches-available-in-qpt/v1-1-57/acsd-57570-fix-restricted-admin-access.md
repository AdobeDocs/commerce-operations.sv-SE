---
title: 'ACSD-57570: Korrigera begränsad administratörsanvändaråtkomst till delade kataloger'
description: Använd patchen ACSD-57570 för att åtgärda Adobe Commerce-problemet där en begränsad administratörsanvändare med åtkomst till en viss butik inte konsekvent kan visa alla delade kataloger som tilldelats produkter eller spara kundinformation, vilket leder till inkonsekvenser i systemet.
feature: B2B, Companies, Roles/Permissions
role: Admin, Developer
source-git-commit: 6147a028e2ce783809b5c2c32c65784611d03f0e
workflow-type: tm+mt
source-wordcount: '538'
ht-degree: 0%

---


# ACSD-57570: Korrigera begränsad administratörsanvändaråtkomst till delade kataloger

Korrigeringen ACSD-57570 åtgärdar ett problem där en begränsad administratörsanvändare med åtkomst till en viss butik inte konsekvent kan visa alla delade kataloger som tilldelats produkter eller spara kundinformation, vilket leder till inkonsekvenser i systemet. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57 är installerad. Patch-ID:t är ACSD-57570. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.5.0.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4-p3

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3 - 2.4.4-p9

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

En begränsad administratörsanvändare med åtkomst till en viss butik kan inte alltid se alla delade kataloger eller spara kunder, vilket leder till inkonsekvenser. I flera arkiv kan administratören inte se nya företag eller anpassade delade kataloger.

<u>Steg som ska återskapas</u>:

1. Ställ in butiker i följande ordning:
   * Skapa en ny webbplats med namnet W2.
   * Skapa en ny butiksvy för standardwebbplatsen.
   * Skapa en ny butik med namnet W2S2 för webbplatsen W2.
   * Skapa en ny butiksvy med namnet W2S2SV1 för butiken W2S2.
   * Skapa en ny butiksvy med namnet W2S2SV2 för butiken W2S2.
   * Skapa ett företag för W2.
1. Tilldela produkter:
   * Tilldela endast W1 vissa produkter.
   * Tilldela endast W2 vissa produkter.
   * Tilldela vissa produkter till både W1 och W2.
1. Skapa en anpassad delad katalog och tilldela alla produkter till den.
1. Skapa en anpassad administratörsroll med åtkomst till endast **W2S2**, inte **W2**.
1. Tilldela den begränsade administratörsanvändaren den nya anpassade administratörsrollen.
1. Logga in som begränsad administratörsanvändare.
1. Verifiera åtkomst:
   * Kontrollera vilka företag du kan se.
   * Kontrollera vilka delade kataloger du kan se.
   * Öppna produktlistan och kontrollera om du kan se alla delade kataloger som produkterna är tilldelade till.

<u>Förväntade resultat</u>:

Beteendet bör vara konsekvent.

<u>Faktiska resultat</u>:

Om du bara skapar ytterligare en webbplats-, butik- och butiksvy kan den begränsade administratörsanvändaren se företaget, den delade katalogen och båda delade kataloger i produktlistan. Med ovanstående inställningar kan den begränsade administratören inte se det nya företaget eller den anpassade delade katalogen, och endast standardkatalogen visas i produktlistan.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
