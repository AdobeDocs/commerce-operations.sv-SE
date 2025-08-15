---
title: 'ACSD-48570: Åtgärdar problem med lösenordslänk för administratörsåterställning med lagringskod i URL'
description: Använd korrigeringsfilen ACSD-48570 för att åtgärda Adobe Commerce-problemet där det inte gick att få åtkomst till återställningssidan via länken för lösenord för administratörsåterställning när konfigurationen för [!UICONTROL Add Store Code to URLs] var aktiverad.
feature: Security, User Account
role: Admin, Developer
exl-id: 049a82ff-80e3-46a1-8472-ac74de0e365f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# ACSD-48570: Åtgärdar problem med lösenordslänk för administratörsåterställning med lagringskod i URL

Korrigeringsfilen ACSD-48570 som åtgärdar Adobe Commerce-problemet där sidan för återställning av lösenord inte kunde nås via länken för administratörsåterställning av lösenord när konfigurationen av *[!UICONTROL Add Store Code to URLs]* aktiverades. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58 har installerats. Korrigerings-ID är ACSD-48570. Observera att problemet har åtgärdats i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.6-p8

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

När inställningen **[!UICONTROL Add Store Code to URLs]** är aktiverad fungerar inte administratörsåterställningen för lösenord korrekt.
När en administratör begär en lösenordsåterställning och klickar på återställningslänken i e-postmeddelandet, dirigeras de om till inloggningssidan eller får ett 404-fel i stället för att tas till formuläret för att återställa lösenordet. Detta förhindrar administratörer från att återställa sina konton utan manuell åtgärd.

<u>Steg som ska återskapas</u>:

1. Aktivera **[!UICONTROL Add Store Code to URLs]**-konfigurationen på **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Web]** > **[!UICONTROL URL Options]**.
1. Logga ut från panelen Admin och klicka på länken **[!UICONTROL Forgot your password?]** på inloggningssidan för Admin.
1. Ange administratörsanvändarens e-postadress, skicka captcha och klicka på **[!UICONTROL Retrieve Password]**.
1. Öppna e-postmeddelandet för återställning av lösenord och klicka på länken för återställning av lösenord.

<u>Förväntade resultat</u>:

Formuläret för att återställa lösenordet ska visas.

<u>Faktiska resultat</u>:

Inloggningssidan eller en 404-felsida visas i stället för formuläret för att återställa lösenordet.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
