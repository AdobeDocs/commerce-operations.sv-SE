---
title: Bästa tillvägagångssätt för att ändra storlek på katalogbilder
description: Lär dig hur du förhindrar prestandaförsämringar innan du lanserar Adobe Commerce webbplats.
feature: Best Practices
role: Developer
exl-id: 591b1a62-bdba-4301-858a-77620ee657a9
source-git-commit: 823498f041a6d12cfdedd6757499d62ac2aced3d
workflow-type: tm+mt
source-wordcount: '464'
ht-degree: 0%

---

# Bästa tillvägagångssätt för att ändra storlek på katalogbilder

Alla katalogbilder bör storleksändras innan en butik går till produktion. Om det inte går att ändra storlek på bilder innan produktionen tvingar det fram en storleksändring under sidinläsningen, vilket minskar webbplatshastigheten avsevärt och ökar serverbelastningen under de första dagarna till veckor efter start.

## Den långsamma vägen

Använd det förvalda CLI-kommandot för att ändra storlek på alla bilder:

```bash
bin/magento catalog:images:resize
```

Nackdelarna med detta tillvägagångssätt är bland annat:

- Processen är entrådad
- Processen ändrar storlek på bilder som redan har ändrat storlek
- Processen kan inte avbrytas, vilket kan ta dagar

## Snabba(er) vägen

Asynkron storleksändring av bilder introducerades i Adobe Commerce 2.4 och det går snabbare att ändra storlek på bilder.

1. Starta tillfälligt några extra köhanterare på alla webbservrar (dubbelt så många fysiska processorer per server):

   ```bsh
   for i in {1.."$((2 * `nproc --all`))"};do bin/magento queue:consumers:start media.storage.catalog.image.resize &;done;
   ```

1. Kontrollera att köhanterarna körs:

   ```bash
   pgrep -fl media.storage.catalog.image.resize
   ```

1. Fyll kön med alla begäranden om storleksändring av bilder:

   ```bash
   bin/magento catalog:images:resize --async
   ```

1. Avsluta processen när alla bilder har ändrat storlek:

   ```bash
   pkill -f media.storage.catalog.image.resize
   ```

## Den snabba vägen

Det finns ett annat sätt att ändra storlek på bilder med hjälp av förgrunden.

Fördelarna med detta tillvägagångssätt är bland annat:

- Processen är flertrådig
- Processen är flerserver (om du har flera webbnoder, en belastningsutjämnare och delat diskutrymme för katalogen `media/`)
- Processen hoppar över bilder som redan har ändrat storlek

Detta arbetssätt ändrar storlek på 100 000 bilder på mindre än 8 timmar, medan det tar 6 dagar att slutföra CLI-kommandot.

1. Logga in på servern.
1. Navigera till `pub/media/catalog/product` och notera en av hash-koderna (till exempel 0047d83143a5a3a4683afdf116df680).
1. Ersätt `www.example.com` med domänen för din butik i följande exempel och ersätt hash-koden med den som du angav.

>[!BEGINTABS]

>[!TAB Använt]

```bash
cd pub/
find ./media/catalog/product -path ./media/catalog/product/cache -prune -o -type f -print | sed 's~./media/catalog/product/~https://www.example.com/media/catalog/product/cache/0047d83143a5a3a4683afdf1116df680/~g' > images.txt
```

>[!TAB belägring]

Nackdelen med `siege` är att den besöker alla URL:er i tio gånger om samtidighet har angetts till 10.

```bash
siege --file=./images.txt --user-agent="image-resizer" --no-follow --no-parser --concurrent=10 --reps=once
```

>[!TAB curl]

```bash
xargs -0 -n 1 -P 10 curl -X HEAD -s -w "%{http_code} %{time_starttransfer} %{url_effective}\n" < <(tr \\n \\0 <images.txt)
```

Argumentet `-P` avgör antalet trådar.

>[!TAB bash one-line]

Den linjära för exemplet `find/curl` om du kan köra `curl` från samma dator som bilderna finns på:

```bash
find ./media/catalog/product -path ./media/catalog/product/cache -prune -o -type f -print | sed 's~./media/catalog/product/~https://www.example.com/media/catalog/product/cache/0047d83143a5a3a4683afdf1116df680/~g' | xargs -n 1 -P 10 curl -X HEAD -s -w "%{http_code} %{time_starttransfer} %{url_effective}\n"
```

Ersätt igen `www.example.com` med webbplatsens domän och ställ in `-P` på det antal trådar som servern kan hantera utan att krascha.

>[!ENDTABS]

Utdata returnerar en lista med alla produktbilder i butiken. Du kan crawla bilderna (med `siege` eller någon annan crawler) med alla servrar och processorkärnor som är tillgängliga för dig och generera cacheminnet för storleksändring med betydligt högre hastighet än andra metoder.

Om du besöker en URL för bildcache genereras alla bildstorlekar i bakgrunden om de inte finns än. Dessutom hoppas filer som redan har ändrat storlek över.

>[!NOTE]
>
>- Adobe Commerce i molninfrastrukturprojekt kan avlasta storleksändringen av produktbilder till tjänsten Snabbt. Se [Djupbildoptimering](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly-image-optimization.html?lang=sv-SE#deep-image-optimization) i _molnguiden_.
>- Om du använder fjärrlagringsmodulen kan du också försöka med att avlasta bildens storlek så att den ändras till nginx. Se [Konfigurera storleksändring av bilder för fjärrlagring](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/storage/remote-storage/remote-storage-image-resize.html?lang=sv-SE) i _Konfigurationshandboken_.
