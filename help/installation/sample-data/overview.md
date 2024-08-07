---
title: Översikt över exempeldata
description: Lär dig hur du använder exempeldata för Adobe Commerce-projekt.
exl-id: 828b009d-a6ff-4db2-aa1a-838f6f55a194
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '243'
ht-degree: 0%

---

# Översikt över exempeldata

Exempeldata ger en butiksbild baserad på Luma-temat som är utrustat med produkter, kategorier, kundregistrering osv. Det fungerar precis som en Commerce-butik och du kan ändra priser, lager och kampanjpriser med hjälp av Admin.

>[!NOTE]
>
>Om du vill granska och analysera databaser och olika funktioner bör du överväga att använda riktiga data i stället för exempeldata. Exempeldata är utformade som en förgenererad butikssimulering, för att demonstrera temadesign och grundläggande butiksbeteenden. Alla exempeldataenheter skrivs direkt i databastabellerna, medan exempeldata installeras.

Du kan installera exempeldata antingen före eller efter installationen av Commerce. När du är klar med exempeldata kan du antingen ta bort den eller installera den på nytt enligt beskrivningen i [Ta bort exempeldatamoduler eller uppdatera exempeldata](remove-or-update.md).

>[!WARNING]
>
>Du kan inte avinstallera exempeldata. Använd endast exempeldata för att lära dig mer om hur Adobe Commerce fungerar. Undvik all utveckling i ett system där du har installerat exempeldata.

Du kan installera valfria exempeldata på något av följande sätt:

| Installationsmetod | Beskrivning | Nödvändig kompetensnivå |
|--- |--- |--- |
| Använda Composer | [Kör `magento sampledata:deploy` om du vill ändra programmets rot `composer.json`](composer-packages.md) för att aktivera exempeldatamoduler. | Kräver kunskap om och åtkomst till filsystemet i Commerce. |
| Klona databaser | [Klona GitHub-databasen](git-repositories.md) och exempeldatalagret och länka dem sedan tillsammans. | Endast för medverkande utvecklare. Alla andra bör använda någon av de föregående metoderna. |
