---
title: Konfigurera storleksändring av bilder för fjärrlagring
description: Optimera diskresurserna genom att konfigurera storleksändring av bilder på serversidan.
source-git-commit: 96fe0c5eeaa029347c829c39547ee5e473c8d04d
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 1%

---

# Konfigurera storleksändring av bilder för fjärrlagring

Som standard [!DNL Commerce] har stöd för att ändra storlek på bilder på programsidan. Genom att aktivera modulen Fjärrlagring kan du emellertid använda Nginx för att avlasta en bild som ändrar storlek till serversidan, där du kan spara diskresurser och optimera diskanvändningen.

I följande diagram visas hur Nginx hämtar, ändrar storlek på och lagrar bilder i cachen. Storleksändringen bestäms av de parametrar som finns i URL-adressen, till exempel höjd och bredd.

![bildstorlek](../../assets/configuration/remote-storage-nginx-image-resize.png)

## Konfigurera URL-format i [!DNL Commerce]

Om du vill ändra storlek på bilder på serversidan måste du konfigurera Commerce så att den innehåller argument för bildens höjd, bredd och plats (URL).

**Så här konfigurerar du Commerce för storleksändring av serverbilder**:

1. I _Administratör_ panel, klicka **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Web]**.

1. Expandera i den högra rutan **[!UICONTROL Url options]**.

1. I _URL-format för katalogmedia_ sektion, klar **[!UICONTROL Use system value]**.

1. Välj `Image optimization based on query parameters` URL i **_URL-format för katalogmedia_** fält.

1. Klicka på **[!UICONTROL Save Config]**.

1. Fortsätt till [Nginx-konfiguration](#configure-nginx).

## Konfigurera Nginx

Om du vill fortsätta att konfigurera storleksändring av bilder på serversidan måste du förbereda `nginx.conf` och ange `proxy_pass` värdet för det valda kortet.

**Aktivera Nginx för att ändra storlek på bilder**:

1. Installera [Modul för Nginx-bildfilter][nginx-module].

   ```shell
   load_module /etc/nginx/modules/ngx_http_image_filter_module.so;
   ```

1. Skapa en `nginx.conf` fil baserad på den inkluderade mallen `nginx.conf.sample` -fil. Exempel:

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

1. [_Valfritt_] Konfigurera en `proxy_pass` värdet för ditt specifika kort.

   - [Amazon Simple Storage Service (Amazon S3)](remote-storage-aws-s3.md)

<!-- link definitions -->

[nginx-module]: https://nginx.org/en/docs/http/ngx_http_image_filter_module.html
