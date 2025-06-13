---
title: 'ACSD-47027: långsam fråga B2B [!UICONTROL CompanyRole] [!DNL GraphQL] uppdatering'
description: Använd korrigeringsfilen ACSD-47027 för att åtgärda Adobe Commerce-problemet där det finns en långsam uppdatering av B2B [!UICONTROL CompanyRole] [!DNL GraphQL] -frågan.
feature: B2B, Companies, GraphQL, Roles/Permissions
role: Admin
exl-id: 91eb0297-1ba8-47b7-9581-29bee835843c
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# ACSD-47027: långsam fråga B2B [!UICONTROL CompanyRole] [!DNL GraphQL] uppdatering

Korrigeringen ACSD-47027 löser problemet där den långsamma uppdateringen av fråga B2B [!UICONTROL CompanyRole] [!DNL GraphQL] inte fungerar som förväntat. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.23 har installerats. Korrigerings-ID är ACSD-47027. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**
* Adobe Commerce (alla distributionsmetoder) 2.4.2-p1

**Kompatibel med Adobe Commerce-versioner:**
* Adobe Commerce (alla distributionsmetoder) 2.4.2 - 2.4.5-p1

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Den långsamma uppdateringen av fråga B2B [!UICONTROL CompanyRole] [!DNL GraphQL] fungerar inte som förväntat.

<u>Förutsättningar</u>:

Installera B2B-modulen.

<u>Steg som ska återskapas</u>:

1. Gå till **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configurations]** > **[!UICONTROL B2B Features]** i Adobe Commerce Admin och ange **[!UICONTROL Enable Company]** som _Ja_.
1. Gå till fronten och skapa ett företag.
1. När du har loggat in som företagsanvändare går du till **[!UICONTROL My Account]** > **[!UICONTROL Roles and Permissions]** och lägger till en ny roll.
1. Aktivera [!UICONTROL dev]-frågelogg med `bin/magento dev:que:enab`.
1. Skicka nu begäran [!DNL GraphQL] nedan (id är det [!UICONTROL base64]-kodade roll-ID:t):

   <pre><code>
   mutation {
   updateCompanyRole(
      input: {
         id: "Mg=="
         permissions: [
         "Magento_Company::view"
         "Magento_Company::view_account"
         "Magento_Company::user_management"
         "Magento_Company::roles_view"
        ]
      }
    ) {
      role {
         id

         name

         permissions {
         id

         text

         children {
            id

            text

            children {
               id

               text
             }
           }
         }
       }
     }
   }
   </code></pre>

1. Kontrollera frågeloggen.
1. Du ser att frågan ovan körs. Frågan körs i `app/code/Magento/CompanyGraphQl/Model/Company/Role/ValidateRole.php::validateResources`.

<u>Förväntade resultat</u>:

`app/code/Magento/CompanyGraphQl/Model/Company/Role/ValidateRole.php::validateResources` måste optimeras för att undvika inläsning av alla data som är tillgängliga i databastabellen **[!UICONTROL company_permissions]**.

<u>Faktiska resultat</u>:

Adobe Commerce kör en fråga utan något filter. När det finns ett stort antal poster tar det lång tid för Adobe Commerce att förbereda datainsamlingen.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur. 

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
