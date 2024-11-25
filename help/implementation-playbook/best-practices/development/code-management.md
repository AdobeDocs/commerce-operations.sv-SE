---
title: Bästa praxis för kodhantering
description: Läs om de effektivaste strategierna för kodhantering i utvecklingsfasen av Adobe Commerce-projekt.
feature: Best Practices
role: Developer
exl-id: 0bff4c7a-1082-4b3e-b19c-bc8ad529b131
source-git-commit: ee7551374aa6d4ad462dd64ee3d05b934b43ce45
workflow-type: tm+mt
source-wordcount: '659'
ht-degree: 0%

---

# De bästa sätten att hantera kod för Adobe Commerce

Det här avsnittet är utformat för att hjälpa dig att avgöra om du ska använda Git eller Composer för att distribuera anpassad kod, med hänsyn till versionshantering, kodkomplexitet och beroendehantering.

>[!NOTE]
>
>Dessa bästa metoder är lämpligast för migreringar och implementeringar, och mindre bra för utveckling av en enda modul.

## Berörda produkter och versioner

[Alla versioner som stöds](../../../release/versions.md) av:

- Adobe Commerce i molninfrastruktur
- Adobe Commerce lokalt

## Definitioner

{{$include /help/_includes/gra-definitions.md}}

## Använd Git eller Composer

<table>
<thead>
  <tr>
    <th></th>
    <th>Kod som huvudsakligen hanteras via Git</th>
    <th>Kod som huvudsakligen hanteras via Composer</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>När används för en inställning med en instans</td>
    <td>
      <ul>
        <li><strong>Standardmetod för att hantera kod för en enskild instansinställning</strong></li>
        <li>När kodbasen inte kommer att ingå i ett GRA-avtal för flera varumärken i framtiden</li>
        <li>När alla varumärken körs på en enda instans som webbplatser</li>
      </ul>
    </td>
    <td>
      <ul>
        <li>När kodbasen kan eller kommer att ingå i en flerinstanskonfiguration i framtiden</li>
      </ul>
    </td>
  </tr>
  <tr>
    <td>När används för en flerinstansinställning</td>
    <td>
      <ul>
        <li>När nästan alla moduler är sammanlänkade (rekommenderas inte)</li>
        <li>När koden underhålls av ett team som inte är bekant med Composer</li>
      </ul>
    </td>
    <td>
      <ul>
        <li><strong>Standardmetod för att hantera kod för en konfiguration med flera instanser</strong></li>
        <li>När Adobe underhåller kodbasen eller så är gruppen som underhåller Composer bekant med den</li>
      </ul>
    </td>
  </tr>
</tbody>
</table>

## Funktionsmatris

| Funktion | Git | Disposition |
|------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------|
| Huvudkodarkiv | All kod finns i en enda eller några Git-databaser | All kod finns i paketen i en Composer-databas<br>Varje Composer-paket representeras av en Git-databas |
| Kodplats | Utveckling sker i katalogen `app/` | Utveckling sker i katalogen `vendor/` |
| Core upgrade management | Adobe Commerce Core installeras och uppgraderas med Composer och resultatet implementeras i Git | Adobe Commerce Core installeras och uppgraderas med Composer; resultatet implementeras i Git |
| Modulhantering från tredje part | Tredjepartsmoduler installeras i `vendor/` om de installeras via Marketplace eller packagist.org. Annars installeras de i `app/` | Alla tredjepartsmoduler är installerade i katalogen `vendor/` |
| Utgåvor | Frisläppningen kännetecknas av kommandona `git merge` och `git pull` eller `git checkout` | Frisläppningen kännetecknas av kommandona `composer update` och `git pull` eller `git checkout` |
| Antal Git-databaser | Få | Många |
| Utvecklingskomplexitet | Enkel | Komplex |
| Komplexitet för pull-begäran | Enkel | Komplex |
| Komplexitet för kodgranskning | Enkel | Enkel |
| Dev/QA/UAT-miljö - uppdaterar komplexitet | Enkel | Komplex |
| GRA-stöd | ![Ja, ikon](../../../assets/yes.svg) | ![Ja, ikon](../../../assets/yes.svg) |
| Moduler kan installera externa bibliotek automatiskt | ![Ingen ikon](../../../assets/no.svg) | ![Ja, ikon](../../../assets/yes.svg) |
| Flexibilitet i GRA-sammansättning | ![Ingen ikon](../../../assets/no.svg) | ![Ja, ikon](../../../assets/yes.svg) |
| Modulberoendehantering | ![Ja, ikon](../../../assets/yes.svg) Endast via `module.xml`, begränsad funktionalitet | ![Ja, ikon](../../../assets/yes.svg) Fullständig beroendehantering via `composer.json` |
| Modulversionshantering | ![Ja, ikon](../../../assets/yes.svg) Du kan definiera en version, men du kan inte installera en viss version | ![Ja, ikon](../../../assets/yes.svg) Stöd för fullversion |
| Betalda tjänster krävs | Git-databas | Git-arkiv, privat Packagist (± 600 euro per år) |
| Bitbucket-integrering med Jira möjlig | ![Ja, ikon](../../../assets/yes.svg) | ![Ja, ikon](../../../assets/yes.svg) |
| Kodändringar som är direkt tillgängliga för installation | ![Ja, ikon](../../../assets/yes.svg) | ![Ja, ikon](../../../assets/yes.svg) |

## Lösningar att undvika

1. **Kombinera disposition och `app/code` för dina moduler**

   Resultatet blir att alla nackdelar med båda kodhanteringsformaten kombineras i ditt projekt. Det ger onödig komplexitet, instabilitet och bristande flexibilitet.

   Exempel:
   - Förklara både Git- och Composer-arbetsflöden (i stället för bara ett av dem) för utvecklingsteamet.
   - Installera inkompatibla moduler i `app/code` eftersom det inte finns något som kan stoppa det.
   - Det är besvärligt att flytta en modul från `app/code` till Composer (eller omvänt), särskilt med pågående utveckling.

1. **Satis Package Manager**

   Privata paketeringskostnader ± 600 euro per år. Kostnaden är för hela GRA kombinerat, inte per varumärke. Undvik inte dessa kostnader genom att använda den kostnadsfria lösningen Satis. Satis uppdaterar inte automatiskt dina paket när du push-implementerar för att Git. Satis har inte heller någon inbyggd behörighet. Du måste ha en webbserver för att köra Satis. Det innebär att ni måste betala en stor mängd av den privata Packagistens prenumerationsavgift för att underhålla Satis.

1. **Börja med Git och gå sedan till Composer**

   Välj en metod för kodhantering i början av projektet. Att byta från Git till Composer eller tvärtom, med pågående utveckling är besvärligt och kan leda till kodförlust och eller förlust av revisionshistorik.
