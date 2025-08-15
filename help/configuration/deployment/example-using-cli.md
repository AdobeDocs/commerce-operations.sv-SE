---
title: Exempel med CLI-kommandon
description: Se ett exempel på hur du ställer in delade, systemspecifika och känsliga värden i utvecklingssystemet med kommandoraden.
exl-id: d0058e9f-a5a9-48a6-9c66-c61515666335
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1023'
ht-degree: 0%

---

# Exempel med CLI-kommandon

I det här exemplet visas hur du ställer in delade, systemspecifika och känsliga värden i utvecklingssystemet och sedan distribuerar dessa värden till produktionssystemet.
Detta görs genom att använda en kombination av delade konfigurationer, filen `config.php` och Commerce CLI-kommandot.

I det här exemplet används följande konfigurationsinställningar:

- **Vat Number** och **Store Name** för de delade konfigurationsinställningarna.

  Dessa finns under **Lager** > Inställningar > **Konfiguration** > Allmänt > **Allmänt**.

- **Skicka e-post till** för det känsliga konfigurationsvärdet.

  Detta finns under **Lager** > Inställningar > **Konfiguration** > Allmänt > **Kontakter**.

- **Standarddomän för e-post** för det systemspecifika konfigurationsvärdet.

  Detta hittar du under **Lager** > Inställningar > **Konfiguration** > Kunder > **Kundkonfiguration** > **Skapa nya kontoalternativ**.

Du kan använda samma procedur som i det här exemplet för att konfigurera inställningar i följande referenser:

- [Referens för känsliga och systemspecifika konfigurationssökvägar](../reference/config-reference-sens.md)
- [Referens för sökvägar för betalningskonfiguration](../reference/config-reference-payment.md)
- [Referens för andra konfigurationssökvägar](../reference/config-reference-general.md)
- [Referens för konfigurationssökvägar för Commerce Enterprise B2B-tillägg](../reference/config-reference-b2b.md)

## Innan du börjar

Konfigurera filsystembehörigheter och ägarskap enligt beskrivningen i [Krav för utvecklings-, bygg- och produktionssystem](../deployment/prerequisites.md) innan du börjar.

## Antaganden

Det här avsnittet innehåller ett exempel på hur du ändrar konfigurationen av produktionssystemet. Du kan välja olika konfigurationsalternativ om du vill.

I det här exemplet förutsätts följande:

- Du använder Git-källkontrollen
- Utvecklingssystemet är tillgängligt i en Git-fjärrdatabas med namnet `mconfig`
- Din Git-arbetsgrupp heter `m2.2_deploy`

## Steg 1: Ange konfigurationen i utvecklingssystemet

Så här anger du standardinställningar för nationella inställningar och viktenheter i utvecklingssystemet:

1. Logga in på Admin.
1. Klicka på **Lagrar** > Inställningar > **Konfiguration** > Allmänt > **Allmänt**.
1. Om du har fler än en webbplats tillgänglig kan du använda listan **Butiksvy** i det övre vänstra hörnet för att växla till en annan webbplats som på bilden nedan.

   ![Växla webbplatser](../../assets/configuration/split-deploy-switch-website.png)

1. Expandera **Lagra information** i den högra rutan.
1. Om det behövs avmarkerar du kryssrutan **Använd standard** bredvid fälten **Momsnummer** och **Butiksnamn**.
1. Ange ett tal i fältet (till exempel `12345`).
1. Ange ett värde (till exempel **) i fältet** Butiksnamn`My Store`.
1. Klicka på **Spara konfiguration**.
1. Klicka på **Kontakter** under Allmänt i den vänstra navigeringen.
1. Expandera **E-postalternativ** i den högra rutan.
1. Om det behövs avmarkerar du kryssrutan **Använd standard** bredvid fältet **Skicka e-post till**.
1. Ange en e-postadress i fältet.
1. Klicka på **Spara konfiguration**.
1. Använd listan **Butiksvy** för att välja **Standardkonfiguration** enligt bilden nedan.

   ![Växla till standardkonfigurationen](../../assets/configuration/split-deploy-default-config.png)

1. Klicka på Kunder > **Kundkonfiguration** i den vänstra rutan.
1. Expandera **Skapa nya kontoalternativ** i den högra rutan.
1. Om det behövs avmarkerar du kryssrutan **Använd systemvärde** bredvid fältet **Standarddomän för e-post**.
1. Ange ett domännamn i fältet.
1. Klicka på **Spara konfiguration**.
1. Rensa cachen om du uppmanas till det.

## Steg 2: Uppdatera konfigurationen

Nu när du har ändrat konfigurationen i Admin skriver du den delade konfigurationen till en fil enligt följande:

{{$include /help/_includes/config-save-config.md}}

Även om `app/etc/env.php` (den systemspecifika konfigurationen) har uppdaterats, ska du inte checka in den i källkontrollen.
Du kommer att skapa samma konfigurationsinställningar i produktionssystemet senare under den här proceduren.

## Steg 3: Uppdatera ditt byggsystem och generera filer

Nu när du har implementerat ändringarna i den delade konfigurationen för källkontroll kan du överföra dessa ändringar till ditt build-system, kompilera koden och generera statiska filer.

{{$include /help/_includes/config-update-build-system.md}}

## Steg 4: Uppdatera produktionssystemet

Det sista steget i processen är att uppdatera produktionssystemet. Du måste göra det i två delar:

- Uppdatera känsliga och systemspecifika inställningar
- Uppdatera de delade inställningarna

### Uppdatera känsliga och systemspecifika inställningar

Om du vill ange känsliga och systemspecifika inställningar med hjälp av systemvariabler måste du känna till följande:

- Omfång för varje inställning

  Om du följde instruktionerna i steg 1 är omfattningen för **Skicka e-post till** en webbplats och omfattningen för **Standarddomän för e-post** är global (d.v.s. standardkonfigurationsomfånget).

  Du behöver webbplatskoden för att ange konfigurationsvärdet **Skicka e-post till**.

  Mer information om hur du hittar det här värdet finns i: [Använd miljövariabler för att åsidosätta konfigurationsinställningar](../reference/override-config-settings.md#environment-variables).

- Konfigurationssökvägar för inställningarna som används i det här exemplet:

  | Inställningsnamn | Konfigurationssökväg |
  | -------------------- | -------------------------------------- |
  | Skicka e-post till | `contact/email/recipient_email` |
  | Standarddomän för e-post | `customer/create_account/email_domain` |

  Information om alla känsliga och systemspecifika konfigurationssökvägar finns i: [Känsliga och systemspecifika konfigurationssökvägar, referens](../reference/config-reference-sens.md).

### Ange variabler med CLI-kommandon

Använd följande CLI-kommandon för att ange systemspecifika och känsliga konfigurationsinställningar:

- `magento config:set` för systemspecifika inställningar
- `magento config:sensitive:set` för känsliga inställningar

Använd följande kommando för att ange den systemspecifika inställningen **Standarddomän för e-post**, som finns i standardomfånget:

```bash
bin/magento config:set customer/create_account/email_domain <email domain>
```

Du behöver inte använda scopet i kommandot eftersom det är standardscopet.

Om du vill ange värden för **Skicka e-post till** måste du dock känna till omfångstypen (`website`) och omfångskoden, som troligtvis är annorlunda på alla webbplatser.

Exempel:

```unix
bin/magento config:sensitive:set contact/email/recipient_email --scope=website --scope-code=<website code> <email address>
```

### Uppdatera de delade inställningarna

I det här avsnittet beskrivs hur du kan dra in alla ändringar du har gjort i din utveckling och bygga system till en produktionsmiljö, som uppdaterar de delade konfigurationsinställningarna (Butiksnamn och Momsnummer).

{{$include /help/_includes/config-update-prod-system.md}}

### Verifiera konfigurationsinställningar i administratören

Så här verifierar du konfigurationsinställningarna:

1. Logga in i produktionssystemets administratör.
1. Klicka på **Lagrar** > Inställningar > **Konfiguration** > Allmänt > **Allmänt**.
1. Använd listan **Butiksvy** i det övre vänstra hörnet för att växla till en annan webbplats.

   De alternativ för delad konfiguration som du anger i utvecklingssystemet visas på liknande sätt som följande.

   ![Kontrollera inställningarna i produktionssystemet](../../assets/configuration/split-deploy-verify-storeinfo.png)

   >[!INFO]
   >
   >Fältet **Butiksnamn** kan redigeras i webbplatsomfånget, men om du växlar till standardomfånget för konfiguration går det inte att redigera det. Detta är resultatet av hur du anger alternativen i utvecklingssystemet. Värdet **VAT Number** kan inte redigeras i webbplatsomfånget.

1. Om du inte redan har gjort det växlar du till Standardkonfigurationsomfång.
1. Klicka på **Kontakter** under Allmänt i den vänstra navigeringen.

   Fältet **Skicka e-post till** kan inte redigeras, vilket visas i bilden nedan. Det här är en känslig inställning.

   ![Kontrollera inställningarna i produktionssystemet](../../assets/configuration/split-deploy-verify-contacts.png)

1. Klicka på Kunder > **Kundkonfiguration** i den vänstra rutan.
1. Expandera **Skapa nya kontoalternativ** i den högra rutan.

   Värdet i fältet **Standarddomän för e-post** visas enligt följande. Detta är en systemspecifik inställning.

   ![Kontrollera inställningarna i produktionssystemet](../../assets/configuration/split-default-domain.png)
