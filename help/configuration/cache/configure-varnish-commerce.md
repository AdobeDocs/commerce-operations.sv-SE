---
title: Konfigurera lack för handel
description: Lär dig att uppdatera och hantera din konfigurationsfil för lack för Commerce-programmet.
exl-id: 6c007ff9-493f-4df2-b7b4-438b41fd7e37
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# Konfigurera Commerce-programmet att använda engelska

Så här konfigurerar du Commerce att använda engelska:

1. Logga in på administratören som administratör.
1. Klicka **[!UICONTROL Stores]** > Inställningar > **Konfiguration** > **Avancerat** > **System** > **Helsidescache**.
1. Från **[!UICONTROL Caching Application]** lista, klicka på **Finska cachelagring**.
1. Ange ett värde i dialogrutan **[!UICONTROL TTL for public content]** fält.
1. Expandera **[!UICONTROL Varnish Configuration]** och ange följande information:

   | Fält | Beskrivning |
   | ----- | ----------- |
   | Åtkomstlista | Ange det fullständiga värdnamnet, IP-adressen eller [CIDR (Classless Inter-domain Routing)](https://www.digitalocean.com/community/tutorials/understanding-ip-addresses-subnets-and-cidr-notation-for-networking) IP-adressintervall för notationen som innehållet ska göras ogiltigt för. Se [Rensning av finans-cache](https://varnish-cache.org/docs/3.0/tutorial/purging.html). |
   | Serverdelsvärd | Ange det fullständiga värdnamnet eller IP-adressen och avlyssningsporten för lack _serverdel_ eller _origin-server_; dvs. servern som tillhandahåller innehållet varnish accelererar. Vanligtvis är det här din webbserver. Se [Backend-servrar för lack-cache](https://www.varnish-cache.org/docs/trunk/users-guide/vcl-backends.html). |
   | Backend-port | Ursprungsserverns lyssningsport. |
   | Respitperiod | Fristen avgör hur länge varnish skickar gammalt innehåll om backend-objektet inte svarar. Standardvärdet är 300 sekunder. |

1. Klicka **Spara konfiguration**.

Du kan även aktivera lack från kommandoraden i stället för att logga in i Admin med kommandoradsverktyget C:

```bash
bin/magento config:set --scope=default --scope-code=0 system/full_page_cache/caching_application 2
```

## Exportera en lack-konfigurationsfil

Så här exporterar du en lack-konfigurationsfil från administratören:

1. Klicka på en av exportknapparna för att skapa en `varnish.vcl` kan du använda med varnish.

   Om du till exempel har lack 4 klickar du på **Exportera VCL för lack 4**

   I följande bild visas ett exempel:

   ![Konfigurera Commerce att använda engelska i administratören](../../assets/configuration/varnish-admin-22.png)

1. Säkerhetskopiera dina befintliga `default.vcl`. Byt sedan namn på `varnish.vcl` som du just exporterat till `default.vcl`. Kopiera sedan filen till `/etc/varnish/` katalog.

   ```bash
   cp /etc/varnish/default.vcl /etc/varnish/default.vcl.bak2
   ```

   ```bash
   mv <download_directory>/varnish.vcl default.vcl
   ```

   ```bash
   cp <download_directory>/default.vcl /etc/varnish/default.vcl
   ```

1. Adobe rekommenderar att du öppnar `default.vcl` och ändra värdet för `acl purge` till IP-adressen för den Varniska värden. (Du kan ange flera värdar på separata rader eller också kan du använda CIDR-notation.)

   Till exempel:

   ```conf
    acl purge {
       "localhost";
    }
   ```

1. Om du vill anpassa Vagrant-hälsokontroller, respitläge eller helskärmsläge, se [Avancerad lack-konfiguration](config-varnish-advanced.md).

1. Starta om Varnish och webbservern:

   ```bash
   service varnish restart
   ```

   ```bash
   service httpd restart
   ```

## Cachelagra statiska filer

Statiska filer bör inte cachelagras som standard, men om du vill cachelagra dem kan du redigera avsnittet `Static files caching` i VCL för att ha följande innehåll:

```conf
# Static files should not be cached by default
  return (pass);

# But if you use a few locales and do not use CDN you can enable caching static files by commenting previous line (#return (pass);) and uncommenting next 3 lines
  #unset req.http.Https;
  #unset req.http./* {{ ssl_offloaded_header }} */;
  #unset req.http.Cookie;
```

Du måste göra dessa ändringar innan du konfigurerar Commerce att använda engelska.
