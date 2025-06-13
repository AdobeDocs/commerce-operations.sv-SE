---
title: 'ACSD-52831: Det går inte att placera överlåtbara offertorder när [!DNL Google reCAPTCHA v3 Invisible] är aktiverat'
description: Använd patchen ACSD-52831 för att åtgärda Adobe Commerce-problemet där du inte kan göra överlåtbara offertbeställningar när  [!DNL Google reCAPTCHA v3 Invisible] är aktiverat.
feature: Quotes, B2B, Checkout
role: Admin
exl-id: fa09e41f-f6c3-4cc7-a814-0e1ac5e9ea2e
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 0%

---

# ACSD-52831: Det går inte att placera överlåtbara offertorder när [!DNL Google reCAPTCHA v3 Invisible] är aktiverat

Korrigeringen ACSD-52831 åtgärdar ett problem där du inte kan göra överlåtbara offertorder när [!DNL Google reCAPTCHA v3 Invisible] är aktiverat. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.35 har installerats. Korrigerings-ID är ACSD-52831. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Det går inte att placera överlåtbara offertorder när [!DNL Google reCAPTCHA v3 Invisible] är aktiverat.

<u>Steg som ska återskapas</u>:

1. Aktivera funktionen för B2B-offerter.
1. Aktivera [!DNL Google reCAPTCHA v3 Invisible] på butiken för att aktivera utcheckning/placering av order.
1. Räck upp en offert och fortsätt till kassan med den offerten.
1. Du kommer inte att kunna göra en beställning på grund av CAPTCHA-felet.

<u>Förväntade resultat</u>:

Offerten går vidare till kassan.

<u>Faktiska resultat</u>:

Felet *reCAPTCHA-validering misslyckades. Försök igen*.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
