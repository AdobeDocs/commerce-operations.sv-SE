---
title: Förhindra cacheförgiftning
description: Lär dig hur du förhindrar att sidcachen förgiftas för din Commerce Store.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 0%

---


# Förhindra cacheförgiftning

I det här avsnittet beskrivs hur du förhindrar cacheförgiftning om du använder webbservern Microsoft Internet Information Server (IIS). _Cacheförgiftning_ är ett sätt att ändra cacheinnehåll så att det inkluderar olika sidor från samma plats. Du kan till exempel mata in en HTTP 404-felsida (Hittades inte) istället för en benign sida (till exempel hemsidan för butiken), vilket kan leda till en denial of service-sida (DoS). De skadliga sidans URL:er cachas av Varnish eller Redis, därav namnet _sidcacheförgiftning_.

Den här typen av attacker kan vara svåra att upptäcka eftersom de inte leder till fel i webbserverloggar.

Den här lösningen gäller följande versioner av Commerce:

- 2.0.10 och senare
- 2.1.2 och senare

>[!INFO]
>
>Det här avsnittet är avsett för erfarna IIS-administratörer.

## Beskrivning

Problemet uppstår om URL-omskrivningar är aktiverade på IIS-servern och något av följande HTTP-huvuden ändras innan begäran når cachelagringstjänsten Varnish eller Redis:

- `X-Rewrite-Url`
- `X-Original-Url`
- `IIS-wasurlrewritten`
- `Unencoded-URL`
- `Orig-path-info`

Om dessa rubriker ändras cachelagras den resulterande URL:en och innehållet, vilket kan göra dem sårbara.

## Lösning

Vi erbjuder alternativet att ta bort värdena för alla föregående rubriker baserat på IIS-serverinställningen för `Enable_IIS_Rewrites`.

- If `Enable_IIS_Rewrites` är inställd på `0`tas rubrikernas värden bort.
- If `Enable_IIS_Rewrites` är inställd på `1`ändras inte rubrikernas värden.

>[!WARNING]
>
>Om du anger `Enable_IIS_Rewrites` till `1`får du inte tillåta att värdena för föregående rubriker ändras innan begäran når IIS-webbservern.
