---
title: 'ACSD-66093: Fälten för gästkundens namn tillåter e-postinmatning som orsakar ogiltiga e-postorder'
description: Använd patchen ACSD-66093 för att åtgärda Adobe Commerce-problemet där det går att ange e-postadresser i fälten för gästkunden **[!UICONTROL First Name]** och **[!UICONTROL Last Name]** och skicka ogiltiga orderbekräftelsemeddelanden.
feature: Checkout
role: Admin, Developer
type: Troubleshooting
exl-id: 30790492-330e-4810-8069-fce87b40ebb2
source-git-commit: b1912bbc5aabd36067563326ee5c6bb84e14441d
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# ACSD-66093: Fälten för gästkundens namn tillåter e-postinmatning som orsakar ogiltiga e-postorder

Korrigeringen ACSD-66093 åtgärdar ett problem där e-postadresser kan anges i gästkundens **[!UICONTROL First Name]**- och **[!UICONTROL Last Name]**-fält, vilket resulterar i ogiltiga e-postmeddelanden med orderbekräftelse. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.65 har installerats. Korrigerings-ID är ACSD-66093. Observera att problemet har åtgärdats i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p11

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.7-p5

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

E-postadresser kunde anges i gästkundens fält **[!UICONTROL First Name]** och **[!UICONTROL Last Name]**, vilket resulterade i ogiltiga e-postmeddelanden med orderbekräftelse.

<u>Steg som ska återskapas</u>:

1. Lägg produkter i kundvagnen som gästkund.
2. Gå till kassan.
3. Fyll i e-postadressen med&quot;test1@gmail.co&quot;.
4. Fyll **[!UICONTROL First Name]** med <test2@gmail.co>.
5. Fyll **[!UICONTROL Last Name]** med <test3@gmail.co>.
6. Fyll i andra obligatoriska fält.
7. Montera order.

<u>Förväntade resultat</u>:

Valideringsmeddelanden ska visas som anger att fälten **[!UICONTROL First Name]** och **[!UICONTROL Last Name]** inte är giltiga, som *Förnamn är inte giltigt! och efternamnet är inte giltigt!* och ordningen ska inte placeras.

<u>Faktiska resultat</u>:

Beställning placeras.
**[!UICONTROL First Name]** och **[!UICONTROL Last Name]** fält sparas som de anges.
Beställningsbekräftelsemeddelandet skickas till alla tre e-postmeddelandena: test1@gmail.co, test2@gmail.co och test3@gmail.co.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
