---
title: Filägarskap och behörigheter
description: Läs om hur viktigt det är med filsystemsbehörigheter när du arbetar med lokala installationer av Adobe Commerce och Magento Open Source.
exl-id: a84784bf-afd6-4dba-9745-3fefc0ecafcb
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 0%

---

# Filägarskap och behörigheter

Det är viktigt att ha en säker installation av Adobe Commerce eller Magento Open Source i en utvecklingsmiljö för att förhindra problem som rör obehöriga personer eller processer som har åtkomst till - och kan skada - systemet. Använd följande riktlinjer för ägarskap och behörighet för filsystem för att skydda installationen.

## Ägare till filsystem

Ägaren av filsystemet är en användare som äger och har skrivbehörighet till filer i filsystemet.

Det finns två typer av ägare av filsystem:

- **Delad värdtjänst med en enskild användare**

  Med delade värdtjänstleverantörer kan du logga in på programservern som en användare. Som enskild användare kan du logga in, överföra filer med FTP och köra webbservern. Du kan välja att ställa in en [`umask`](#restrict-access-with-a-umask) ytterligare begränsa tillgången, särskilt i produktionsmiljö.

- **Privat hosting med två användare**

  Privata värdtjänster är användbara om du hanterar en programserver. Varje användare har ett särskilt ansvar:

   - The _webbserveranvändare_ kör Admin och storefront.

   - The _kommandoradsanvändare_ kör cron-jobb och kommandoradsverktyg.

  Båda användarna behöver samma behörigheter i filsystemet, så det är bäst att använda en [delad grupp](configure-permissions.md#set-ownership-and-permissions-for-two-users) och ange [`umask`](#restrict-access-with-a-umask).

### Begränsa åtkomst med en mask

Om du vill öka säkerheten, särskilt i en produktionsmiljö i ett delat värdsystem, kan du använda `umask` för att begränsa åtkomsten. A `umask`—kallas även _filsystemmask_—är en uppsättning bitar som styr hur filbehörigheterna ställs in för nyligen skapade filer.

>[!WARNING]
>
>Filsystemsäkerhet är komplicerad och viktig. Vi rekommenderar att du rådfrågar en erfaren systemadministratör eller nätverksadministratör innan du bestämmer vilken behörighetsnivå som ska anges. Vi tillhandahåller en mekanism som du kan använda, men det är ditt ansvar att skapa en behörighetsstrategi.

Adobe Commerce och Magento Open Source använder en trebitars standardmask: `002`. Subtrahera standardmasken från UNIX-standardvärdena 666 för filer och 777 för kataloger.

Exempel:

- **775 för kataloger**—Full kontroll av användaren, fullständig kontroll av gruppen och gör det möjligt för alla att gå igenom katalogen. Dessa behörigheter krävs vanligtvis av delade värdtjänstleverantörer.

- **664 för filer**- Skrivbar av användaren, skrivbar av gruppen och skrivskyddad för alla andra.

Mer information om hur du skapar en `magento_umask` -fil, se [Ange en mask](../../next-steps/set-umask.md).

## Behörigheter, ägarskap och programlägen

Vi rekommenderar olika behörigheter och ägarskap när du använder olika programlägen för Adobe Commerce och Magento Open Source:

- Standard
- Utvecklare
- Produktion

Se [Om lägen](../../../configuration/bootstrap/application-modes.md) i _Konfigurationsguide_.

Vi diskuterar ytterligare rekommendationer om behörigheter i [Åtkomstbehörigheter för filsystem](../../../configuration/deployment/file-system-permissions.md) i _Konfigurationsguide_.

>[!TIP]
>
>Innan du installerar Adobe Commerce eller Magento Open Source bör du granska [Konfigurera filägarskap och behörigheter](configure-permissions.md).
