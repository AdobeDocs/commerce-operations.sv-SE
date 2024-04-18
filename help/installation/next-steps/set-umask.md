---
title: Ange en mask (valfritt)
description: Förbättra säkerhetspositionen för din Adobe Commerce-installation lokalt genom att begränsa filsystemsbehörigheter.
feature: Install, Configuration
exl-id: 18d65d75-7be0-4488-bf35-4b058e4ae5ea
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 0%

---

# Ange en mask (valfritt)

Webbservergruppen måste ha skrivbehörighet till vissa kataloger i filsystemet, men du kanske vill ha bättre säkerhet, särskilt i produktionen. Vi ger dig flexibilitet att ytterligare begränsa dessa behörigheter med en [umask](https://www.cyberciti.biz/tips/understanding-linux-unix-umask-value-usage.html).

Vår lösning är att göra det möjligt att skapa en fil med namnet `magento_umask` i programmets rotkatalog som begränsar behörigheterna för webbservergruppen och alla andra.

>[!NOTE]
>
>Vi rekommenderar att du endast ändrar mask för ett enanvändar- eller delat värdsystem. Om du har en privat programserver måste gruppen ha skrivåtkomst till filsystemet. Tumpen tar bort skrivåtkomst från gruppen.

Standardmask (utan `magento_umask` anges) är `002`, vilket betyder

* 775 för kataloger, vilket innebär fullständig kontroll för användaren, fullständig kontroll för gruppen och gör att alla kan gå igenom katalogen. Dessa behörigheter krävs vanligtvis av delade värdtjänstleverantörer.

* 664 för filer, vilket betyder skrivbar av användaren, skrivbar av gruppen och skrivskyddad för alla andra

Ett vanligt förslag är att använda värdet `022` i `magento_umask` fil, vilket betyder:

* 755 för kataloger: fullständig kontroll för användaren, och alla andra kan gå igenom kataloger.
* 644 för filer: läs- och skrivbehörighet för användaren och skrivskyddad för alla andra.

Till `magento_umask`:

1. I en kommandoradsterminal loggar du in på programservern som en [ägare av filsystem](../prerequisites/file-system/overview.md).
1. Navigera till installationskatalogen för programmet:

   ```bash
   cd <Application install directory>
   ```

1. Använd följande kommando för att skapa en fil med namnet `magento_umask` och skriva `umask` värdesätta för den.

   ```bash
   echo <desired umask number> > magento_umask
   ```

   Nu bör du ha en fil med namnet `magento_umask` i `<Magento install dir>` med det enda innehållet som `umask` tal.

1. Logga ut och logga in igen som [ägare av filsystem](../prerequisites/file-system/overview.md) för att tillämpa ändringarna.
