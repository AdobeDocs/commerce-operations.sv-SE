---
title: Konfigurera lack för Commerce
description: Lär dig hur du uppdaterar och hanterar din konfigurationsfil för lack för Commerce-programmet.
feature: Configuration, Cache, SCD
exl-id: 6c007ff9-493f-4df2-b7b4-438b41fd7e37
source-git-commit: 602a1ef82fcb8d30ff027db0fe0aacb981c7e08e
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# Konfigurera Commerce-programmet så att det använder engelska

Så här konfigurerar du Commerce att använda engelska:

1. Logga in på administratören som administratör.
1. Klicka på **[!UICONTROL Stores]** > Inställningar > **Konfiguration** > **Avancerat** > **System** > **Fullsidescache**.
1. Klicka på **Varnish Caching** i listan **[!UICONTROL Caching Application]**.
1. Ange ett värde i fältet **[!UICONTROL TTL for public content]**.
1. Expandera **[!UICONTROL Varnish Configuration]** och ange följande information:

   | Fält | Beskrivning |
   | ----- | ----------- |
   | Åtkomstlista | Ange det fullständigt kvalificerade värdnamnet, IP-adressen eller CIDR-adressintervallet [för klassfri routning mellan domäner (CIDR)](https://www.digitalocean.com/community/tutorials/understanding-ip-addresses-subnets-and-cidr-notation-for-networking) som innehållet ska ogiltigförklaras för. Se [Rensa lack-cache](https://varnish-cache.org/docs/3.0/tutorial/purging.html). |
   | Serverdelsvärd | Ange det fullständiga värdnamnet eller IP-adressen och avlyssningsporten för den fullständiga värdservern _serverdelen_ eller _ursprungsservern_, det vill säga servern som tillhandahåller innehållet lack accelererar. Vanligtvis är det här din webbserver. Se [Serverdelsservrar för lack-cache](https://www.varnish-cache.org/docs/trunk/users-guide/vcl-backends.html). |
   | Backend-port | Ursprungsserverns lyssningsport. |
   | Respitperiod | Avgör hur länge varnish visar inaktuellt innehåll om serverdelen inte är responsiv. Standardvärdet är 300 sekunder. |
   | Hanterar parameterstorlek | Anger det maximala antalet [layoutreferenser](https://developer.adobe.com/commerce/frontend-core/guide/layouts/#layout-handles) som kan bearbetas på HTTP-slutpunkten i [`{BASE-URL}/page_cache/block/esi`](use-varnish-esi.md) för helsidescache. Genom att begränsa storleken kan du förbättra säkerheten och prestandan. Standardvärdet är 100. |

1. Klicka på **Spara konfiguration**.

Du kan även aktivera lack från kommandoraden i stället för att logga in i Admin med kommandoradsverktyget C:

```bash
bin/magento config:set --scope=default --scope-code=0 system/full_page_cache/caching_application 2
```

## Exportera en lack-konfigurationsfil

Så här exporterar du en lack-konfigurationsfil från administratören:

1. Klicka på en av exportknapparna för att skapa en `varnish.vcl` som du kan använda med lack.

   Om du till exempel har lack 4 klickar du på **Exportera VCL för lack 4**

   I följande bild visas ett exempel:

   ![Konfigurera Commerce att använda engelska i administratören](../../assets/configuration/varnish-admin-22.png)

1. Säkerhetskopiera din befintliga `default.vcl`. Byt sedan namn på filen `varnish.vcl` som du just exporterade till `default.vcl`. Kopiera sedan filen till katalogen `/etc/varnish/`.

   ```bash
   cp /etc/varnish/default.vcl /etc/varnish/default.vcl.bak2
   ```

   ```bash
   mv <download_directory>/varnish.vcl default.vcl
   ```

   ```bash
   cp <download_directory>/default.vcl /etc/varnish/default.vcl
   ```

1. Adobe rekommenderar att du öppnar `default.vcl` och ändrar värdet för `acl purge` till IP-adressen för värden i Valnish. (Du kan ange flera värdar på separata rader eller också kan du använda CIDR-notation.)

   Exempel:

   ```conf
    acl purge {
       "localhost";
    }
   ```

1. Om du vill anpassa Vagrant-hälsokontroller, respitläge eller konfiguration för helskärmsläge, se [Avancerad lack-konfiguration](config-varnish-advanced.md).

1. Starta om Varnish och webbservern:

   ```bash
   service varnish restart
   ```

   ```bash
   service httpd restart
   ```

## Cachelagra statiska filer

Statiska filer ska inte cachelagras som standard, men om du vill cachelagra dem kan du redigera avsnittet `Static files caching` i VCL så att det har följande innehåll:

```conf
# Static files should not be cached by default
  return (pass);

# But if you use a few locales and do not use CDN you can enable caching static files by commenting previous line (#return (pass);) and uncommenting next 3 lines
  #unset req.http.Https;
  #unset req.http./* {{ ssl_offloaded_header }} */;
  #unset req.http.Cookie;
```

Du måste göra dessa ändringar innan du konfigurerar Commerce att använda lack.
