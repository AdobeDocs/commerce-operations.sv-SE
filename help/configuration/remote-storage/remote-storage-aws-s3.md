---
title: Konfigurera AWS S3-bucket för fjärrlagring
description: Konfigurera ditt Commerce-projekt för att använda AWS S3-lagringstjänsten för fjärrlagring.
feature: Configuration, Storage
exl-id: e8aeade8-2ec4-4844-bd6c-ab9489d10436
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---

# Konfigurera AWS S3-bucket för fjärrlagring

[Amazon Simple Storage Service (Amazon S3)][AWS S3] är en objektlagringstjänst som erbjuder branschledande skalbarhet, datatillgänglighet, säkerhet och prestanda. AWS S3-tjänsten använder bucket, eller behållare, för datalagring. Den här konfigurationen kräver att du skapar en _privat_-bucket. Information om Adobe Commerce molninfrastruktur finns i [Konfigurera fjärrlagring för Commerce i molninfrastrukturen](cloud-support.md).

>[!WARNING]
>
>Adobe avråder starkt från att använda offentliga fickor eftersom detta utgör en allvarlig säkerhetsrisk.

**Så här aktiverar du fjärrlagring med AWS S3-adaptern**:

1. Logga in på din Amazon S3-instrumentpanel och skapa en _privat_-bucket.

1. Konfigurera [AWS IAM]-roller. Du kan också generera åtkomst och hemliga nycklar.

1. Inaktivera standarddatabaslagring.

   ```bash
   bin/magento config:set system/media_storage_configuration/media_database 0
   ```

1. Konfigurera Commerce att använda den privata bucket. En fullständig lista över parametrar finns i [Alternativ för fjärrlagring](remote-storage.md#remote-storage-options).

   ```bash
   bin/magento setup:config:set --remote-storage-driver="aws-s3" --remote-storage-bucket="<bucket-name>" --remote-storage-region="<region-name>" --remote-storage-prefix="<optional-prefix>" --remote-storage-key=<optional-access-key> --remote-storage-secret=<optional-secret-key> -n
   ```

1. Synkronisera mediefiler med fjärrlagring.

   ```bash
   bin/magento remote-storage:sync
   ```

## Konfigurera Nginx

Nginx kräver ytterligare konfiguration för att utföra autentisering med direktivet `proxy_pass`. Lägg till följande proxyinformation i filen `nginx.conf`:

>nginx.conf

```conf
location ~* \.(ico|jpg|jpeg|png|gif|svg|js|css|swf|eot|ttf|otf|woff|woff2)$ {
    # Proxying to AWS S3 storage.
    resolver 8.8.8.8;
    set $bucket "<s3-bucket-name>";
    proxy_pass https://s3.amazonaws.com/$bucket$uri;
    proxy_pass_request_body off;
    proxy_pass_request_headers off;
    proxy_intercept_errors on;
    proxy_hide_header "x-amz-id-2";
    proxy_hide_header "x-amz-request-id";
    proxy_hide_header "x-amz-storage-class";
    proxy_hide_header "Set-Cookie";
    proxy_ignore_headers "Set-Cookie";
}
```

### Autentisering

Om du använder åtkomstnycklar och hemliga nycklar i stället för [AWS IAM] -roller måste du inkludera [`ngx_aws_auth` Nginx-modulen ][ngx repo].

### Behörigheter

S3-integreringen bygger på möjligheten att generera och lagra cachelagrade bilder i det lokala filsystemet. Därför är mappbehörigheter för `pub/media` och liknande kataloger samma för S3 som för lokala lager.

### Filåtgärder

Vi rekommenderar starkt att du använder [!DNL Commerce]-filadaptermetoder i kodnings- eller tilläggsutvecklingen, oavsett fillagringstyp. När du använder S3 för lagring ska du inte använda interna I/O-åtgärder för PHP-filer, till exempel `copy`, `rename` eller `file_put_contents`, eftersom S3-filer inte finns i filsystemet. Se [DriverInterface.php](https://github.com/magento/magento2/blob/2.4-develop/lib/internal/Magento/Framework/Filesystem/DriverInterface.php#L18) för kodexempel.

<!-- link definitions -->

[AWS S3]: https://aws.amazon.com/s3
[AWS IAM]: https://aws.amazon.com/iam/
[ngx repo]: https://github.com/anomalizer/ngx_aws_auth
