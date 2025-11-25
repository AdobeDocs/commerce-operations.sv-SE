---
title: Skaffa Adobe Commerce
description: Lär dig hur du laddar ned Adobe Commerce.
exl-id: 7a769d5b-5397-4572-8db5-7602068e6aad
source-git-commit: 84a20012a81278cc95587ec14281b05330261687
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# Skaffa Adobe Commerce

Du är bland de 240 000 handlare världen över som litar på vår e-handelsprogramvara. Vi har samlat in information som hjälper dig att komma igång med installationen.

## Så här skaffar du programmet

Kontrollera tillgängligheten och kompatibiliteten för tillägg som skapats av Adobe och Commerce Services för Adobe Commerce och Magento Open Source på [produkttillgänglighetssidan](https://experienceleague.adobe.com/sv/docs/commerce-operations/release/product-availability).

>[!NOTE]
>
>Adobe Commerce-kodebaser distribueras nu exklusivt via Composer på grund av policyändringar. Använd Composer för att hämta någon av de listade Adobe Commerce-versionerna eftersom kodbasen inte längre är tillgänglig i hämtningsavsnittet.
>
>Mer information finns i [Kan inte komma åt faktureringsutdrag och hämta kodbas på Adobe Commerce i molninfrastruktur](https://experienceleague.adobe.com/sv/docs/experience-cloud-kcs/kbarticles/ka-26611)

Se följande tabell för att komma igång med installationen av Adobe Commerce.

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
        <td><ol><li>Skapar ett <em>projekt</em> i Composer som innehåller listan med komponenter som ska användas.</li>
            <li>Använder Composer för att uppdatera paketberoenden. <code>composer create-project</code> används för att hämta Composer-metapaketet.</li>
            <li>Installerar programmet med kommandoraden <a href="../advanced.md"></a>.</li>
        <li>Uppgraderar programmet och tilläggen med kommandoraden <a href="../../upgrade/implementation/perform-upgrade.md"></a>.</li></ol></td>
        <td><p><a href="../composer.md">Hämta metapackage</a></p></td>
    </tr>
    <tr>
        <td><p>Medverkande utvecklare</p></td>
        <td><p>Bidrar till Magento Open Source-kodbas, sparar filer och anpassar programmet. Mycket tekniskt, har en egen utvecklingsserver, förstår Composer och GitHub.</p>
            <p>Du <em>kan inte</em> använda programmet i en produktionsmiljö.</p>
      <p>Du måste uppgradera med kommandona <a href="../../upgrade/developer/git-installs.md">Composer och Git</a>.</p></td>
        <td><ol><li>Klonar GitHub-databasen.</li>
            <li>Använder Composer för att uppdatera paketberoenden.</li>
            <li>Installerar programmet med <a href="../advanced.md">kommandorad</a>.</li>
            <li>Uppgraderar programmet med kommandona <a href="../../upgrade/developer/git-installs.md">Composer och Git</a>.</li>
            <li>Anpassar kod i katalogen <code>app/code</code>.</li></ol></td>
        <td><p><a href="https://developer.adobe.com/commerce/contributor/guides/install/clone-repository">Klona GitHub-databasen</a></p></td>
    </tr>
    </tbody>
</table>

## Användbar information

Använd länkarna till vänster på sidan för att navigera i avsnitten i varje del av installationen.

## Nödvändiga serverbehörigheter

UNIX-system kräver `root` behörigheter för att installera och konfigurera programvara som en webbserver, PHP. Om du behöver installera den här programvaran måste du ha `root`-åtkomst.

Installera *inte* programmet i webbserverns dokumentrot som `root`-användare eftersom webbservern kanske inte kan interagera med de filerna.

Du behöver `root` behörigheter för att skapa [filsystemsägaren](file-system/overview.md) och lägga till den ägaren i webbservergruppen. Du använder filsystemets ägare för att köra `bin/magento`-kommandon från kommandoraden och för att konfigurera cron-jobb, som schemalägger aktiviteter åt dig.
