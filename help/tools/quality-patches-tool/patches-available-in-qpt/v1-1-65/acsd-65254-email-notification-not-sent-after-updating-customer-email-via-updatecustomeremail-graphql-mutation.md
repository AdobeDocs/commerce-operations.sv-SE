---
title: 'ACSD-65254: E-postmeddelande skickas inte efter uppdatering av kundens e-post via updateCustomerEmail [!DNL GraphQL] mutation'
description: Använd korrigeringsfilen ACSD-65254 för att åtgärda Adobe Commerce-problemet där e-postmeddelanden inte skickades till kunder efter att deras e-postadresser uppdaterats med valideringen updateCustomerEmail [!DNL GraphQL] .
feature: GraphQL, User Account
role: Admin, Developer
type: Troubleshooting
exl-id: a97daceb-98f6-4bb8-9847-692af700c0fd
source-git-commit: 7e9598e3ac0558706ef98ca81c19d27c37f7e860
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---

# ACSD-65254: E-postmeddelande skickas inte efter uppdatering av kundens e-post via `updateCustomerEmail` [!DNL GraphQL]-mutation

Korrigeringen ACSD-65254 åtgärdar ett problem där e-postmeddelanden inte skickades till kunder efter att deras e-postadresser uppdaterats på deras konton med hjälp av mutationen `updateCustomerEmail` [!DNL GraphQL]. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.65 har installerats. Korrigerings-ID är ACSD-65254. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.9.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.7-p5

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

E-postmeddelanden skickades inte till kunder efter att deras e-postadresser uppdaterats med mutationen `updateCustomerEmail` [!DNL GraphQL].

<u>Steg som ska återskapas</u>:

1. Skapa användare med hjälp av mutationen nedan:

   ```
   mutation {
   	    createCustomer(
   		    input: {
   			    firstname: "Test"
   			    lastname: "User"
   			    email: "test@test.com"
   			    password: "Admin@123"
   			    is_subscribed: true
   		    }
   	    ) {
   		    customer {
   			    created_at
   		    }
   	    }
   }
   ```

1. Generera en token för den tidigare skapade användaren och använd den som en innehavartoken:

   ```
   mutation {
   generateCustomerToken(email: "test@test.com", password: "Admin@123") {
   	    token
   }
   }
   ```

1. Försök att uppdatera e-postadressen för den tidigare skapade användaren med den senast skapade innehavartoken:

   ```
   mutation {
   	    updateCustomerEmail(email: "test+updated@test.com", password: "Admin@123") {
   		    customer {
   			    email
   		    }
   	    }
   }
   ```

<u>Förväntade resultat</u>:

Kunder bör få e-postmeddelanden när de har uppdaterat e-postadresserna på sina konton.

<u>Faktiska resultat</u>:

Endast ett prenumerationsmeddelande skickas till den nya adressen. Bekräftelsemeddelandet för e-postadressändringen skickas inte.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
