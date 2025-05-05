---
title: 'ACSD-48773: E-postmall för belöningspoäng som hämtas från fel butik'
description: Använd korrigeringsfilen ACSD-48773 för att åtgärda Adobe Commerce-problemet där e-postmallen för belöningspoäng hämtas från fel butik.
feature: Admin Workspace, Communications, Marketing Tools, Orders, Personalization, Rewards
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 0%

---

# ACSD-48773: E-postmall för belöningspoäng som hämtas från fel butik

Korrigeringen ACSD-48773 åtgärdar ett problem där e-postmallen för belöningspoäng hämtas från fel butik. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.26 har installerats. Korrigerings-ID är ACSD-48773. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4-p2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2 - 2.4.6

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Produktprisomindexeringen fungerar inte om paketprodukten inte har tilldelats någon webbplats.

<u>Steg som ska återskapas</u>:

1. Skapa två webbplatser, två butiker och två butiksvyer.
1. Gå till **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Product Reviews]** och aktivera **[!UICONTROL Reviews]**.
1. Gå till **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Store Email Addresses]**.
Växla till **[!DNL default website scope]** och ange adressen **[!UICONTROL Customer Support Sender Email]** (till exempel: *support_base@example.com*).
Växla till **[!DNL second website scope]** och ange ett annat värde för **[!UICONTROL Customer Support Sender Email]**-adressen (till exempel: *support_second@example.com*).
1. Gå till **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Customer Configuration]** > **[!UICONTROL Account Sharing Options]** > **[!UICONTROL Share Customer Accounts]** och ange **[!UICONTROL Share Customer Accounts]** = *Per webbplats*.
1. Ange följande under **[!UICONTROL Reward Points]**:
   **[!UICONTROL Enable Reward Points Functionality]** = *Ja*
   **[!UICONTROL Enable Reward Points Functionality on Storefront]** = *Ja*
   **[!UICONTROL Actions for Acquiring Reward Points by Customers]** > **[!UICONTROL Review Submission]** och ange **[!UICONTROL Review Submission]** = *150*
   **[!UICONTROL Email Notification Settings]** > **[!UICONTROL Email Sender]** och ange **[!UICONTROL Email Sender]** = *Kundsupport*
1. Gå till **[!UICONTROL Stores]** > **[!UICONTROL Other Settings]** > **[!UICONTROL Reward Exchange Rates]** och ange valutakurserna för den andra webbplatsen för både **[!UICONTROL Points/Currency]** och **[!UICONTROL Currency/Points]**.
1. Skapa ett kundkonto på den andra webbplatsen.
1. Logga in som kund på den andra webbplatsen.
1. Aktivera **[!UICONTROL Subscribe]** för **[!UICONTROL Balance Updates]**.
1. Skicka in en produktrecension.
1. Gå till **[!UICONTROL Marketing]** > **[!UICONTROL User Content]** > **[!UICONTROL Pending Reviews]**.
1. Ändra status för den nya granskningen till ***[!UICONTROL Approved]*** och **[!UICONTROL Save]**.
1. Vänta på att e-postmeddelandet kommer fram.

<u>Förväntade resultat</u>:

E-postmeddelandet om uppdatering av belöningspoäng borde ha skickats av den e-postavsändare som konfigurerats på den andra webbplatsomfånget.

<u>Faktiska resultat</u>:

E-postmeddelandet om uppdatering av belöningspoäng skickades av den e-postavsändare som är konfigurerad på standardwebbplatsens omfång.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
