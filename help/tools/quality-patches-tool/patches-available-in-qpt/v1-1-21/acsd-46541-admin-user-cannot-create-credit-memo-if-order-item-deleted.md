---
title: 'ACSD-46541: En administratörsanvändare kan inte skapa en kreditnota om ett orderobjekt tas bort'
description: Använd korrigeringsfilen ACSD-46541 för att åtgärda Adobe Commerce-problemet där du inte kan skapa en kreditnota i Adobe Commerce Admin när en produkt har tagits bort.
feature: Admin Workspace, Orders, Returns
role: Admin
exl-id: c46ee888-92b1-4798-bd2b-1a082fd1406a
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---

# ACSD-46541: En administratörsanvändare kan inte skapa en kreditnota om ett orderobjekt tas bort

Korrigeringen ACSD-46541 åtgärdar ett problem där en administratörsanvändare inte kan skapa en kreditnota om ett orderobjekt tas bort. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.21 har installerats. Korrigerings-ID är ACSD-46541. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.0 - 2.4.3-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

När en produkt har tagits bort kan du inte skapa en kreditnota i Commerce Admin.

<u>Steg som ska återskapas</u>:

1. Logga in på Commerce Admin.
1. Skapa en order.
1. Fakturera ordern.
1. Ta bort produkten från beställningen.
1. Klicka på länken **[!UICONTROL Credit Memo]** på sidan för orderredigering.
1. Klicka på **[!UICONTROL Refund Offline]** för att skapa en kreditnota.

<u>Förväntade resultat</u>:

En kreditnota har skapats.

<u>Faktiska resultat</u>:

_Följande produkter med begärda SKU:er hittades inte: SKU001_ -fel visas.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
