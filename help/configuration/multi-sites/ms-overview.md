---
title: Flera webbplatser eller butiker
description: Lär dig hur du kan starta flera webbplatser eller implementera butiksvyer med olika alternativ, domäner och innehåll.
exl-id: 724d75d9-13fc-40f9-951a-69aa407adb6f
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---

# Flera webbplatser eller butiker

Med en enda instans av Adobe Commerce kan du starta flera webbplatser eller lagra vyer med olika attribut och innehåll, som:

- Standardspråk
- Domännamn
- Kategorier
- Produkter
- Valutor

Denna flexibla lösning gör att en Commerce-kodbas och administratör kan administrera och visa olika butiker. Du konfigurerar webbplatser, butiker och butiksvyer i Admin. Använd vissa variabler i virtuella värdar för att starta Commerce-programmet med dessa webbplatser eller butiksvyer.

Ett vanligt användningsområde är att konfigurera butiker med olika alternativ i olika domäner. Du kan till exempel ha en uppsättning kategorier och produkter på en domän och en annan uppsättning kategorier och produkter på en separat domän på ett annat språk.

Du konfigurerar webbplatser, butiker och butiksvyer i Commerce Admin. Använd `MAGE_RUN_TYPE` och `MAGE_RUN_CODE` variabler i virtuella värdar för att starta Commerce-programmet med dessa webbplatser eller butiksvyer.

Tänk på följande termer:

- **Webbplats**—är den översta behållaren för webbplatser, leveransmetoder, betalningsmetoder med mera. Om du vill skapa helt separata sajter som inte delar varukorg, leveransmetoder eller andra måste du skapa separata webbplatser.

  Kundkonton på webbplatser kan delas mellan flera webbplatser i en enda Commerce-instans. En webbplats innehåller minst en butik. Katalogpriserna bör hanteras på webbplatsnivå.

- **Butik**—finns på en webbplats. I sin tur innehåller en butik minst en *butiksvy*.

  Flera butiker kan dela kundvagn, användarsessioner, betalningsgateways med mera, men de har separata katalogstrukturer och katalogpris.

  Katalogkvantitet (lager) kan inte hanteras på butiksnivå. Lager hanteras endast på webbplats- eller global nivå.

  Vyerna i butiken förändrar hur sidorna presenteras och används vanligtvis för att visa en butik med olika layouter eller språk. Du kan hantera olika valutor per butiksvy.

  Varje webbplats och varje butiksvy måste ha en unik identifierare. Den här identifieraren krävs för att använda `MAGE_RUN_TYPE` och `MAGE_RUN_CODE` variabler enligt följande:

- `MAGE_RUN_TYPE` kan vara antingen `store` eller `website`

   - Använd `website` för att läsa in en webbplats i din butik.
   - Använd `store` för att läsa in alla butiksvyer i butiken.

- `MAGE_RUN_CODE` är den unika kod för webbplats- eller butiksvyn som motsvarar `MAGE_RUN_TYPE`

Här följer en sammanfattning av de uppgifter du måste utföra:

1. [Konfigurera webbplatser, butiker och butiksvyer i administratören.](ms-admin.md)
1. Skapa en virtuell värd för att läsa in många webbplatser eller en virtuell värd per Commerce-webbplats eller butiksvy för att tillåta specifika direktiv för varje butik.
1. Skicka värdena för `MAGE_RUN_TYPE` och `MAGE_RUN_CODE` till webbservern.
