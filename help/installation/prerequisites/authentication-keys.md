---
title: Hämta dina autentiseringsnycklar
description: Följ de här stegen för att hämta inloggningsuppgifter för att komma åt Adobe Commerce- och Magento Open Source Composer-paket på repo.magento.com.
source-git-commit: 8f05fb6fc212c2b3fda80457bbf27ecf16fb1194
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 0%

---


# Hämta dina autentiseringsnycklar

The `repo.magento.com` är den plats där Adobe Commerce-, Magento Open Source- och tredjepartspaket för disposition lagras och kräver autentisering. Använd ditt Commerce Marketplace-konto för att skapa ett par med 32 tecken *autentiseringsnycklar* för att komma åt databasen.

>[!NOTE]
>
>För åtkomsträttigheter till Adobe Commerce- och Magento Open Source-paket måste du använda nycklar som är kopplade till ett MAGEID som har beviljats åtkomst till dessa paket. MAGEID är vanligtvis **Faktureringskontakt** på Adobe Commerce-kontot och kanske inte alltid är **Projektägare** av Adobe Commerce om molninfrastrukturprojekt. Om du stöter på [fel](https://support.magento.com/hc/en-us/articles/360040296392)kanske du inte har åtkomstbehörighet för paketet eller så har åtkomsträttigheterna gått ut på grund av en utestående faktura på kontot. Kontakt [Adobe Commerce Support](https://support.magento.com/hc/en-us) om du behöver hjälp med ditt MAGEID.

Så här skapar du autentiseringsnycklar:

1. Logga in på [Commerce Marketplace](https://marketplace.magento.com). Om du inte har något konto klickar du på **Registrera**.
1. Klicka på ditt kontonamn längst upp till höger på sidan och välj **Min profil**.

1. Klicka **Åtkomsttangenter** på Marketplace-fliken.

   ![Skaffa säkra nycklar på Commerce Marketplace](../../assets/installation/cloud_access-key.png)

1. Klicka **Skapa en ny åtkomstnyckel**. Ange ett specifikt namn för nycklarna (till exempel namnet på utvecklaren som tar emot nycklarna) och klicka på **OK**.

1. Nya offentliga och privata nycklar är nu kopplade till ditt konto som du kan klicka på för att kopiera. Spara informationen eller håll sidan öppen när du arbetar med projektet. Använd **Offentlig nyckel** som ditt användarnamn och **Privat nyckel** som ditt lösenord.

## Hantera dina autentiseringsnycklar

Du kan även inaktivera eller ta bort autentiseringsnycklar. Du kan till exempel inaktivera eller ta bort nycklar av säkerhetsskäl efter att någon har lämnat organisationen.

* Så här inaktiverar du nycklar: Klicka **Inaktivera**. Du kan göra detta om du vill göra uppehåll i användningen av dina nycklar.
* Så här aktiverar du en tidigare inaktiverad nyckel: Klicka **Aktivera**.
* Så här tar du bort nycklar: Klicka **Ta bort**.

### Hantera SSH-åtkomsttoken

Om du vill hämta Adobe Commerce-versioner med SSH måste du generera en åtkomsttoken för nedladdning. Så här skapar du en token:

1. Logga in på [magento.com-konto](https://account.magento.com/customer/account/login).
1. Klicka **Mitt konto** överst på sidan.
1. Klicka **Kontoinställningar** > **Åtkomsttoken hämtas**.

   ![Få åtkomst till dina nycklar](../../assets/installation/connect_keys1.png)

1. Klicka **Generera ny token** för att ersätta och inaktivera en befintlig token.

Du måste använda ditt MAGEID plus din token för att hämta en release. Ditt MAGEID visas längst upp till vänster på din kontosida.

Exempel:

```bash
curl -k https://MAGEID:TOKEN@www.magentocommerce.com/products/downloads/info/help
```

Använd dina autentiseringsnycklar för att:

* [Hämta metapaketet (integratörer, paketerare)](../composer.md)
* [Klona GitHub-databasen](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/) (endast bidragsgivande utvecklare)
* [Uppgradera och hantera moduler](../../upgrade/modules/upgrade.md)