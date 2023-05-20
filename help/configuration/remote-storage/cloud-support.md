---
title: Fjärrlagring för Commerce i molninfrastruktur
description: Mer information om hur du konfigurerar fjärrlagring för Adobe Commerce om molninfrastruktur finns i vägledningen.
exl-id: da352466-13f2-42e4-a589-3b0a89728467
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '630'
ht-degree: 0%

---

# Konfigurera fjärrlagring för Commerce i molninfrastruktur

Börja med `ece-tools` paket 2002.1.5 kan du använda en miljövariabel för att aktivera modulen Fjärrlagring; modulen Fjärrlagring har _begränsad_ stöd för Adobe Commerce i molninfrastruktur. Adobe kan inte felsöka nätverkskorttjänsten från tredje part helt.

## Miljövariabel

The `REMOTE_STORAGE` variabeln används under [distributionsfas](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/process.html) av ett molninfrastrukturprojekt.

### `REMOTE_STORAGE`

- **Standard**—_Ej angiven_
- **Version**—Commerce 2.4.2 och senare

Konfigurera en _lagringskort_ att lagra mediefiler i en beständig fjärrlagringsbehållare med hjälp av en lagringstjänst som AWS S3. Aktivera modulen Fjärrlagring för att förbättra prestanda i molnprojekt med komplexa konfigurationer med flera servrar som måste dela resurser. Följande är ett exempel på konfiguration av fjärrlagring med `.magento.env.yaml` fil:

```yaml
stage:
  deploy:
    REMOTE_STORAGE:
      driver: aws-s3 # Required
      prefix: cloud # Optional
      config:
        bucket: my-bucket # Required
        region: my-region # Required
        key: my-key # Optional
        secret: my-secret-key # Optional
```

### Ange variabel med CLI i molnet

Ange `REMOTE_STORAGE` variabel som [miljönivåvariabel](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/variable-levels.html) så att filer inte delas mellan produktions-, förproduktionsmiljö- och integreringsmiljöer. Genom att ställa in variablerna på miljönivå får du endast flexibilitet att använda fjärrlagring i vissa miljöer, till exempel genom att utesluta användning av fjärrlagring i integreringsmiljön.

**Lägga till variabeln för fjärrlagring med hjälp av CLI för molnet**:

```bash
magento-cloud variable:create --level environment --name REMOTE_STORAGE --json true --inheritable false --value '{"driver":"aws-s3","prefix":"uat","config":{"bucket":"aws-bucket-id","region":"eu-west-1","key":"optional-key","secret":"optional-secret"}}'
```

Detta skapar en `REMOTE_STORAGE` variabel med angiven JSON-konfiguration. The `REMOTE_STORAGE` variabeln använder en JSON-sträng för att konfigurera fjärrlagring. Följande är ett exempel på JSON-konfiguration:

```json
{
  "driver": "aws-s3",
  "prefix": "uat",
  "config": {
    "bucket": "aws-bucket-id",
    "region": "aws-region-id",
    "key": "optional-key",
    "secret": "optional-secret"
  }
}
```

När du har skapat konfigurationen och distribuerat bör distributionsloggarna innehålla information om konfigurationen för fjärrlagring, till exempel `INFO: Remote storage driver set to: "aws-s3"`

### Ange variabel med Project Web Interface

Du kan också använda Project Web Interface för att lägga till variabeln i lämplig miljö.

**Lägga till variabeln för fjärrlagring med Project Web Interface**:

1. I _Project Web Interface_ väljer du miljö från vänster.

1. Klicka på **Konfigurera miljö** ikon.

1. I _Konfigurera miljö_ visa klickar du på **Variabler** -fliken.

1. Klicka **Lägg till variabel**.

1. I _Namn_ fält, ange `REMOTE_STORAGE`

1. I _Värde_ lägger du till JSON-konfigurationen.

1. Välj **JSON-värde** och **Känslig**; avmarkera **Ärftlig av underordnade miljöer**.

1. Klicka **Lägg till variabel**.

### Använd valfri autentisering

The `key` och `secret` är valfria. När du skapar variabeln kan du dölja `key` och `secret` genom att välja `sensitive` alternativ. Med den här inställningen syns inte värdena i webbgränssnittet. Se [Variabel synlighet](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/variable-levels.html#visibility) i _Guide för Commerce on Cloud Infrastructure_.

Om du vill använda en annan autentiseringsmetod utelämnar du `key` och `secret` från JSON-konfigurationen, Konfigurera den alternativa autentiseringsmetoden och verifiera att servern är auktoriserad för S3-bucket.

### Synkronisera fjärrlagring

När du har aktiverat modulen Fjärrlagring synkroniserar du de aktuella mediefilerna till fjärrlagringsplatsen.

**Starta synkroniseringen**:

1. Använd SSH för att logga in på fjärrmiljön med konfigurerad fjärrlagring.

1. Starta synkroniseringen.

```bash
bin/magento remote-storage:sync 
```

## Snabb konfiguration

Om du väljer att använda fjärrlagringslösningen med ett Adobe Commerce-projekt för molninfrastruktur använder du [Amazon S3](https://docs.fastly.com/en/guides/amazon-s3) i _Snabbt_ dokumentation som säkerställer att Snabb bildoptimering fungerar med AWS S3.

Var redo med [Autentiseringsuppgifter snabbt](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#get-fastly-credentials). I Pro-projekt kan du använda SSH för att ansluta till servern och hämta inloggningsuppgifterna snabbt från `/mnt/shared/fastly_tokens.txt` -fil. För mellanlagrings- och produktionsmiljöer finns unika autentiseringsuppgifter. Du måste hämta autentiseringsuppgifterna för varje miljö.

Fortsätt konfigurera fjärrlagring för molnprojekt med följande uppgifter:

1. Konfigurera en [Snabb integration med backend](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/Edge-Modules/EDGE-MODULE-OTHER-CMS-INTEGRATION.md).

1. Skapa VCL-logik för [AWS S3-autentisering](https://docs.fastly.com/en/guides/amazon-s3#using-an-amazon-s3-private-bucket).

1. Skapa VCL-logik för [backend-begäranden till AWS S3-bucket](https://developer.fastly.com/reference/vcl/variables/backend-connection/req-backend/).
