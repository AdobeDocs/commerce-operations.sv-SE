---
title: Fjärrlagring för Commerce i molninfrastruktur
description: Mer information om hur du konfigurerar fjärrlagring för Adobe Commerce om molninfrastruktur finns i vägledningen.
feature: Configuration, Cloud, Storage
exl-id: da352466-13f2-42e4-a589-3b0a89728467
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '579'
ht-degree: 0%

---

# Konfigurera fjärrlagring för Commerce i molninfrastruktur

Från och med paketet `ece-tools` 2002.1.5 kan du använda en miljövariabel för att aktivera modulen Fjärrlagring. Fjärrlagringsmodulen har dock _begränsat_ stöd för Adobe Commerce i molninfrastrukturen. Adobe kan inte felsöka nätverkskorttjänsten från tredje part helt.

## Miljövariabel

Variabeln `REMOTE_STORAGE` används under [distributionsfasen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/process.html?lang=sv-SE) i ett molninfrastrukturprojekt.

### `REMOTE_STORAGE`

- **Standard**—_Inte angivet_
- **Version** - Commerce 2.4.2 och senare

Konfigurera ett _lagringskort_ för att lagra mediefiler i en beständig fjärrlagringsbehållare med hjälp av en lagringstjänst, till exempel AWS S3. Aktivera modulen Fjärrlagring för att förbättra prestanda i molnprojekt med komplexa konfigurationer med flera servrar som måste dela resurser. Följande är ett exempel på fjärrlagringskonfigurationen som använder filen `.magento.env.yaml`:

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

Ange variabeln `REMOTE_STORAGE` som en [miljönivåvariabel](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/variable-levels.html?lang=sv-SE) så att filer inte delas mellan produktions-, mellanlagrings- och integreringsmiljöer. Genom att ställa in variablerna på miljönivå får du endast flexibilitet att använda fjärrlagring i vissa miljöer, till exempel genom att utesluta användning av fjärrlagring i integreringsmiljön.

**Så här lägger du till fjärrlagringsvariabeln med molnet-CLI**:

```bash
magento-cloud variable:create --level environment --name REMOTE_STORAGE --json true --inheritable false --value '{"driver":"aws-s3","prefix":"uat","config":{"bucket":"aws-bucket-id","region":"eu-west-1","key":"optional-key","secret":"optional-secret"}}'
```

Detta skapar en `REMOTE_STORAGE`-variabel med den angivna JSON-konfigurationen. Variabeln `REMOTE_STORAGE` tar en JSON-sträng för att konfigurera fjärrlagring. Följande är ett exempel på JSON-konfiguration:

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

**Så här lägger du till fjärrlagringsvariabeln med Project Web Interface**:

1. Välj miljön från vänster i _Project Web Interface_.

1. Klicka på ikonen **Konfigurera miljö** .

1. Klicka på fliken **Variabler** i vyn _Konfigurera miljö_ .

1. Klicka på **Lägg till variabel**.

1. Ange `REMOTE_STORAGE` i fältet _Namn_

1. Lägg till JSON-konfigurationen i fältet _Värde_.

1. Markera **JSON-värdet** och **Känsligt**. Avmarkera **Ärftligt av underordnade miljöer**.

1. Klicka på **Lägg till variabel**.

### Använd valfri autentisering

`key` och `secret` är valfria. När du skapar variabeln kan du dölja `key` och `secret` genom att välja alternativet `sensitive`. Med den här inställningen syns inte värdena i webbgränssnittet. Se [Variabel synlighet](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/variable-levels.html?lang=sv-SE#visibility) i guiden _Commerce om molninfrastruktur_.

Om du vill använda en annan autentiseringsmetod utelämnar du `key` och `secret` från JSON-konfigurationen. Konfigurera den alternativa autentiseringsmetoden och verifiera att servern är auktoriserad för S3-bucket.

### Synkronisera fjärrlagring

När du har aktiverat modulen Fjärrlagring synkroniserar du de aktuella mediefilerna till fjärrlagringsplatsen.

**Så här startar du synkroniseringen**:

1. Använd SSH för att logga in på fjärrmiljön med konfigurerad fjärrlagring.

1. Starta synkroniseringen.

```bash
bin/magento remote-storage:sync 
```

## Snabb konfiguration

Om du väljer att använda fjärrlagringslösningen med ett Adobe Commerce-projekt för molninfrastruktur kan du använda [Amazon S3](https://docs.fastly.com/en/guides/amazon-s3) i _Snabbt_ -dokumentationen för att se till att snabbbildsoptimering fungerar med AWS S3.

Förbered dig med dina [snabbuppgifter](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=sv-SE#get-fastly-credentials). I Pro-projekt kan du använda SSH för att ansluta till servern och hämta snabbinloggningsuppgifterna från filen `/mnt/shared/fastly_tokens.txt`. För mellanlagrings- och produktionsmiljöer finns unika autentiseringsuppgifter. Du måste hämta autentiseringsuppgifterna för varje miljö.

Fortsätt konfigurera fjärrlagring för molnprojekt med följande uppgifter:

1. Konfigurera en [snabb backend-integrering](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/Edge-Modules/EDGE-MODULE-OTHER-CMS-INTEGRATION.md).

1. Skapa VCL-logik för [AWS S3-autentisering](https://docs.fastly.com/en/guides/amazon-s3#using-an-amazon-s3-private-bucket).

1. Skapa VCL-logik för [backend-begäranden till AWS S3-bucket](https://developer.fastly.com/reference/vcl/variables/backend-connection/req-backend/).
