---
title: "ACSD-54060: Begränsad administratör kan inte spara produkten om den är underordnad en annan produkt"
description: Använd patchen ACSD-54060 för att åtgärda Adobe Commerce-problemet där en begränsad administratör inte kan spara en produkt om den är underordnad en annan produkt som tilldelats ett annat omfång.
feature: Admin Workspace, Roles/Permissions, Products
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 0%

---

# ACSD-54060: Begränsad administratör kan inte spara produkten om den är underordnad en annan produkt

Korrigeringen ACSD-54060 åtgärdar ett problem där en begränsad administratör inte kan spara en produkt om den är underordnad en annan produkt som tilldelats ett annat omfång. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.42 är installerad. Korrigerings-ID är ACSD-54060. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3 - 2.4.6-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

En begränsad administratör kan inte spara en produkt om den är underordnad en annan produkt som har tilldelats ett annat omfång.

<u>Steg som ska återskapas</u>:

1. Skapa ytterligare en webbplats.
1. Skapa en enkel produkt och tilldela den till båda webbplatserna.
1. Skapa en konfigurerbar produkt med den enkla produkten som enda variant och tilldela endast den konfigurerbara produkten till standardwebbplatsen.
1. Skapa en begränsad administratörsanvändare med endast åtkomst till den andra webbplatsen.
1. Logga in som begränsad administratörsanvändare.
1. Försök att ändra det enkla produktnamnet i det andra webbplatsomfånget.

<u>Förväntade resultat</u>:

Den begränsade administratören kan ändra produktnamnet.

<u>Faktiska resultat</u>:

Ett fel inträffar: *Fler behörigheter krävs för att visa det här objektet*.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
