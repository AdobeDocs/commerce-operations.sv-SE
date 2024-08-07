---
title: Förhindra cacheförgiftning
description: Lär dig hur du förhindrar att sidcachen förgiftar din Commerce-butik.
feature: Configuration, Cache, Security
exl-id: 947024dd-d59d-480d-bb6c-8e0065054bb6
source-git-commit: 56a2461edea2799a9d569bd486f995b0fe5b5947
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 0%

---

# Förhindra cacheförgiftning

I det här avsnittet beskrivs hur du förhindrar cacheförgiftning om du använder webbservern Microsoft Internet Information Server (IIS). _Cacheförgiftning_ är ett sätt att ändra cacheinnehåll så att det inkluderar olika sidor från samma plats. Du kan till exempel mata in en HTTP 404-felsida (Hittades inte) istället för en benign sida (till exempel hemsidan för butiken), vilket kan leda till en denial of service-sida (DoS). De skadliga sidans URL:er cachas av Varnish eller Redis, vilket innebär att namnet _sidcacheförgiftning_.

Den här typen av attacker kan vara svåra att upptäcka eftersom de inte leder till fel i webbserverloggar.

Lösningen gäller följande Commerce-versioner:

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

- Om `Enable_IIS_Rewrites` är `0` tas rubrikernas värden bort.
- Om `Enable_IIS_Rewrites` är inställt på `1` lämnas rubrikernas värden intakta.

>[!WARNING]
>
>Om du anger `Enable_IIS_Rewrites` som `1` får du inte tillåta att värdena för föregående rubriker ändras innan begäran når IIS-webbservern.
