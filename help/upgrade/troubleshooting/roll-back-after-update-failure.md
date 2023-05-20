---
title: Återställning efter moduluppdateringsfel
description: Felsök uppgraderingen av Adobe Commerce eller Magento Open Source efter att ha påträffat ett uppdateringsfel för modulen.
exl-id: 1537a6b1-b450-4f90-bffb-73359fa71598
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '93'
ht-degree: 0%

---

# Återställning efter moduluppdateringsfel

Om moduluppdateringen misslyckas visas meddelanden som liknar följande i konsolloggen:

```terminal
[2015-08-14 12:12:02 CDT] Job "update {"components":[{"name":"example/module","version":"1.1.0"}]}" has been started
[2015-08-14 12:12:02 CDT] Starting composer update...
[2015-08-14 12:12:02 CDT] An error occurred while executing job "update {"components":
[{"name":"example/module","version":"1.1.0"}]}": Could not complete update {"components":
[{"name":"example/module","version":"1.1.0"}]} successfully: Cannot find component to update
```

I föregående exempel finns det ingen komponentversion att återställa till. Kontakta komponentleverantören eller försök lösa problemet själv.

Under tiden kan du gå tillbaka till en tidigare version genom att klicka på **Återställning**, som återställer dina data även om du inte har säkerhetskopierat tidigare.
