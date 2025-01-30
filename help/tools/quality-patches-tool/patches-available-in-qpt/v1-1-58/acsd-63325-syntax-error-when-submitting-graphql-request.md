---
title: 'ACSD-63325: Syntaxfel: Oväntat <EOF>-fel när en tom [!DNL GraphQL] begäran skickades'
description: Använd korrigeringen ACSD-63325 för att åtgärda Adobe Commerce-problemet där ett syntaxfel inträffar när en tom [!DNL GraphQL] begäran skickas.
feature: GraphQL
Role: Admin, Developer
source-git-commit: 805ab7fb001cda112ce1298f0221fb22b6494b47
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---


# ACSD-63325: Syntaxfel: Oväntat &lt; EOF >-fel när tom [!DNL GraphQL]-begäran skickades

Korrigeringen ACSD-63325 åtgärdar ett fel där ett syntaxfel: Oväntat &lt; EOF > och en svarskod som inte är 200 returnerades när en tom [!DNL GraphQL]-begäran skickades. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58 har installerats. Korrigerings-ID är ACSD-63325. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7-p3

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

När en tom [!DNL GraphQL]-begäran skickas uppstår ett HTTP-serverfel i stället för en 200-svarskod.

<u>Steg som ska återskapas</u>:

1. Skicka en tom GraphQL-begäran

   ```graphql
   curl -i -X OPTIONS http://commerce.local/graphql
   ```

<u>Förväntade resultat</u>:

Svarskoden är 200 för begäran.

```
curl -i -X OPTIONS http://commerce.local/graphql
```

<u>Faktiska resultat</u>:

Ett 500 internt serverfel inträffar enligt följande:

```
HTTP/1.1 500 Internal Server Error
```

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) i Commerce i guiden för molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
