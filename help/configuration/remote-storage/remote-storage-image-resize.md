---
title: Konfigurera storleksändring av bilder för fjärrlagring
description: Optimera diskresurserna genom att konfigurera storleksändring av bilder på serversidan.
feature: Configuration, Storage
exl-id: 51c2b9b3-0f5f-4868-9191-911d5df341ec
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 1%

---

# Konfigurera storleksändring av bilder för fjärrlagring

Som standard har Adobe Commerce stöd för storleksändring av bilder på programsidan. Genom att aktivera modulen Fjärrlagring kan du emellertid använda Nginx för att avlasta en bild som ändrar storlek till serversidan, där du kan spara diskresurser och optimera diskanvändningen.

I följande diagram visas hur Nginx hämtar, ändrar storlek på och lagrar bilder i cachen. Storleksändringen bestäms av de parametrar som finns i URL-adressen, till exempel höjd och bredd.

![ändra storlek på bild](../../assets/configuration/remote-storage-nginx-image-resize.png)

>[!TIP]
>
>Information om Adobe Commerce i molninfrastrukturprojekt finns i [Konfigurera fjärrlagring för Commerce i molninfrastrukturen](cloud-support.md)

## Konfigurera URL-format i Adobe Commerce

Om du vill ändra storlek på bilder på serversidan måste du konfigurera Adobe Commerce så att det innehåller argument för bildens höjd, bredd och plats (URL).

**Så här konfigurerar du Commerce för storleksändring av serversidesbild**:

1. Klicka på _>_ > **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** på panelen **[!UICONTROL General]** Admin **[!UICONTROL Web]**.

1. Expandera **[!UICONTROL Url options]** i den högra rutan.

1. I avsnittet _URL-format för katalogmedia_ rensar du **[!UICONTROL Use system value]**.

1. Markera URL:en `Image optimization based on query parameters` i fältet **_URL-format för katalogmedia_**.

1. Klicka på **[!UICONTROL Save Config]**.

1. Fortsätt till [Nginx-konfigurationen](#configure-nginx).

## Konfigurera Nginx

Om du vill fortsätta att konfigurera storleksändring av bilder på serversidan måste du förbereda filen `nginx.conf` och ange ett `proxy_pass`-värde för det valda kortet.

**Så här aktiverar du Nginx för att ändra storlek på bilder**:

1. Installera [Nginx-bildfiltermodulen][nginx-module].

   ```shell
   load_module /etc/nginx/modules/ngx_http_image_filter_module.so;
   ```

1. Skapa en `nginx.conf`-fil baserat på den inkluderade mallfilen `nginx.conf.sample`. Exempel:

   ```conf
   location ~* \.(jpg|jpeg|png|gif|webp)$ {
       set $width "-";
       set $height "-";
       if ($arg_width != '') {
           set $width $arg_width;
       }
       if ($arg_height != '') {
           set $height $arg_height;
       }
       image_filter resize $width $height;
       image_filter_jpeg_quality 90;
   }
   ```

1. [_Valfritt_] Konfigurera ett `proxy_pass`-värde för ditt specifika kort.

   - [Amazon Simple Storage Service (Amazon S3)](remote-storage-aws-s3.md)

<!-- link definitions -->

[nginx-module]: https://nginx.org/en/docs/http/ngx_http_image_filter_module.html
