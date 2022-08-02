---
title: Översikt över sökmotorn
description: Översikt över sökmotoralternativ för Adobe Commerce och Magento Open Source.
source-git-commit: 52c472bf80942339b511292243b5da9babf829d9
workflow-type: tm+mt
source-wordcount: '161'
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

[Krav för sökmotor]: https://devdocs.magento.com/guides/v2.4/install-gde/prereq/elasticsearch.html
[Konfigurera nginx för sökmotorn]: https://devdocs.magento.com/guides/v2.4/install-gde/prereq/es-config-nginx.html
[Konfigurera Apache för sökmotorn]: https://devdocs.magento.com/guides/v2.4/install-gde/prereq/es-config-apache.html
[Elasticsearch]: https://www.elastic.co
[Elasticsearch documentation]: https://www.elastic.co/guide/en/elasticsearch/reference/current/index.html
[Installera Commerce-programvaran]: https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-install.html
[OpenSearch]: https://opensearch.org/docs/latest/opensearch/install/index/
