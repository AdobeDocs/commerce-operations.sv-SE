---
title: 'ACSD-63244: Åtgärda problem med administratörspanelen i JavaScript, inklusive  [!DNL Google Maps] återgivning och konsolfel'
description: ACSD-63244-korrigeringen åtgärdar flera JavaScript-problem på administratörspanelen, inklusive problem med  [!DNL Google Maps] återgivning och återkommande Uncaught TypeError this._each är inte en funktion" i webbläsarkonsolen.
feature: Admin Workspace
role: Admin, Developer
exl-id: 1985c845-219e-4af4-8f70-62dd57722494
source-git-commit: 6b623811440238deee7a7fe859d887830f89782c
workflow-type: tm+mt
source-wordcount: '323'
ht-degree: 0%

---

# ACSD-63244: Åtgärda problem med administratörspanelen i JavaScript, inklusive [!DNL Google Maps] återgivning och konsolfel

Korrigeringen ACSD-63244 åtgärdar flera JavaScript-problem på administratörspanelen, bland annat problem med [!DNL Google Maps]-återgivning och återkommande `Uncaught TypeError: this._each is not a function`-fel i webbläsarkonsolen. Den här korrigeringen är tillgänglig med [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56. Korrigerings-ID är ACSD-63244. Observera att problemet var planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

Adobe Commerce (alla distributionsmetoder) 2.4.4, 2.4.4-p9, 2.4.6-p7, 2.4.7

**Kompatibel med Adobe Commerce-versioner:**

Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

* Felet `Uncaught TypeError: this._each is not a function` visas i webbläsarkonsolen och stör administratörens gränssnittsfunktioner.
* JavaScript-fel förhindrar att [!DNL Google Maps] återges korrekt.

<u>Steg som ska återskapas</u>:

1. Läs in användargränssnittet för Adobe Commerce Admin.
1. Öppna webbläsarkonsolen och kör följande skript:

   ```
   Object.values([] || {}).forEach((function(e) {  
   e("dd")  
   }));  
   ```

<u>Förväntade resultat</u>:

De JavaScript-funktioner som är tillgängliga i standardbiblioteket för JS körs korrekt utan fel.

<u>Faktiska resultat</u>:

JavaScript-fel visas i webbläsarkonsolen:

```
Uncaught TypeError: this._each is not a function
```

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
