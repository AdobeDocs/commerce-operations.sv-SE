---
title: Konfigurera webbserver
description: Lär dig hur du konfigurerar webbservern så att den fungerar med lack.
source-git-commit: ee2e446edf79efcd7cbbd67248f8e7ece06bfefd
workflow-type: tm+mt
source-wordcount: '746'
ht-degree: 0%

---


# Konfigurera webbservern

Konfigurera webbservern så att den lyssnar på en annan port än standardporten 80 eftersom Varnish svarar direkt på inkommande HTTP-begäranden, inte på webbservern.

I följande avsnitt används port 8080 som exempel.

**Så här ändrar du Apache 2.4-lyssningsporten**:

1. Öppna `/etc/httpd/conf/httpd.conf` i en textredigerare.
1. Leta reda på `Listen` -direktivet.
1. Ändra värdet för lyssningsporten till `8080`. (Du kan använda valfri tillgänglig lyssningsport.)
1. Spara ändringarna i `httpd.conf` och avsluta textredigeraren.

## Ändra konfigurationen för lack-systemet

Så här ändrar du systemkonfigurationen för engelska:

1. Som användare med `root` behörighet, öppna din VDanish-konfigurationsfil i en textredigerare:

   - CentOS 6: `/etc/sysconfig/varnish`
   - CentOS 7: `/etc/varnish/varnish.params`
   - Debian: `/etc/default/varnish`
   - Ubuntu: `/etc/default/varnish`

1. Ställ in Varnish-lyssningsporten på 80:

   ```conf
   VARNISH_LISTEN_PORT=80
   ```

   Kontrollera att DAEMON_OPTS innehåller rätt avlyssningsport för `-a` parameter (även om VARNISH_LISTEN_PORT har rätt värde):

   ```conf
   DAEMON_OPTS="-a :80 \
      -T localhost:6082 \
      -f /etc/varnish/default.vcl \
      -S /etc/varnish/secret \
      -s malloc,256m"
   ```

1. Spara ändringarna i konfigurationsfilen för lack och avsluta textredigeraren.

### Ändra standard-VCL

I det här avsnittet beskrivs hur du tillhandahåller minimal konfiguration så att Varnish returnerar HTTP-svarshuvuden. Detta gör att du kan verifiera att lack fungerar innan du konfigurerar [!DNL Commerce] för att använda lack.

Så här konfigurerar du engelska minimalt:

1. Säkerhetskopiera `default.vcl`:

   ```bash
   cp /etc/varnish/default.vcl /etc/varnish/default.vcl.bak
   ```

1. Öppna `/etc/varnish/default.vcl` i en textredigerare.
1. Leta reda på följande stanza:

   ```conf
   backend default {
       .host = "127.0.0.1";
       .port = "80";
   }
   ```

1. Ersätt värdet för `.host` med det fullständiga värdnamnet eller IP-adressen och avlyssningsporten för varnish _serverdel_ eller _origin-server_; dvs. servern som tillhandahåller innehållet varnish kommer att accelerera.

   Vanligtvis är det här din webbserver. Se [Serverlösningar](https://varnish-cache.org/docs/trunk/users-guide/vcl-backends.html) i _Varnish - guide_.

1. Ersätt värdet för `.port` med webbserverns lyssningsport (8080 i det här exemplet).

   Exempel: Apache installeras på värd 192.0.2.55 och Apache lyssnar på port 8080:

   ```conf
   backend default {
       .host = "192.0.2.55";
       .port = "8080";
   }
   ```

   >[!INFO]
   >
   >Om lack och Apache körs på samma värd rekommenderar Adobe att du använder en IP-adress eller ett värdnamn och inte `localhost`.

1. Spara ändringarna i `default.vcl` och avsluta textredigeraren.

1. Starta om lack:

   ```bash
   service varnish restart
   ```

Om det inte går att starta Varnish kan du försöka köra det från kommandoraden på följande sätt:

```bash
varnishd -d -f /etc/varnish/default.vcl
```

Detta bör visa felmeddelanden.


>[!INFO]
>
>Om lack inte startar som en tjänst måste du konfigurera SELinux-regler så att den kan köras.

## Kontrollera att lack fungerar

I följande avsnitt beskrivs hur du kan verifiera att Varnish fungerar, men _utan_ konfigurerar Commerce för att använda den. Du bör prova detta innan du konfigurerar Commerce.

Utför de uppgifter som beskrivs i följande avsnitt i den ordning som visas:

- [Start Varnish](#start-varnish)
- [&quot;netstat&quot;](#netstat)

### Start Varnish

Ange: `service varnish start`

Om Varnish inte kan starta som en tjänst startar du den från kommandoraden enligt följande:

1. Starta Varnish CLI:

   ```bash
   varnishd -d -f /etc/varnish/default.vcl
   ```

1. Starta den underordnade processen för lack:

   Ange `start`

   Följande meddelanden visas för att bekräfta att starten lyckades:

   ```terminal
   child (29805) Started
   200 0
   
   Child (29805) said
   Child (29805) said Child starts
   ```

### netstat

Logga in på Varnish-servern och ange följande kommando:

```bash
netstat -tulpn
```

Leta efter följande utdata:

```terminal
tcp        0      0 0.0.0.0:80                  0.0.0.0:*                   LISTEN      32614/varnishd
tcp        0      0 127.0.0.1:58484             0.0.0.0:*                   LISTEN      32604/varnishd
tcp        0      0 :::8080                     :::*                        LISTEN      26822/httpd
tcp        0      0 ::1:48509                   :::*                        LISTEN      32604/varnishd
```

I föregående exempel visas hur Varnish körs på port 80 och Apache som körs på port 8080.

Om du inte ser utdata för `varnishd`, se till att Varnish är igång.

Se [`netstat` alternativ](https://tldp.org/LDP/nag2/x-087-2-iface.netstat.html).

## Installera Commerce-programvaran

Installera Commerce-programvaran om du inte redan har gjort det. När du uppmanas att ange en bas-URL använder du värddatorn Varnish och port 80 (för Varnish) eftersom Varnish tar emot alla inkommande HTTP-begäranden.

Möjligt fel vid installation av Commerce:

```terminal
Error 503 Service Unavailable
Service Unavailable
XID: 303394517
Varnish cache server
```

Om det här felet uppstår kan du redigera `default.vcl` och lägga till en timeout i `backend` stanza enligt följande:

```conf
backend default {
   .host = "127.0.0.1";
   .port = "8080";
   .first_byte_timeout = 600s;
}
```

## Verifiera HTTP-svarshuvuden

Nu kan du verifiera att Varnish serverar sidor genom att titta på [HTML](https://glossary.magento.com/html) svarshuvuden returneras från vilken sida som helst.

Innan du kan titta på rubriker måste du ange Commerce för utvecklarläge. Det finns flera sätt att göra det på. Det enklaste är att ändra `.htaccess` i Commerce-programmets rot. Du kan också använda [`magento deploy:mode:set`](../cli/set-mode.md) -kommando.

### Ange handel för utvecklarläge

Om du vill ange Commerce för utvecklarläge använder du [`magento deploy:mode:set`](../cli/set-mode.md#change-to-developer-mode) -kommando.

### Titta på varnish-loggen

Kontrollera att Varnish körs och ange sedan följande kommando på Varnish-servern:

```bash
varnishlog
```

Gå till valfri Commerce-sida i en webbläsare.

En lång lista med svarshuvuden visas i kommandotolken. Leta efter rubriker som följande:

```terminal
-   BereqHeader    X-Varnish: 3
-   VCL_call       BACKEND_FETCH
-   VCL_return     fetch
-   BackendOpen    17 default(10.249.151.10,,8080) 10.249.151.10 60914
-   Backend        17 default(10.249.151.10,,8080)
-   Timestamp      Bereq: 1440449534.261791 0.000618 0.000618
-   ReqHeader      Host: 10.249.151.10
-   ReqHeader      Connection: keep-alive
-   ReqHeader      Content-Length: 86
-   ReqHeader      Cache-Control: max-age=0
-   ReqHeader      Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
-   ReqHeader      Origin: http://10.249.151.10
```

Om rubriker som dessa gör det _not_ visa, stoppa Varnish, kontrollera `default.vcl`och försök igen.

### Titta på sidhuvuden för svar från HTML

Det finns flera sätt att se på svarshuvuden, bland annat genom att använda en webbläsare [plugin-program](https://glossary.magento.com/plug-in) eller en webbläsarkontroll.

I följande exempel används `curl`. Du kan ange det här kommandot från alla datorer som har åtkomst till Commerce-servern med HTTP.

```bash
curl -I -v --location-trusted '<your Commerce base URL>'
```

Exempel:

```bash
curl -I -v --location-trusted 'http://192.0.2.55/magento2'
```

Leta efter rubriker som följande:

```terminal
Content-Type: text/html; charset=iso-8859-1
X-Varnish: 15
Age: 0
Via: 1.1 varnish-v6
X-Magento-Cache-Debug: HIT
```
