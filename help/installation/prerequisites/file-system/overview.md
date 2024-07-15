---
title: Filägarskap och behörigheter
description: Läs om hur viktigt det är med filsystemsbehörigheter när du arbetar med lokala installationer av Adobe Commerce.
exl-id: a84784bf-afd6-4dba-9745-3fefc0ecafcb
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---

# Filägarskap och behörigheter

Det är viktigt att du har en säker Adobe Commerce-installation i en utvecklingsmiljö så att du kan förhindra att obehöriga får åtkomst till - och eventuellt skada - systemet. Använd följande riktlinjer för ägarskap och behörighet för filsystem för att skydda installationen.

## Ägare till filsystem

Ägaren av filsystemet är en användare som äger och har skrivbehörighet till filer i filsystemet.

Det finns två typer av ägare av filsystem:

- **Delad värdtjänst med en enskild användare**

  Med delade värdtjänstleverantörer kan du logga in på programservern som en användare. Som enskild användare kan du logga in, överföra filer med FTP och köra webbservern. Du kan ange en [`umask`](#restrict-access-with-a-umask) om du vill begränsa åtkomsten ytterligare, särskilt i en produktionsmiljö.

- **Privat värdtjänst med två användare**

  Privata värdtjänster är användbara om du hanterar en programserver. Varje användare har ett särskilt ansvar:

   - Webbserveranvändaren _(_ webbserver) kör Admin och storefront.

   - Kommandoradsanvändaren _kör cron-jobb och kommandoradsverktyg._

  Båda användarna kräver samma behörigheter i filsystemet, så det är bäst att använda en [delad grupp](configure-permissions.md#set-ownership-and-permissions-for-two-users) och ange en [`umask`](#restrict-access-with-a-umask).

### Begränsa åtkomst med en mask

Om du vill öka säkerheten, särskilt i en produktionsmiljö på ett delat värdsystem, kan du använda `umask` för att begränsa åtkomsten. En `umask`, som även kallas _filsystemmask_, är en uppsättning bitar som styr hur filbehörigheterna ställs in för nyligen skapade filer.

>[!WARNING]
>
>Filsystemsäkerhet är komplicerad och viktig. Vi rekommenderar att du rådfrågar en erfaren systemadministratör eller nätverksadministratör innan du bestämmer vilken behörighetsnivå som ska anges. Vi tillhandahåller en mekanism som du kan använda, men det är ditt ansvar att skapa en behörighetsstrategi.

Adobe Commerce använder en trebitars standardmask: `002`. Subtrahera standardmasken från UNIX-standardvärdena 666 för filer och 777 för kataloger.

Exempel:

- **775 för kataloger** - Full kontroll av användaren, fullständig kontroll av gruppen och gör att alla kan gå igenom katalogen. Dessa behörigheter krävs vanligtvis av delade värdtjänstleverantörer.

- **664 för filer** - Skrivbar av användaren, skrivbar av gruppen och skrivskyddad för alla andra.

Mer information om hur du skapar en `magento_umask`-fil finns i [Ange en mask](../../next-steps/set-umask.md).

## Behörigheter, ägarskap och programlägen

Vi rekommenderar olika behörigheter och ägandeskap när du använder olika Adobe Commerce-programlägen:

- Standard
- Utvecklare
- Produktion

Se [Om lägen](../../../configuration/bootstrap/application-modes.md) i _Konfigurationsguiden_.

Vi diskuterar ytterligare rekommendationer om behörigheter i [Åtkomstbehörigheter för filsystem](../../../configuration/deployment/file-system-permissions.md) i _Konfigurationsguiden_.

>[!TIP]
>
>Granska [Konfigurera filägarskap och behörigheter](configure-permissions.md) innan du installerar Adobe Commerce.
