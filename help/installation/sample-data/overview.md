---
title: Översikt över exempeldata
description: Lär dig hur du använder exempeldata för Adobe Commerce- och Magento Open Source-projekt.
source-git-commit: 8f05fb6fc212c2b3fda80457bbf27ecf16fb1194
workflow-type: tm+mt
source-wordcount: '205'
ht-degree: 0%

---


# Översikt över exempeldata

Exempeldata ger en butiksbild baserad på Luma-temat som är utrustat med produkter, kategorier, kundregistrering osv. Det fungerar precis som en Commerce Store och du kan ändra priser, lager och kampanjpriser med hjälp av Admin.

Du kan installera exempeldata antingen före eller efter installationen av Commerce-programmet. När du är klar med exempeldata kan du antingen ta bort den eller installera den på nytt enligt beskrivningen i [Ta bort exempeldatamoduler eller uppdatera exempeldata](remove-or-update.md).

>[!WARNING]
>
>Du kan inte avinstallera exempeldata. Vi rekommenderar att du endast använder exempeldata för att lära dig mer om hur Adobe Commerce och Magento Open Source fungerar. Undvik all utveckling i ett system där du har installerat exempeldata.

Du kan installera valfria exempeldata på något av följande sätt:

| Installationsmetod | Beskrivning | Nödvändig kompetensnivå |
|--- |--- |--- |
| Använda Composer | [Kör `magento sampledata:deploy` för att ändra programmets rot `composer.json`](composer-packages.md) för att aktivera exempeldatamoduler. | Kräver kunskap om och åtkomst till Commerce-filsystemet. |
| Klona databaser | [Klona GitHub-databasen](git-repositories.md) och exempeldatabasen, och sedan länka samman dem. | Endast för medverkande utvecklare. Alla andra bör använda någon av de föregående metoderna. |
