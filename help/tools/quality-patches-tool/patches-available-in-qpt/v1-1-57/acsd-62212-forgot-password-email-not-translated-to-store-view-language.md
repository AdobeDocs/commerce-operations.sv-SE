---
title: 'ACSD-62212: [!UICONTROL Forgot Password]-e-postmeddelande har inte översatts till visningsspråket för arkivet'
description: Använd korrigeringsfilen ACSD-62212 för att åtgärda Adobe Commerce-problemet där innehållet i e-postmeddelandet *[!UICONTROL Forgot Password]* inte översätts till butiksvyns språk.
feature: GraphQL
role: Admin, Developer
exl-id: 29e6f2fa-574f-4ab1-82f5-88e1eb1de83e
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# ACSD-62212: *[!UICONTROL Forgot Password]*-e-postmeddelande har inte översatts till visningsspråket för arkivet

Korrigeringen ACSD-62212 åtgärdar ett problem där innehållet i e-postmeddelandet *[!UICONTROL Forgot Password]* inte översätts till visningsspråket för butiken. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=sv-SE) 1.1.57 är installerad. Korrigerings-ID är ACSD-62212. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7-p2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

När du återställer lösenord via GraphQL i en annan butiksvy än den som är registrerad matchar återställningslösenordslänken inte den butiksvy som lösenordet startades från.

<u>Steg som ska återskapas</u>:

1. Skapa en sekundär butiksvy under *[!UICONTROL Main Website Store]*.
1. Växla *[!UICONTROL Locale]* till *[!UICONTROL French (France)]* i den sekundära lagringsvyns omfång.
1. Installera det franska språkpaketet för översättningar.
1. Skapa ett kundkonto.
1. Använd följande GraphQL-mutation med rubriken *store* med den sekundära lagringsvykoden.

   ```
   mutation {
       requestPasswordResetEmail(
           email: "test@gmail.com"
       )
   }
   ```

1. Kontrollera e-postmeddelandet.

<u>Förväntade resultat</u>:

* Språket för e-postmeddelandets ämne, länk och innehåll överensstämmer med språkinställningen i butiksvyn.
* Begäran om återställning av lösenord skickas från butiken där kundens konto är registrerat, oavsett butikshuvudet i begäran.

<u>Faktiska resultat</u>:

Följande kan observeras i e-postmeddelandet:

* Länken för att återställa lösenordet har lagringskoden &quot;default&quot;.
* Ämnet är på engelska.
* Innehållet är på franska.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
