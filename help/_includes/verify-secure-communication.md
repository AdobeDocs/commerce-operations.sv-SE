---
source-git-commit: 4c18f00e0b92e49924676274c4ed462a175a7e4b
workflow-type: tm+mt
source-wordcount: '146'
ht-degree: 1%

---
# Verifiera att kommunikationen är säker

I det här avsnittet beskrivs två sätt att verifiera att grundläggande HTTP-autentisering fungerar:

* Använda `curl` för att verifiera att du måste ange ett användarnamn och lösenord för att få klusterstatus
* Konfigurera grundläggande HTTP-autentisering i administratören

## Använd en `curl` kommando för att verifiera klusterstatus

Ange följande kommando:

```bash
curl -i http://<hostname, ip, or localhost>:<proxy port>/_cluster/health
```

Om du till exempel anger kommandot på sökmotorservern och proxyn använder port 8080:

```bash
curl -i http://localhost:8080/_cluster/health
```

Följande meddelande visas för att ange att autentiseringen misslyckades:

```terminal
HTTP/1.1 401 Unauthorized
Date: Tue, 23 Feb 2016 20:35:29 GMT
Content-Type: text/html
Content-Length: 194
Connection: keep-alive
WWW-Authenticate: Basic realm="Restricted"
<html>
<head><title>401 Authorization Required</title></head>
<body bgcolor="white">
  <center><h1>401 Authorization Required</h1></center>
</body>
</html>
```

Prova följande kommando:

```bash
curl -i -u <username>:<password> http://<hostname, ip, or localhost>:<proxy port>/_cluster/health
```

Exempel:

```bash
curl -i -u magento_elasticsearch:mypassword http://localhost:8080/_cluster/health
```

Den här gången lyckas kommandot med ett meddelande som liknar följande:

```terminal
HTTP/1.1 200 OK
Date: Tue, 23 Feb 2016 20:38:03 GMT
Content-Type: application/json; charset=UTF-8
Content-Length: 389
Connection: keep-alive
{"cluster_name":"elasticsearch","status":"yellow","timed_out":false,"number_of_nodes":1,"number_of_data_nodes":1,"active_primary_shards":5,"active_shards":5,"relocating_shards":0,"initializing_shards":0,"unassigned_shards":5,"delayed_unassigned_shards":0,"number_of_pending_tasks":0,"number_of_in_flight_fetch":0,"task_max_waiting_in_queue_millis":0,"active_shards_percent_as_number":50.0}
```

## Konfigurera grundläggande HTTP-autentisering i administratören

Utför samma uppgifter som beskrivs i [Sökmotorkonfiguration](../configuration/search/configure-search-engine.md) *utom* klicka **[!UICONTROL Yes]** från **[!UICONTROL Enable HTTP Auth]** och ange ditt användarnamn och lösenord i fälten.

Klicka **[!UICONTROL Test Connection]** för att vara säker på att det fungerar och klicka sedan på **[!UICONTROL Save Config]**.

Du måste tömma cachen och indexera om innan du fortsätter.
