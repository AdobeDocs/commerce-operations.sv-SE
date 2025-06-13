---
title: 'ACSD-48164: Begränsad administratör kan inte spara webbplatsnivåvärde'
description: Använd korrigeringsfilen ACSD-48164 för att åtgärda Adobe Commerce-problemet där en begränsad administratör inte kan spara ett webbplatsnivåvärde.
feature: Admin Workspace
role: Admin
exl-id: 1ad4758e-7ecc-48d0-8313-1163188cbe73
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# ACSD-48164: Begränsad administratör kan inte spara webbplatsnivåvärde

Korrigeringen ACSD-48164 åtgärdar ett problem där en begränsad administratör inte kan spara ett värde på webbplatsnivå. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.27 är installerad. Korrigerings-ID är ACSD-48164. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.7 - 2.4.6

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Begränsad administratör kan inte spara ett värde på webbplatsnivå.

<u>Steg som ska återskapas</u>:

1. Skapa en ny webbplats-, butiks- och butiksvy i [!UICONTROL Admin] > **[!UICONTROL Store]** > **[!UICONTROL All Stores]**.
1. Skapa en ny administratörsroll i [!UICONTROL Admin] > **[!UICONTROL System]** > **[!UICONTROL User Roles]**.

   * Gå till **[!UICONTROL Role Resources]** > **[!UICONTROL Role Scopes]**, markera den nya webbplatsen och tilldela den här rollen till valfri administratörsanvändare.

1. Välj valfri produkt och tilldela bara den nya webbplatsen. Välj inte standardwebbplatsen.
1. Logga in som admin-användare tilldelad i steg två och redigera produkten under **[!UICONTROL All Store View]** genom att ändra alla webbplatsnivåattribut som *[!UICONTROL Status]*, *[!UICONTROL Tax Class]* och ange produkten som ny.
1. Spara produkten.

<u>Förväntade resultat</u>:

Administratörsanvändare som är associerad med rollomfånget för en webbplats kan spara produktattribut på webbplatsnivå med omfånget *[!UICONTROL All Store View]*.

<u>Faktiska resultat</u>:

Meddelandet om att produkten sparades visas, men produktattributvärdena ändras inte.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
