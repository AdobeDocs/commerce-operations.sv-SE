---
title: '''ACSD-51666: Fel: "Sessionen har upphört, logga in igen." efter att du loggat in'
description: Använd ACSD-51666-korrigeringen för att åtgärda Adobe Commerce-problemet där felet *Sessionen har upphört, logga in igen.* inträffar när du försöker logga in.
feature: Customers
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '455'
ht-degree: 0%

---

# ACSD-51666: Fel *Sessionen har upphört. Logga in igen.* efter att du har loggat in

ACSD-51666-korrigeringen åtgärdar ett problem där felet *Sessionen har upphört. Logga in igen.* inträffar när du försöker logga in. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.36 är installerad. Korrigerings-ID är ACSD-51666. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Felet *Sessionen har upphört. Logga in igen.* vid försök att logga in med det nya lösenordet från en enhet efter att lösenordet återställts på en annan enhet. Det händer bara om det finns ytterligare en Ajax-begäran på sidan som har lagts till av en anpassad modul.

<u>Steg som ska återskapas</u>:

1. Installera en anpassad modul som lägger till en Ajax-begäran på varje sida i butiken.
1. Skapa ett nytt konto.
1. Logga ut och gå tillbaka till inloggningssidan.
1. Öppna länken *Har du glömt lösenordet* i en annan webbläsare och skicka e-postmeddelandet *Återställ lösenord*.
1. Öppna e-postadressen för att återställa lösenordet i den första webbläsaren och ange det nya lösenordet.
1. Försök logga in i den andra webbläsaren.

<u>Förväntade resultat</u>:

Du kan logga in korrekt vid första försöket.

<u>Faktiska resultat</u>:

* *Mötet har gått ut. Logga in igen.*-fel.
* Du är inte inloggad och omdirigerad till hemsidan.
* Ditt andra inloggningsförsök har slutförts.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
