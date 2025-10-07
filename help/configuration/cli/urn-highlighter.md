---
title: URN highlighter
description: Lär dig hur du ställer in URN-markering i utvecklingsmiljön för Adobe Commerce. Upptäck konfiguration och optimering av XSD-scheman.
exl-id: 6389ab58-af70-4b33-800e-be3191c5a4cc
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '187'
ht-degree: 0%

---

# Översikt över URN-markering

{{file-system-owner}}

Commerce-koden refererar alla XSD-scheman som [URI:er (Uniform Resource Names)](https://www.ietf.org/rfc/rfc2141.txt). Om du utvecklar kod och behöver referera till XSD:er konfigurerar det här kommandot din integrerade utvecklingsmiljö (IDE) så att URN:er känns igen och markeras. Detta underlättar utvecklingen.

Som standard är en IDE som PhpStorm inte konfigurerad för att identifiera URN:er och därför visas de i röd text enligt följande:

![PhpStorm är inte konfigurerad för att identifiera URN](../../assets/configuration/urn-before.png)

Med kommandot `bin/magento dev:urn-catalog:generate` kan din IDE (för närvarande bara PhpStorm och Visual Studio Code) identifiera och markera URN:er enligt följande:

![Aktivera IDE för att identifiera URN](../../assets/configuration/urn-after.png)

Kommandot skapar i synnerhet följande PhpStorm-konfiguration:

![Exempel på PhpStorm-konfiguration](../../assets/configuration/urn-settings.png)

## Konfigurera din IDE

För närvarande stöds bara PhpStorm och Visual Studio Code.

Kommandosyntax:

```bash
bin/magento dev:urn-catalog:generate <path>
```

Där `<path>` är sökvägen till din PhpStorm `misc.xml`-fil, som finns i förhållande till projektets rot. Vanligtvis är `<path>` `.idea/misc.xml`.

>[!INFO]
>
>Om du vill att dina scheman och DTD:n ska vara aktuella kör du kommandot `dev:urn-catalog:generate` varje gång du lägger till, ändrar eller tar bort Commerce 2-moduler som innehåller `*.xsd`-filer.
