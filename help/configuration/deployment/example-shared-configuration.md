---
title: Exempel med en delad konfiguration
description: Se ett exempel på hur du ändrar inställningar i ett utvecklingssystem med en delad konfigurationsfil.
exl-id: c980ec01-ca2d-43db-b68d-8e9435e07e6a
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 0%

---

# Exempel med en delad konfiguration

I det här exemplet visas hur du ändrar följande inställningar i utvecklingssystemet, uppdaterar den delade konfigurationsfilen, `config.php`, i ditt build-system och implementerar samma inställningar i produktionssystemet:

- Tidszon
- Viktenhet

De här inställningarna är tillgängliga i Admin i **Lagrar** > Inställningar > **Konfiguration** > Allmänt > **Allmänt**.

Du kan använda samma procedur för att konfigurera icke-känsliga, icke-systemspecifika inställningar i följande referenser:

- [Referens för andra konfigurationssökvägar](../reference/config-reference-general.md)
- [Referens för sökvägar för betalningskonfiguration](../reference/config-reference-payment.md)
- [Referens för konfigurationssökvägar för Commerce Enterprise B2B-tillägg](../reference/config-reference-b2b.md)

## Innan du börjar

Innan du börjar konfigurerar du filsystembehörigheter och ägarskap enligt beskrivningen i [Förutsättningar för utvecklings-, bygg- och produktionssystem](../deployment/prerequisites.md).

## Antaganden

Det här avsnittet innehåller ett exempel på hur du ändrar konfigurationen av produktionssystemet. Du kan välja olika konfigurationsalternativ om du vill.

I det här exemplet förutsätts följande:

- Du använder Git-källkontrollen
- Utvecklingssystemet är tillgängligt i en Git-fjärrdatabas med namnet `mconfig`
- Din Git-arbetsgrupp heter `m2.2_deploy`

## Steg 1: Ange konfigurationen i utvecklingssystemet

Så här anger du tidszon- och viktenheter i utvecklingssystemet:

1. Logga in på Admin.
1. Klicka på **Lagrar** > Inställningar > **Konfiguration** > Allmänt > **Allmänt**.
1. Expandera **Språkalternativ** i den högra rutan.

   I bilden nedan visas ett exempel.

   ![Ange språkinställningar i utvecklingssystemet](../../assets/configuration/split-deploy-set-locale.png)

1. Klicka på **GMT+00:00 (UTC)** i listan **Tidszon**.
1. Avmarkera kryssrutan **Använd systemvärde** intill fältet **Viktenhet**.
1. Klicka på **kgs** i listan **Viktenhet**.
1. Klicka på **Spara konfiguration**.
1. Rensa cachen om du uppmanas till det.

## Steg 2: Uppdatera den delade konfigurationen

Generera den delade konfigurationsfilen, `app/etc/config.php`, i utvecklingssystemet och överför den med hjälp av källkontroll till ditt build-system, vilket beskrivs i det här avsnittet.

{{$include /help/_includes/config-save-config.md}}

## Steg 3: Uppdatera ditt byggsystem och generera filer

Nu när du har implementerat ändringarna i den delade konfigurationen för källkontroll kan du dra in dessa ändringar i ditt build-system, kompilera kod och generera statiska filer. Det sista steget är att föra över dessa ändringar till produktionssystemet. Resultatet blir att produktionssystemets konfiguration matchar utvecklingssystemet.

{{$include /help/_includes/config-update-build-system.md}}

## Steg 4: Uppdatera produktionssystemet

Det sista steget i processen är att uppdatera produktionssystemet från källkontroll. Då uppdateras alla ändringar du har gjort i dina utvecklings- och konstruktionssystem, vilket innebär att ditt produktionssystem är helt uppdaterat.

{{$include /help/_includes/config-update-prod-system.md}}

### Verifiera ändringarna i administratören

**Så här verifierar du att de här inställningarna inte går att redigera i Admin**:

1. Logga in på Admin.
1. Klicka på **Lagrar** > Inställningar > **Konfiguration** > Allmänt > **Allmänt**.
1. Expandera **Språkalternativ** i den högra rutan.

   De alternativ du just anger visas enligt följande:

   ![Konfigurationsalternativen kan inte redigeras i administratören](../../assets/configuration/split-deploy-not-editable.png)

>[!INFO]
>
>Om du vill ändra en inställning som är låst i Admin använder du kommandot [`magento config:set --lock` ](../cli/set-configuration-values.md).
