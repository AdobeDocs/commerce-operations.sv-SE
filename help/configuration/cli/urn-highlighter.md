---
title: URN highlighter
description: Lär dig hur du ställer in URN-markering i din IDE.
exl-id: 6389ab58-af70-4b33-800e-be3191c5a4cc
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 0%

---

# Översikt över URN-markering

{{file-system-owner}}

Handelskoden refererar till alla XSD-scheman som [Uniform Resource Names (URN)](https://www.ietf.org/rfc/rfc2141.txt). Om du utvecklar kod och behöver referera till XSD:er konfigurerar det här kommandot din integrerade utvecklingsmiljö (IDE) så att URN:er känns igen och markeras. Detta underlättar utvecklingen.

Som standard är en IDE som PhpStorm inte konfigurerad för att identifiera URN:er och därför visas de i röd text enligt följande:

![PhpStorm är inte konfigurerad för att identifiera URN](../../assets/configuration/urn-before.png)

The `bin/magento dev:urn-catalog:generate` Med kommandot kan IDE (för närvarande endast PhpStorm och Visual Studio Code) identifiera och markera URN:er enligt följande:

![Aktivera IDE för att identifiera URN](../../assets/configuration/urn-after.png)

Kommandot skapar i synnerhet följande PhpStorm-konfiguration:

![Exempel på konfiguration av PhpStorm](../../assets/configuration/urn-settings.png)

## Konfigurera din IDE

För närvarande stöds bara PhpStorm och Visual Studio Code.

Kommandosyntax:

```bash
bin/magento dev:urn-catalog:generate <path>
```

Plats `<path>` är sökvägen till din PhpStorm `misc.xml` -fil, som finns i förhållande till projektets rot. Vanligtvis `<path>` är `.idea/misc.xml`.

>[!INFO]
>
>Kör `dev:urn-catalog:generate` varje gång du lägger till, ändrar eller tar bort Commerce 2-moduler som innehåller `*.xsd` filer.
