---
title: Hämta dina autentiseringsnycklar
description: Följ de här stegen för att hämta inloggningsuppgifter för att komma åt Adobe Commerce Composer-paket på repo.magento.com.
exl-id: 7ec2a410-d81f-476a-bf6a-f3c61982a734
source-git-commit: fc63ca58cd2ff7c5ec597751980a39bfbe68aa5f
workflow-type: tm+mt
source-wordcount: '470'
ht-degree: 0%

---

# Hämta dina autentiseringsnycklar

`repo.magento.com`-databasen är den plats där Adobe Commerce-paket och Composer-paket från tredje part lagras och kräver autentisering. Använd ditt Commerce Marketplace-konto för att skapa ett par *autentiseringsnycklar* med 32 tecken för att få åtkomst till databasen.

För åtkomsträttigheter till Adobe Commerce-paket måste du använda nycklar som är kopplade till ett MAGEID som har beviljats åtkomst till dessa paket. MAGEID är vanligtvis den primära kontakten på Adobe Commerce-kontot och är kanske inte alltid projektägare till Adobe Commerce i molninfrastrukturprojekt.

>[!TIP]
>
>Om du stöter på [fel](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/deployment/magento-commerce-cloud-repo-could-not-be-accessed-403-forbidden-or-404-not-found-error-when-deploying.html?lang=sv-SE) kanske du inte har åtkomstbehörighet till paketet, eller så har åtkomstbehörigheten gått ut på grund av en utestående faktura på ditt konto.
>
>* Om du är primär kontaktperson för kontot kontrollerar du att det inte finns någon utestående faktura på kontot.
>* Om nycklarna som tillhandahålls av den primära kontakten inte fungerar och det inte finns några utestående fakturor på kontot kontaktar den primära kontakten [Adobe Commerce support](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=sv-SE#submit-ticket) för att få hjälp.

Skapa autentiseringsnycklar:

1. Logga in på [Commerce Marketplace](https://commercemarketplace.adobe.com/). Om du inte har något konto klickar du på **Registrera**.

1. Klicka på ditt kontonamn längst upp till höger på sidan och välj **Min profil**.

1. Klicka på **Åtkomstnycklar** på fliken Marketplace.

   ![Hämta dina säkra nycklar på Commerce Marketplace](../../assets/installation/cloud_access-key.png)

1. Klicka på **Skapa en ny åtkomstnyckel**. Ange ett specifikt namn för nycklarna (till exempel namnet på utvecklaren som tar emot nycklarna) och klicka på **OK**.

1. Nya offentliga och privata nycklar är nu kopplade till ditt konto som du kan klicka på för att kopiera. Spara informationen eller håll sidan öppen när du arbetar med projektet. Använd den **publika nyckeln** som användarnamn och den **privata nyckeln** som lösenord.

## Hantera dina autentiseringsnycklar

Du kan även inaktivera eller ta bort autentiseringsnycklar. Du kan till exempel inaktivera eller ta bort nycklar av säkerhetsskäl efter att någon har lämnat organisationen.

* Så här inaktiverar du nycklar: Klicka på **Inaktivera**. Du kan göra detta om du vill göra uppehåll i användningen av dina nycklar.
* Så här aktiverar du en tidigare inaktiverad nyckel: Klicka på **Aktivera**.
* Så här tar du bort nycklar: Klicka på **Ta bort**.

### Hantera SSH-åtkomsttoken

Om du vill hämta Adobe Commerce-versioner med SSH måste du generera en åtkomsttoken för nedladdning. Så här skapar du en token:

1. Logga in på ditt [magento.com ](https://account.magento.com/customer/account/login).
1. Klicka på **Mitt konto** överst på sidan.
1. Klicka på **Kontoinställningar** > **Hämtar åtkomsttoken**.

   ![Använd dina nycklar](../../assets/installation/connect_keys1.png)

1. Klicka på **Generera ny token** om du vill ersätta och inaktivera en befintlig token.

Du måste använda ditt MAGEID plus din token för att hämta en release. Ditt MAGEID visas längst upp till vänster på din kontosida.

Exempel:

```bash
curl -k https://MAGEID:TOKEN@www.magentocommerce.com/products/downloads/info/help
```

Använd dina autentiseringsnycklar för att:

* [Hämta metapaketet (integratörer, paketerare)](../composer.md)
* [Klona GitHub-databasen](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/) (endast bidragande utvecklare)
* [Uppgradera och hantera moduler](../../upgrade/modules/upgrade.md)
