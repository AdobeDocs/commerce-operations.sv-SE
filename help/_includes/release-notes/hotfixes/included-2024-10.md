---
source-git-commit: b63fa9a8b2b59f6e8dfd7003e75c66caf99d5e81
workflow-type: tm+mt
source-wordcount: '81'
ht-degree: 0%

---
# Programfixar som ingår i säkerhetsuppdateringar för oktober (utom 2.4.4)

Den här versionen innehåller en snabbkorrigering som löser ett problem med Braintree betalningsgateway.

Systemet innehåller nu de fält som krävs för att uppfylla kraven för 3DS VISA-mandat när Braintree används som betalningsgateway. Detta säkerställer att alla transaktioner överensstämmer med de senaste säkerhetsstandarderna från VISA. Tidigare ingick inte dessa ytterligare fält i den betalningsinformation som skickades, vilket kunde ha lett till att de nya kraven för VISA inte hade uppfyllts.

<!--
BUNDLE-3360
-->