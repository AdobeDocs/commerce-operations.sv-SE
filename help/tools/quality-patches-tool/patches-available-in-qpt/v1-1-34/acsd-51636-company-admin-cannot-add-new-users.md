---
title: "ACSD-51636: Företagsadministratören kan inte lägga till nya användare från kundkontoavsnittet"
description: Använd korrigeringsfilen ACSD-51636 för att åtgärda Adobe Commerce-problemet där företagsadministratören inte kan lägga till nya användare från kundkontoavsnittet trots att de har alla nödvändiga roller och behörigheter.
feature: Admin Workspace, B2B, Companies, Customer Service
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 0%

---

# ACSD-51636: Företagsadministratören kan inte lägga till nya användare från kundkontoavsnittet

Korrigeringen ACSD-51636 åtgärdar ett problem där företagsadministratören inte kan lägga till nya användare från kundkontoavsnittet trots att de har alla nödvändiga roller och behörigheter. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.34 har installerats. Korrigerings-ID är ACSD-51636. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Företagsadministratören kan inte lägga till nya användare från kundkontoavsnittet trots att de har alla nödvändiga roller och behörigheter.

Förutsättningar:

* B2B-modulen är installerad.
* Företagsfunktioner är aktiverade.

<u>Steg som ska återskapas</u>:

1. Skapa ett nytt företag.
1. Gå till **[!UICONTROL Admin]** > **[!UICONTROL Customers]** > **[!UICONTROL All Customers]**.
1. Redigera typen **[!UICONTROL Company Admin]** till *Kund*.
1. Logga in som kund.
1. Gå till **[!UICONTROL My Account]** > **[!UICONTROL Company Users]** > **[!UICONTROL Add User]** och lägg till information för användaren och aktivera den.
1. Spara den nya användaren.

<u>Förväntade resultat</u>

Administratörsanvändaren kan lägga till en ny användare.

<u>Faktiska resultat</u>

* Administratörsanvändaren får ett felmeddelande: *Något gick fel*.
* Administratörsanvändaren kan inte skapa en ny kund.
* Loggen innehåller följande fel:

  ```PHP
      report.CRITICAL: Error: Call to a member function __toArray() on null in app/code/Magento/LoginAsCustomerLogging/Observer/LogSaveCustomerObserver.php:123
  ```

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](</help/tools/quality-patches-tool/usage.md>) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) i [!DNL Quality Patches Tool]-handboken.
