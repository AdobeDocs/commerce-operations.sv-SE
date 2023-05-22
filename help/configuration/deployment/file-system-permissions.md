---
title: Åtkomstbehörigheter för filsystem
description: Se hur du konfigurerar ägare eller ägare av Commerce-programmets filsystem för ett utvecklings- och produktionssystem.
feature: Configuration, Roles/Permissions
exl-id: 95b27db9-5247-4f58-a9af-1590897d73db
source-git-commit: dcc283b901917e3681863370516771763ae87462
workflow-type: tm+mt
source-wordcount: '866'
ht-degree: 0%

---

# Åtkomstbehörigheter för filsystem

I det här avsnittet beskrivs hur du ställer in ägare eller ägare av Commerce-filsystemet för ett utvecklings- och produktionssystem. Innan du fortsätter bör du läsa de koncept som beskrivs i [Översikt över ägarskap och behörigheter i filsystemet](../../installation/prerequisites/file-system/overview.md).

Det här ämnet handlar om utveckling och produktion av handel. Om du installerar Commerce kan du läsa [Ange ägarskap och behörigheter för förinstallation](../../installation/prerequisites/file-system/configure-permissions.md).

De avsnitt som följer behandlar kraven för en eller två ägare av filsystem. Det innebär:

- **En användare**- Används vanligtvis av delade värdtjänstleverantörer, som gör att du bara kan komma åt en användare på servern. Den här användaren kan logga in, överföra filer med FTP och den här användaren kör även webbservern.

- **Två användare**—Vi rekommenderar två användare om du kör en egen Commerce-server: en för att överföra filer och köra kommandoradsverktyg och en separat användare för webbserverprogrammet. När det är möjligt är detta att föredra eftersom det är säkrare.

   I stället har du separata användare:

   - Webbserveranvändaren som kör Admin och storefront.

   - A _kommandoradsanvändare_, som är ett lokalt användarkonto som du kan använda för att logga in på servern. Den här användaren kör Commerce cron-jobb och kommandoradsverktyg.

## Ägande av produktionsfilsystem för delad värdtjänst (en användare)

Om du vill använda enägarsinställningarna måste du logga in på din Commerce-server som samma användare som kör webbservern. Detta är typiskt för delade värdtjänster.

Eftersom det är mindre säkert att ha en ägare av ett filsystem rekommenderar vi att du distribuerar Commerce i produktion på en privat server i stället för på delade värdtjänster, om det är möjligt.

### Konfigurera en ägare för standard- eller utvecklarläge

I standardläge eller utvecklarläge måste följande kataloger vara skrivbara av användaren:

- `vendor`
- `app/etc`
- `pub/static`
- `var`
- Andra statiska resurser
- `generated/code`
- `generated/metadata`
- `var/view_preprocessed`

Du kan ange dessa behörigheter antingen med kommandoraden eller ett filhanteringsprogram som tillhandahålls av din delade värdleverantör.

### Ställ in en ägare för produktionsläge

När du är redo att distribuera webbplatsen till produktion bör du ta bort skrivåtkomsten från filer i följande kataloger för förbättrad säkerhet:

- `vendor`
- `app/code`
- `app/etc`
- `pub/static`
- Andra statiska resurser
- `generated/code`
- `generated/metadata`
- `var/view_preprocessed`

Om du vill uppdatera komponenter, installera nya komponenter eller uppgradera Commerce måste alla föregående kataloger vara skrivskyddade.

#### Skrivskydda kodfiler och kataloger

Så här tar du bort skrivbehörigheter till filer och kataloger från webbserverns användargrupp:

1. Logga in på din Commerce-server.

1. Ändra till installationskatalogen för Commerce.

1. Byt till produktionsläge.

   ```bash
   bin/magento deploy:mode:set production
   ```

1. Ta bort skrivbehörigheter till följande kataloger.

   ```bash
   find app/code var/view_preprocessed vendor pub/static app/etc generated/code generated/metadata \( -type f -or -type d \) -exec chmod u-w {} + && chmod o-rwx app/etc/env.php
   ```

1. Gör kommandoradsverktyget körbart.

   ```bash
   chmod u+x bin/magento
   ```

#### Göra kodfiler och kataloger skrivbara

Så här gör du filer och kataloger skrivbara så att du kan uppdatera komponenter och uppgradera Commerce-programmet:

1. Logga in på din Commerce-server.
1. Ändra till installationskatalogen för Commerce.
1. Ange följande kommandon:

   ```bash
   chmod -R u+w .
   ```

### Valfritt angivet `magento_umask`

Se [Ange en mask om du vill](../../installation/next-steps/set-umask.md) i _Installationsguide_.

## Ägarskap för produktionsfilsystem för privat värdtjänst (två användare)

Om du använder en egen server (inklusive en värdleverantörs privata serverkonfiguration) finns det två användare:

- The **webbserveranvändare**, som kör Admin och storefront.

   Linux-system har vanligtvis inget gränssnitt för den här användaren. du inte kan logga in på Commerce-servern som, eller växla till, webbserveranvändaren.

- The **kommandoradsanvändare** som du loggar in på din Commerce-server som eller byter till.

   Commerce använder den här användaren för att köra CLI-kommandon och cron.

   >[!INFO]
   >
   >Kommandoradsanvändaren kallas även _ägare av filsystem_.

Eftersom de här användarna kräver åtkomst till samma filer rekommenderar vi att du skapar en [delad grupp](../../installation/prerequisites/file-system/configure-permissions.md#about-the-shared-group) som de båda tillhör. Följande procedurer förutsätter att du redan har gjort detta.

Se något av följande avsnitt:

- Två ägare av filsystem i utvecklarläge eller standardläge
- Två ägare av filsystem i produktionsläge

### Konfigurera två ägare för standard- eller utvecklarläge

Filer i följande kataloger måste vara skrivbara av båda användarna i utvecklarläge och standardläge:

- `var`
- `generated`
- `pub/static`
- `pub/media`
- `app/etc`

Ange [`setgid`](https://linuxg.net/how-to-set-the-setuid-and-setgid-bit-for-files-in-linux-and-unix/) biten i kataloger så att behörigheter alltid ärver från den överordnade katalogen.

>[!INFO]
>
>`setgid` endast tillämpas på kataloger, _not_ till filer.

Katalogerna bör dessutom vara skrivbara av webbservergruppen. Eftersom innehåll kan finnas i dessa kataloger lägger du till behörigheterna rekursivt.

#### Ange behörigheter och `setgid`

Till `setgid` och behörigheter för utvecklarläget:

1. Logga in på Commerce-servern som ägare av filsystemet eller växla till den.
1. Ange följande kommandon i den ordning som visas:

   ```bash
   cd <magento_root>
   ```

   ```bash
   find var generated pub/static pub/media app/etc -type f -exec chmod g+w {} +
   ```

   ```bash
   find var generated pub/static pub/media app/etc -type d -exec chmod g+ws {} +
   ```

### Två ägare av filsystem i produktionsläge

När du är redo att distribuera webbplatsen till produktion bör du ta bort skrivåtkomsten från filer i följande kataloger för förbättrad säkerhet:

- `vendor`
- `app/code`
- `app/etc`
- `lib`
- `pub/static`
- Andra statiska resurser
- `generated/code`
- `generated/metadata`
- `var/view_preprocessed`

#### Skrivskydda kodfiler och kataloger

Så här tar du bort skrivbara behörigheter till filer och kataloger från webbserverns användargrupp:

1. Logga in på din Commerce-server.
1. Ändra till installationskatalogen för Commerce.
1. Som ägare av filsystemet anger du följande kommando för att växla till produktionsläge:

   ```bash
   bin/magento deploy:mode:set production
   ```

1. Ange följande kommando som en användare med `root` behörighet:

   ```bash
   find app/code lib pub/static app/etc generated/code generated/metadata var/view_preprocessed \( -type d -or -type f \) -exec chmod g-w {} + && chmod o-rwx app/etc/env.php
   ```

#### Göra kodfiler och kataloger skrivbara

Så här gör du filer och kataloger skrivbara så att du kan uppdatera komponenter och uppgradera Commerce-programmet:

1. Logga in på din Commerce-server.
1. Ändra till installationskatalogen för Commerce.
1. Ange följande kommando:

   ```bash
   find app/code lib var generated vendor pub/static pub/media app/etc \( -type d -or -type f \) -exec chmod g+w {} + && chmod o+rwx app/etc/env.php
   ```
