---
title: Exempel med CLI-kommandon
description: Se ett exempel på hur du ställer in delade, systemspecifika och känsliga värden i utvecklingssystemet med kommandoraden.
exl-id: d0058e9f-a5a9-48a6-9c66-c61515666335
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1019'
ht-degree: 0%

---

# Exempel med CLI-kommandon

I det här exemplet visas hur du ställer in delade, systemspecifika och känsliga värden i utvecklingssystemet och sedan distribuerar dessa värden till produktionssystemet.
Detta görs genom att använda en kombination av delade konfigurationer, `config.php` och Commerce CLI-kommandot.

I det här exemplet används följande konfigurationsinställningar:

- **momsregistreringsnummer** och **Butiksnamn** för de delade konfigurationsinställningarna.

   Dessa finns under **Lager** > Inställningar > **Konfiguration** > Allmänt > **Allmänt**.

- **Skicka e-post till** för det känsliga konfigurationsvärdet.

   Detta finns under **Lager** > Inställningar > **Konfiguration** > Allmänt > **Kontakter**.

- **Standarddomän för e-post** för det systemspecifika konfigurationsvärdet.

   Detta finns under **Lager** > Inställningar > **Konfiguration** > Kunder > **Kundkonfiguration** > **Skapa nya kontoalternativ**.

Du kan använda samma procedur som i det här exemplet för att konfigurera inställningar i följande referenser:

- [Referens för känsliga och systemspecifika konfigurationssökvägar](../reference/config-reference-sens.md)
- [Referens för sökvägar för betalningskonfiguration](../reference/config-reference-payment.md)
- [Andra konfigurationssökvägar - referens](../reference/config-reference-general.md)
- [Referens för konfigurationssökvägar för Commerce Enterprise B2B-tillägg](../reference/config-reference-b2b.md)

## Innan du börjar

Innan du börjar ska du konfigurera filsystembehörigheter och ägarskap enligt [Krav för utvecklings-, bygg- och produktionssystem](../deployment/prerequisites.md).

## Antaganden

Det här avsnittet innehåller ett exempel på hur du ändrar konfigurationen av produktionssystemet. Du kan välja olika konfigurationsalternativ om du vill.

I det här exemplet förutsätts följande:

- Du använder Git-källkontrollen
- Utvecklingssystemet är tillgängligt i en Git-fjärrdatabas med namnet `mconfig`
- Din Git-arbetsgrupp heter `m2.2_deploy`

## Steg 1: Ange konfigurationen i utvecklingssystemet

Så här anger du standardinställningar för nationella inställningar och viktenheter i utvecklingssystemet:

1. Logga in på Admin.
1. Klicka **Lager** > Inställningar > **Konfiguration** > Allmänt > **Allmänt**.
1. Om du har fler än en webbplats tillgänglig använder du **Butiksvy** i det övre vänstra hörnet för att växla till en annan webbplats som bilden nedan visar.

   ![Byt webbplatser](../../assets/configuration/split-deploy-switch-website.png)

1. Expandera i den högra rutan **Butiksinformation**.
1. Rensa **Använd standard** kryssrutan bredvid **Momsnummer** och **Butiksnamn** fält.
1. Ange en siffra i fältet (t.ex. `12345`).
1. I **Butiksnamn** fält, ange ett värde (som `My Store`).
1. Klicka **Spara konfiguration**.
1. Klicka på under Allmänt i den vänstra navigeringen **Kontakter**.
1. Expandera i den högra rutan **E-postalternativ**.
1. Rensa **Använd standard** kryssrutan bredvid **Skicka e-post till** fält.
1. Ange en e-postadress i fältet.
1. Klicka **Spara konfiguration**.
1. Använd **Butiksvy** listan för att välja **Standardkonfiguration** som bilden nedan visar.

   ![Växla till standardkonfigurationen](../../assets/configuration/split-deploy-default-config.png)

1. Klicka på Kunder > **Kundkonfiguration**.
1. Expandera i den högra rutan **Skapa nya kontoalternativ**.
1. Rensa **Använd systemvärde** kryssrutan bredvid **Standarddomän för e-post** fält.
1. Ange ett domännamn i fältet.
1. Klicka **Spara konfiguration**.
1. Rensa cachen om du uppmanas till det.

## Steg 2: Uppdatera konfigurationen

Nu när du har ändrat konfigurationen i Admin skriver du den delade konfigurationen till en fil enligt följande:

{{$include /help/_includes/config-save-config.md}}

Även om `app/etc/env.php` (den systemspecifika konfigurationen) uppdaterades, checka inte in den i källkontrollen.
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

   Om du följde instruktionerna i steg 1, kan du **Skicka e-post till** är webbplats och har **Standarddomän för e-post** är global (d.v.s. standardkonfigurationsomfånget).

   Du behöver webbplatskoden för att ange **Skicka e-post till** konfigurationsvärde.

   Mer information om hur du hittar det här värdet finns i: [Använd miljövariabler för att åsidosätta konfigurationsinställningar](../reference/override-config-settings.md#environment-variables).

- Konfigurationssökvägar för inställningarna som används i det här exemplet:

   | Inställningsnamn | Konfigurationssökväg |
   | -------------------- | -------------------------------------- |
   | Skicka e-post till | `contact/email/recipient_email` |
   | Standarddomän för e-post | `customer/create_account/email_domain` |

   Information om alla känsliga och systemspecifika konfigurationssökvägar finns i: [Referens för känsliga och systemspecifika konfigurationssökvägar](../reference/config-reference-sens.md).

### Ange variabler med CLI-kommandon

Använd följande CLI-kommandon för att ange systemspecifika och känsliga konfigurationsinställningar:

- `magento config:set` för systemspecifika inställningar
- `magento config:sensitive:set` för känsliga inställningar

Ange systemspecifik inställning **Standarddomän för e-post**, som finns i standardomfånget, använder du följande kommando:

```bash
bin/magento config:set customer/create_account/email_domain <email domain>
```

Du behöver inte använda omfånget i kommandot eftersom det är standardomfånget.

Ange värden för **Skicka e-post till** Du måste dock känna till omfångstypen (`website`) och omfångskoden, som troligtvis skiljer sig åt på alla platser.

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
1. Klicka **Lager** > Inställningar > **Konfiguration** > Allmänt > **Allmänt**.
1. Använd **Butiksvy** i det övre vänstra hörnet för att byta till en annan webbplats.

   De alternativ för delad konfiguration som du anger i utvecklingssystemet visas på liknande sätt som följande.

   ![Kontrollera inställningar i produktionssystemet](../../assets/configuration/split-deploy-verify-storeinfo.png)

   >[!INFO]
   >
   >The **Butiksnamn** -fältet kan redigeras i webbplatsens omfång, men om du växlar till standardomfånget för konfiguration går det inte att redigera det. Detta är resultatet av hur du anger alternativen i utvecklingssystemet. Värdet för **Momsnummer** går inte att redigera i webbplatsens omfång.

1. Om du inte redan har gjort det växlar du till Standardkonfigurationsomfång.
1. Klicka på under Allmänt i den vänstra navigeringen **Kontakter**.

   The **Skicka e-post till** -fältet går inte att redigera, vilket visas i bilden nedan. Det här är en känslig inställning.

   ![Kontrollera inställningar i produktionssystemet](../../assets/configuration/split-deploy-verify-contacts.png)

1. Klicka på Kunder > **Kundkonfiguration**.
1. Expandera i den högra rutan **Skapa nya kontoalternativ**.

   Värdet för **Standarddomän för e-post** visas enligt följande. Detta är en systemspecifik inställning.

   ![Kontrollera inställningar i produktionssystemet](../../assets/configuration/split-default-domain.png)
