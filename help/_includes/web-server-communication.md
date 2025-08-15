---
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 0%

---
# Säker webbserverkommunikation

I det här avsnittet beskrivs ett exempel på hur du säkrar kommunikationen mellan webbservern och sökmotorn (Elasticsearch eller OpenSearch) med en kombination av TLS-kryptering (Transport Layer Security) och [grundläggande HTTP-autentisering](https://datatracker.ietf.org/doc/html/rfc2617). Du kan även konfigurera andra typer av autentisering. Vi tillhandahåller referenser för den informationen.

(En äldre term, Secure Sockets Layer (SSL), används ofta som synonymer med TLS. I det här avsnittet hänvisar vi till *TLS*.)

>[!WARNING]
>
>Om inget annat anges måste alla kommandon i det här avsnittet anges som en användare med `root`-behörighet.

## Rekommendationer

Vi rekommenderar följande:

* Din webbserver använder TLS.

  TLS ligger utanför det här ämnesområdet, men vi rekommenderar starkt att du använder ett riktigt certifikat i produktionen och inte ett självsignerat certifikat.

* Sökmotorn körs på samma värd som en webbserver. Det här avsnittet gäller inte för körning av sökmotorn och webbservern på olika värdar.

  Fördelen med att lägga sökmotorn och webbservern på samma värd är att det inte går att fånga upp krypterad kommunikation. Sökmotorns webbserver behöver inte vara samma som Adobe Commerce webbserver. Adobe Commerce kan till exempel köra Apache och Elasticsearch/OpenSearch kan köra nginx.

  Om sökmotorn exponeras för den offentliga webben bör du konfigurera autentiseringen. Om sökmotorinstansen är skyddad i nätverket behöver du inte göra det. Samarbeta med din värdleverantör för att ta reda på vilka säkerhetsåtgärder du bör vidta för att skydda din instans.

## Mer information om TLS

Se någon av följande resurser:

* Apache

   * [Apache 2.4 - instruktiv kryptering](https://httpd.apache.org/docs/2.4/ssl/ssl_howto.html)
   * [Så här skapar du ett SSL-certifikat i Apache för Ubuntu 14.04 (självstudiekurs om digitaloceanen)](https://www.digitalocean.com/community/tutorials/how-to-create-a-ssl-certificate-on-apache-for-ubuntu-14-04)
   * [Konfigurera en SSL-skyddad webbserver med CentOS (CentOS wiki)](https://wiki.centos.org/HowTos/Https)

* Nginx

   * [Nginx SSL-avslutning](https://www.nginx.com/resources/admin-guide/nginx-ssl-termination/)
   * [Så här skapar du ett SSL-certifikat på Nginx för Ubuntu 14.04 (självstudiekurs om digitaloceanen)](https://www.digitalocean.com/community/tutorials/how-to-create-an-ssl-certificate-on-nginx-for-ubuntu-14-04)
   * [Installation av Nginx SSL-certifikat (digicert)](https://www.digicert.com/ssl-certificate-installation-nginx.htm)
