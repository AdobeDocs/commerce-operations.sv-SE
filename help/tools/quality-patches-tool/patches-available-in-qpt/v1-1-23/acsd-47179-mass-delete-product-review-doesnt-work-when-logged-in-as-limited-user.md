---
title: "ACSD-47179: massborttagning av produktgranskningar fungerar inte när användaren är inloggad med en begränsad användarroll"
description: Använd patchen ACSD-47179 för att åtgärda Adobe Commerce-problemet där massborttagning av produktrecensioner inte fungerar när användaren är inloggad som en begränsad användarroll.
feature: Marketing Tools, Products, Roles/Permissions
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# ACSD-47179: massborttagning av produktgranskningar fungerar inte när användaren är inloggad som en begränsad användarroll

Korrigeringen ACSD-47179 åtgärdar ett problem där massborttagning av produktgranskningar inte fungerar när användaren är inloggad som en begränsad användarroll. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.23 har installerats. Korrigerings-ID är ACSD-47179. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Massborttagning av produktgranskningar fungerar inte när du är inloggad som en begränsad användarroll.

<u>Steg som ska återskapas</u>:

1. Skapa en sekundär webbplats.
1. Skapa en användarroll som är begränsad till den sekundära webbplatsen med fullständig behörighet till följande avsnitt:
   * Katalog
   * Kund
   * Marknadsföring
1. Skapa en produkt och tilldela den till den sekundära webbplatsen.
1. Lägg till två recensioner till produkten från förgrunden.
1. Logga in på [!DNL Commerce]-administratören med den begränsade administratörsanvändaren som just skapats.
1. Försök att massta bort väntande granskningar.

<u>Förväntade resultat</u>:

En administratör med tillräcklig behörighet kan massta bort väntande granskningar.

<u>Faktiska resultat</u>:

Du får följande fel: _Något gick fel. Undantag genererades i support_report.log_

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.