---
title: Skaffa Adobe Commerce
description: Lär dig hur du laddar ned Adobe Commerce och Magento Open Source.
exl-id: 7a769d5b-5397-4572-8db5-7602068e6aad
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# Skaffa Adobe Commerce

Du är bland de 240 000 handlare världen över som litar på vår e-handelsprogramvara. Vi har samlat in information som hjälper dig att komma igång med installationen.

## Så här skaffar du programmet

Kolla om det finns nya spännande funktioner och releaser och se hur du kan få dem via [produkttillgänglighetssida](https://devdocs.magento.com/release/availability.html).

Se följande tabell för att komma igång med att installera Adobe Commerce eller Magento Open Source.

<table>
    <tbody>
        <tr>
            <th>Användarbehov</th>
            <th>Beskrivning</th>
            <th>Installations- och uppgraderingssteg på hög nivå</th>
            <th>Länken Kom igång</th>
        </tr>
    <tr>
        <td><p>Integrator, paketerare</p></td>
        <td><p>Om du vill ha fullständig kontroll över alla installerade komponenter har åtkomst till programservern, mycket teknisk, kan paketera om Magento Open Source med andra komponenter.</p>
        </td>
        <td><ol><li>Skapar en disposition <em>projekt</em> som innehåller en lista med komponenter som ska användas.</li>
            <li>Använder Composer för att uppdatera paketberoenden; använder <code>composer create-project</code> för att hämta Composer-metapaketet.</li>
            <li>Installerar programmet med <a href="../advanced.md">kommandorad</a>.</li>
        <li>Uppgraderar programmet och tilläggen med  <a href="../../upgrade/implementation/perform-upgrade.md">kommandorad</a>.</li></ol></td>
        <td><p><a href="../composer.md">Hämta metapackage</a></p></td>
    </tr>
    <tr>
        <td><p>Bidrar utvecklare</p></td>
        <td><p>Bidrar till kodbasen Magento Open Source, filer buggar och anpassar programmet. Mycket tekniskt, har en egen utvecklingsserver, förstår Composer och GitHub.</p>
            <p>Du <em>inte</em> använda programmet i en produktionsmiljö.</p>
      <p>Du måste uppgradera med <a href="../../upgrade/developer/git-installs.md">Kommandona Composer och Git</a>.</p></td>
        <td><ol><li>Klonar GitHub-databasen.</li>
            <li>Använder Composer för att uppdatera paketberoenden.</li>
            <li>Installerar programmet med <a href="../advanced.md">kommandorad</a>.</li>
            <li>Uppgraderar programmet med <a href="../../upgrade/developer/git-installs.md">Kommandona Composer och Git</a>.</li>
            <li>Anpassar kod under <code>app/code</code> katalog.</li></ol></td>
        <td><p><a href="https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/">Klona GitHub-databasen</a></p></td>
    </tr>
    </tbody>
</table>

## Användbar information

Använd länkarna till vänster på sidan för att navigera i avsnitten i varje del av installationen.

## Nödvändiga serverbehörigheter

UNIX-system kräver `root` behörighet att installera och konfigurera programvara som en webbserver, PHP. Om du behöver installera den här programvaran måste du `root` åtkomst.

Gör *not* installera programmet i webbserverns dokument som `root` eftersom webbservern kanske inte kan interagera med dessa filer.

Du behöver `root` behörighet att skapa [ägare av filsystem](file-system/overview.md) och lägg till den ägaren i webbservergruppen. Du använder filsystemets ägare för att köra `bin/magento` kommandon från kommandoraden och för att ställa in cron-jobb, som schemalägger uppgifter åt dig.
