---
title: Översikt över sökmotorn
description: Översikt över sökmotoralternativ för Adobe Commerce och Magento Open Source.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '132'
ht-degree: 0%

---


# Översikt över sökmotorn

Från och med version 2.4.4 kräver Adobe Commerce och Magento Open Source antingen [Elasticsearch] eller [OpenSearch] som katalogsökmotor. Tidigare versioner av 2.4.x krävde Elasticsearch. Mer information om hur du installerar en sökmotor och den inledande konfigurationen finns i följande avsnitt:

- [Krav för sökmotor]
- [Konfigurera nginx för sökmotorn]
- [Konfigurera Apache för sökmotorn]
- [Installera Commerce-programvaran] (kommandoradsgränssnitt)

När du har installerat och integrerat sökmotorn med Adobe Commerce måste du utföra ytterligare underhåll:

- [Konfigurera sökstoppord](search-stopwords.md)
- [Sökmotorkonfiguration](configure-search-engine.md)

<!-- Link Definitions -->

[Krav för sökmotor]: ../../installation/prerequisites/search-engine/overview.md
[Konfigurera nginx för sökmotorn]: ../../installation/prerequisites/search-engine/configure-nginx.md
[Konfigurera Apache för sökmotorn]: ../../installation/prerequisites/search-engine/configure-apache.md
[Elasticsearch]: https://www.elastic.co
[Installera Commerce-programvaran]: ../../installation/composer.md
[OpenSearch]: https://opensearch.org/docs/latest/opensearch/install/index/
