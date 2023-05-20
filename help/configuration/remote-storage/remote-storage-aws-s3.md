---
title: Konfigurera AWS S3-bucket för fjärrlagring
description: Konfigurera ditt Commerce-projekt så att du kan använda lagringstjänsten AWS S3 för fjärrlagring.
exl-id: e8aeade8-2ec4-4844-bd6c-ab9489d10436
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 0%

---

# Konfigurera AWS S3-bucket för fjärrlagring

The [Amazon Simple Storage Service (Amazon S3)][AWS S3] är en objektlagringstjänst som erbjuder branschledande skalbarhet, datatillgänglighet, säkerhet och prestanda. AWS S3-tjänsten använder bucket, eller behållare, för datalagring. Den här konfigurationen kräver att du skapar en _private_ bucket. Information om Adobe Commerce molninfrastruktur finns på [Konfigurera fjärrlagring för Commerce i molninfrastruktur](cloud-support.md).

>[!WARNING]
>
>Adobe avråder starkt från att använda offentliga fickor eftersom detta utgör en allvarlig säkerhetsrisk.

**Aktivera fjärrlagring med AWS S3-adaptern**:

1. Logga in på din Amazon S3-kontrollpanel och skapa en _private_ bucket.

1. Konfigurera [AWS IAM] roller. Du kan också generera åtkomst och hemliga nycklar.

1. Inaktivera standarddatabaslagring.

   ```bash
   bin/magento config:set system/media_storage_configuration/media_database 0
   ```

1. Konfigurera Commerce för att använda den privata bucket. Se [Alternativ för fjärrlagring](remote-storage.md#remote-storage-options) för en fullständig lista över parametrar.

   ```bash
   bin/magento setup:config:set --remote-storage-driver="aws-s3" --remote-storage-bucket="<bucket-name>" --remote-storage-region="<region-name>" --remote-storage-prefix="<optional-prefix>" --remote-storage-key=<optional-access-key> --remote-storage-secret=<optional-secret-key> -n
   ```

1. Synkronisera mediefiler med fjärrlagring.

   ```bash
   bin/magento remote-storage:sync
   ```

## Konfigurera Nginx

Nginx kräver ytterligare konfiguration för att utföra autentisering med `proxy_pass` -direktivet. Lägg till följande proxyinformation i `nginx.conf` fil:

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

Om du använder åtkomst och hemliga nycklar i stället för [AWS IAM] roller, du måste inkludera [`ngx_aws_auth` Nginx-modul][ngx repo].

### Behörigheter

S3-integreringen bygger på möjligheten att generera och lagra cachelagrade bilder i det lokala filsystemet. Därför bör du ha mappbehörigheter för `pub/media` och liknande kataloger är samma för S3 som de är när de använder lokal lagring.

### Filåtgärder

Vi rekommenderar att du använder [!DNL Commerce] -metoder i kodningen eller tilläggsutvecklingen, oavsett fillagringstyp. Använd inte I/O-åtgärder för PHP-filer, som exempelvis när S3 används för lagring `copy`, `rename`, eller `file_put_contents`, eftersom S3-filer inte finns i filsystemet. Se [DriverInterface.php](https://github.com/magento/magento2/blob/2.4-develop/lib/internal/Magento/Framework/Filesystem/DriverInterface.php#L18) för kodexempel.

<!-- link definitions -->

[AWS S3]: https://aws.amazon.com/s3
[AWS IAM]: https://aws.amazon.com/iam/
[ngx repo]: https://github.com/anomalizer/ngx_aws_auth
