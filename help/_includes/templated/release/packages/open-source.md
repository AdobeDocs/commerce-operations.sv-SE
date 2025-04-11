---
source-git-commit: 6752688390a8bea98b49d235515f094386d88bd4
workflow-type: tm+mt
source-wordcount: '3444'
ht-degree: 0%

---
# Magento Open Source

<!-- The 'packages' variable contains the 'packages' node of the '_data/codebase/open-source/composer_lock.json' file
 -->

<!-- The 'packages-dev' variable contains the 'packages-dev' node of the '_data/codebase/open-source/composer_lock.json' file
 -->

<!-- The 'product' variable contains data of the 'magento/product-community-edition' package
 -->

<!-- The edition variable contains `open-source` value from the _data/names.yml file
 -->

Magento Open Source använder Composer för att hantera PHP-paket.

Filen `composer.json` deklarerar paketlistan medan filen `composer.lock` lagrar en fullständig lista över de paket (en fullständig version av varje paket och dess beroenden) som används för att skapa en installation av Magento Open Source.

Följande referensdokumentation genereras från filen `composer.lock` och omfattar obligatoriska paket som ingår i Magento Open Source 2.4.8.

## Beroenden

`magento/product-community-edition 2.4.8` har följande beroenden:

- adobe-commerce/os-extensions-metapackage: 1.0.1
- colinblöenhour/cache-backend-file: ^1.4
- colinblöenhour/cache-backend-redis: ^1.16
- kolinmolentimme/credis: ^1.15
- colinblöenhour/php-redis-session-abstract: ^2.0
- disposition/disposition: ^2.0, !=2.2.16
- duosecurity/duo_api_php: ^1.1
- duosecurity/duo_universal_php: ^1.0
- elasticsearch/elasticsearch: ^8.15
- ext-bcmath: *
- ext-type: *
- Textkurva: *
- extradom: *
- ext-ftp: *
- ext-gd: *
- Text-hash: *
- ext-iconv: *
- ext-intl: *
- ext-mbstring: *
- ext-openssl: *
- ext-pdo_mysql: *
- ext-simplexml: *
- Texttvål: *
- extranatrium: *
- ext-xsl: *
- ext-zip: *
- ezyang/htmlpurifier: ^4.17
- guzzlehttp/guzzle: ^7.5
- laminas/laminas-captcha: ^2.18
- laminas/laminas-code: ^4.13
- laminas/laminas-di: ^3.15
- laminas/laminas-escape: ^2.13
- laminas/laminas-eventsManager: ^3.11
- laminas/laminas-feed: ^2.22
- laminas/laminas-filter: ^2.33
- laminas/laminas-http: ^2.15
- laminas/laminas-i18n: ^2.17
- laminas/laminas-modulemanager: ^2.11
- laminas/laminas-mvc: ^3.6
- laminas/laminas-permissions-acl: ^2.10
- laminas/laminas-servicemanager: ^3.16
- laminas/laminas-soap: ^2.10
- laminas/laminas-stdlib: ^3.11
- laminas/laminas-uri: ^2.9
- laminas/laminas-validator: ^2.23
- Lag/flygsystem: ^3.0
- leag/flysystem-aws-s3-v3: ^3.0
- lib-libxml: *
- magento/composer: ^1.10.1-beta1
- magento/comser-Berodency-version-audit-plugin: ^0.1
- magento/framework: 103.0.8
- magento/framework-amqp: 100.4.6
- magento/framework-bulk: 101.0.4
- magento/framework-message-queue: 100.4.8
- magento/Invental-metapackage: 1.2.8
- magento/language-de_de: 100.4.0
- magento/language-en_us: 100.4.0
- magento/language-es_es: 100.4.0
- magento/language-fr_fr: 100.4.0
- magento/language-nl_nl: 100.4.0
- magento/language-pt_br: 100.4.0
- magento/language-zh_han_cn: 100.4.0
- magento/magento-composer-installer: >=0.4.0
- magento/magento-zf-db: ^3.21.0
- magento/magento2-base: 2.4.8
- [magento/module-admin-analytics](https://developer.adobe.com/commerce/php/module-reference/module-admin-analytics/): 100.4.7
- [magento/module-admin-notification](https://developer.adobe.com/commerce/php/module-reference/module-admin-notification/): 100.4.7
- [magento/module-advanced-pricing-import-export](https://developer.adobe.com/commerce/php/module-reference/module-advanced-pricing-import-export/): 100.4.8
- [magento/module-advanced-search](https://developer.adobe.com/commerce/php/module-reference/module-advanced-search/): 100.4.6
- [magento/module-amqp](https://developer.adobe.com/commerce/php/module-reference/module-amqp/): 100.4.5
- [magento/module-analytics](https://developer.adobe.com/commerce/php/module-reference/module-analytics/): 100.4.8
- [magento/module-application-performance-monitor](https://developer.adobe.com/commerce/php/module-reference/module-application-performance-monitor/): 100.4.1
- [magento/module-application-performance-monitor-new-relic](https://developer.adobe.com/commerce/php/module-reference/module-application-performance-monitor-new-relic/): 100.4.1
- [magento/module-async-config](https://developer.adobe.com/commerce/php/module-reference/module-async-config/): 100.4.1
- [magento/module-asynchronous-operations](https://developer.adobe.com/commerce/php/module-reference/module-asynchronous-operations/): 100.4.8
- [magento/module-authentication](https://developer.adobe.com/commerce/php/module-reference/module-authorization/): 100.4.8
- [magento/module-aws-s3](https://developer.adobe.com/commerce/php/module-reference/module-aws-s3/): 100.4.6
- [magento/module-backend](https://developer.adobe.com/commerce/php/module-reference/module-backend/): 102.0.8
- [magento/module-backup](https://developer.adobe.com/commerce/php/module-reference/module-backup/): 100.4.8
- [magento/module-bundle](https://developer.adobe.com/commerce/php/module-reference/module-bundle/): 101.0.8
- [magento/module-bundle-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-bundle-graph-ql/): 100.4.8
- [magento/module-bundle-import-export](https://developer.adobe.com/commerce/php/module-reference/module-bundle-import-export/): 100.4.7
- [magento/module-cache-invalidate](https://developer.adobe.com/commerce/php/module-reference/module-cache-invalidate/): 100.4.6
- [magento/module-captcha](https://developer.adobe.com/commerce/php/module-reference/module-captcha/): 100.4.8
- [magento/module-cardinal-commerce](https://developer.adobe.com/commerce/php/module-reference/module-cardinal-commerce/): 100.4.6
- [magento/module-catalog](https://developer.adobe.com/commerce/php/module-reference/module-catalog/): 104.0.8
- [magento/module-catalog-analytics](https://developer.adobe.com/commerce/php/module-reference/module-catalog-analytics/): 100.4.5
- [magento/module-catalog-cms-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-catalog-cms-graph-ql/): 100.4.4
- [magento/module-catalog-customer-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-catalog-customer-graph-ql/): 100.4.7
- [magento/module-catalog-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-catalog-graph-ql/): 100.4.8
- [magento/module-catalog-import-export](https://developer.adobe.com/commerce/php/module-reference/module-catalog-import-export/): 101.1.8
- [magento/module-catalog-layer](https://developer.adobe.com/commerce/php/module-reference/module-catalog-inventory/): 100.4.8
- [magento/module-catalog-Inventalog-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-catalog-inventory-graph-ql/): 100.4.5
- [magento/module-catalog-rule](https://developer.adobe.com/commerce/php/module-reference/module-catalog-rule/): 101.2.8
- [magento/module-catalog-rule-configurable](https://developer.adobe.com/commerce/php/module-reference/module-catalog-rule-configurable/): 100.4.7
- [magento/module-catalog-rule-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-catalog-rule-graph-ql/): 100.4.5
- [magento/module-catalog-search](https://developer.adobe.com/commerce/php/module-reference/module-catalog-search/): 102.0.8
- [magento/module-catalog-url-rewrite](https://developer.adobe.com/commerce/php/module-reference/module-catalog-url-rewrite/): 100.4.8
- [magento/module-catalog-url-rewrite-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-catalog-url-rewrite-graph-ql/): 100.4.6
- [magento/module-catalog-widget](https://developer.adobe.com/commerce/php/module-reference/module-catalog-widget/): 100.4.8
- [magento/module-checkout](https://developer.adobe.com/commerce/php/module-reference/module-checkout/): 100.4.8
- [magento/module-checkout-agreements](https://developer.adobe.com/commerce/php/module-reference/module-checkout-agreements/): 100.4.7
- [magento/module-checkout-agreements-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-checkout-agreements-graph-ql/): 100.4.4
- [magento/module-cms](https://developer.adobe.com/commerce/php/module-reference/module-cms/): 104.0.8
- [magento/module-cms-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-cms-graph-ql/): 100.4.5
- [magento/module-cms-url-rewrite](https://developer.adobe.com/commerce/php/module-reference/module-cms-url-rewrite/): 100.4.7
- [magento/module-cms-url-rewrite-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-cms-url-rewrite-graph-ql/): 100.4.6
- [magento/module-compare-list-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-compare-list-graph-ql/): 100.4.4
- [magento/module-config](https://developer.adobe.com/commerce/php/module-reference/module-config/): 101.2.8
- [magento/module-configurable-import-export](https://developer.adobe.com/commerce/php/module-reference/module-configurable-import-export/): 100.4.6
- [magento/module-configurable-product](https://developer.adobe.com/commerce/php/module-reference/module-configurable-product/): 100.4.8
- [magento/module-configurable-product-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-configurable-product-graph-ql/): 100.4.8
- [magento/module-configurable-product-sales](https://developer.adobe.com/commerce/php/module-reference/module-configurable-product-sales/): 100.4.5
- [magento/module-contact](https://developer.adobe.com/commerce/php/module-reference/module-contact/): 100.4.7
- [magento/module-contact-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-contact-graph-ql/): 100.4.1
- [magento/module-cookie](https://developer.adobe.com/commerce/php/module-reference/module-cookie/): 100.4.8
- [magento/module-cron](https://developer.adobe.com/commerce/php/module-reference/module-cron/): 100.4.8
- [magento/module-csp](https://developer.adobe.com/commerce/php/module-reference/module-csp/): 100.4.7
- [magento/module-currency-symbol](https://developer.adobe.com/commerce/php/module-reference/module-currency-symbol/): 100.4.6
- [magento/module-customer](https://developer.adobe.com/commerce/php/module-reference/module-customer/): 103.0.8
- [magento/module-customer-analytics](https://developer.adobe.com/commerce/php/module-reference/module-customer-analytics/): 100.4.5
- [magento/module-customer-downloadable-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-customer-downloadable-graph-ql/): 100.4.4
- [magento/module-customer-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-customer-graph-ql/): 100.4.8
- [magento/module-customer-import-export](https://developer.adobe.com/commerce/php/module-reference/module-customer-import-export/): 100.4.8
- [magento/module-deploy](https://developer.adobe.com/commerce/php/module-reference/module-deploy/): 100.4.8
- [magento/module-developer](https://developer.adobe.com/commerce/php/module-reference/module-developer/): 100.4.8
- [magento/module-dhl](https://developer.adobe.com/commerce/php/module-reference/module-dhl/): 100.4.7
- [magento/module-directory](https://developer.adobe.com/commerce/php/module-reference/module-directory/): 100.4.8
- [magento/module-directory-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-directory-graph-ql/): 100.4.6
- [magento/module-downloadable](https://developer.adobe.com/commerce/php/module-reference/module-downloadable/): 100.4.8
- [magento/module-downloadable-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-downloadable-graph-ql/): 100.4.8
- [magento/module-downloadable-import-export](https://developer.adobe.com/commerce/php/module-reference/module-downloadable-import-export/): 100.4.7
- [magento/module-eav](https://developer.adobe.com/commerce/php/module-reference/module-eav/): 102.1.8
- [magento/module-eav-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-eav-graph-ql/): 100.4.5
- [magento/module-elasticsearch](https://developer.adobe.com/commerce/php/module-reference/module-elasticsearch/): 101.0.8
- [magento/module-elasticsearch-8](https://developer.adobe.com/commerce/php/module-reference/module-elasticsearch-8/): 101.0.0
- [magento/module-email](https://developer.adobe.com/commerce/php/module-reference/module-email/): 101.1.8
- [magento/module-encryption-key](https://developer.adobe.com/commerce/php/module-reference/module-encryption-key/): 100.4.6
- [magento/module-fedex](https://developer.adobe.com/commerce/php/module-reference/module-fedex/): 100.4.6
- [magento/module-present-message](https://developer.adobe.com/commerce/php/module-reference/module-gift-message/): 100.4.7
- [magento/module-present-message-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-gift-message-graph-ql/): 100.4.6
- [magento/module-google-adwords](https://developer.adobe.com/commerce/php/module-reference/module-google-adwords/): 100.4.5
- [magento/module-google-analytics](https://developer.adobe.com/commerce/php/module-reference/module-google-analytics/): 100.4.4
- [magento/module-google-gtag](https://developer.adobe.com/commerce/php/module-reference/module-google-gtag/): 100.4.3
- [magento/module-google-optimizer](https://developer.adobe.com/commerce/php/module-reference/module-google-optimizer/): 100.4.7
- [magento/module-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-graph-ql/): 100.4.8
- [magento/module-graph-ql-cache](https://developer.adobe.com/commerce/php/module-reference/module-graph-ql-cache/): 100.4.5
- [magento/module-graph-ql-new-relic](https://developer.adobe.com/commerce/php/module-reference/module-graph-ql-new-relic/): 100.4.1
- [magento/module-graph-ql-resolver-cache](https://developer.adobe.com/commerce/php/module-reference/module-graph-ql-resolver-cache/): 100.4.1
- [magento/module-grouped-catalog-layer](https://developer.adobe.com/commerce/php/module-reference/module-grouped-catalog-inventory/): 100.4.5
- [magento/module-grouped-import-export](https://developer.adobe.com/commerce/php/module-reference/module-grouped-import-export/): 100.4.6
- [magento/module-grouped-product](https://developer.adobe.com/commerce/php/module-reference/module-grouped-product/): 100.4.8
- [magento/module-grouped-product-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-grouped-product-graph-ql/): 100.4.8
- [magento/module-import-export](https://developer.adobe.com/commerce/php/module-reference/module-import-export/): 101.0.8
- [magento/module-indexer](https://developer.adobe.com/commerce/php/module-reference/module-indexer/): 100.4.8
- [magento/module-instant-purchase](https://developer.adobe.com/commerce/php/module-reference/module-instant-purchase/): 100.4.7
- [magento/module-integration](https://developer.adobe.com/commerce/php/module-reference/module-integration/): 100.4.8
- [magento/module-integration-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-integration-graph-ql/): 100.4.1
- [magento/module-jwt-framework-adapter](https://developer.adobe.com/commerce/php/module-reference/module-jwt-framework-adapter/): 100.4.4
- [magento/module-jwt-user-token](https://developer.adobe.com/commerce/php/module-reference/module-jwt-user-token/): 100.4.3
- [magento/module-layered-navigation](https://developer.adobe.com/commerce/php/module-reference/module-layered-navigation/): 100.4.8
- [magento/module-login-as-customer](https://developer.adobe.com/commerce/php/module-reference/module-login-as-customer/): 100.4.8
- [magento/module-login-as-customer-admin-ui](https://developer.adobe.com/commerce/php/module-reference/module-login-as-customer-admin-ui/): 100.4.8
- [magento/module-login-as-customer-api](https://developer.adobe.com/commerce/php/module-reference/module-login-as-customer-api/): 100.4.7
- [magento/module-login-as-customer-assistance](https://developer.adobe.com/commerce/php/module-reference/module-login-as-customer-assistance/): 100.4.7
- [magento/module-login-as-customer-front-ui](https://developer.adobe.com/commerce/php/module-reference/module-login-as-customer-frontend-ui/): 100.4.7
- [magento/module-login-as-customer-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-login-as-customer-graph-ql/): 100.4.5
- [magento/module-login-as-customer-log](https://developer.adobe.com/commerce/php/module-reference/module-login-as-customer-log/): 100.4.6
- [magento/module-login-as-customer-page-cache](https://developer.adobe.com/commerce/php/module-reference/module-login-as-customer-page-cache/): 100.4.7
- [magento/module-login-as-customer-quote](https://developer.adobe.com/commerce/php/module-reference/module-login-as-customer-quote/): 100.4.6
- [magento/module-login-as-customer-sales](https://developer.adobe.com/commerce/php/module-reference/module-login-as-customer-sales/): 100.4.7
- [magento/module-marketplace](https://developer.adobe.com/commerce/php/module-reference/module-marketplace/): 100.4.6
- [magento/module-media-content](https://developer.adobe.com/commerce/php/module-reference/module-media-content/): 100.4.6
- [magento/module-media-content-api](https://developer.adobe.com/commerce/php/module-reference/module-media-content-api/): 100.4.7
- [magento/module-media-content-catalog](https://developer.adobe.com/commerce/php/module-reference/module-media-content-catalog/): 100.4.6
- [magento/module-media-content-cms](https://developer.adobe.com/commerce/php/module-reference/module-media-content-cms/): 100.4.6
- [magento/module-media-content-synchronization](https://developer.adobe.com/commerce/php/module-reference/module-media-content-synchronization/): 100.4.7
- [magento/module-media-content-synchronization-api](https://developer.adobe.com/commerce/php/module-reference/module-media-content-synchronization-api/): 100.4.6
- [magento/module-media-content-synchronization-catalog](https://developer.adobe.com/commerce/php/module-reference/module-media-content-synchronization-catalog/): 100.4.5
- [magento/module-media-content-synchronization-cms](https://developer.adobe.com/commerce/php/module-reference/module-media-content-synchronization-cms/): 100.4.5
- [magento/module-media-gallery](https://developer.adobe.com/commerce/php/module-reference/module-media-gallery/): 100.4.7
- [magento/module-media-gallery-api](https://developer.adobe.com/commerce/php/module-reference/module-media-gallery-api/): 101.0.7
- [magento/module-media-gallery-catalog](https://developer.adobe.com/commerce/php/module-reference/module-media-gallery-catalog/): 100.4.5
- [magento/module-media-gallery-catalog-integration](https://developer.adobe.com/commerce/php/module-reference/module-media-gallery-catalog-integration/): 100.4.5
- [magento/module-media-gallery-catalog-ui](https://developer.adobe.com/commerce/php/module-reference/module-media-gallery-catalog-ui/): 100.4.5
- [magento/module-media-gallery-cms-ui](https://developer.adobe.com/commerce/php/module-reference/module-media-gallery-cms-ui/): 100.4.5
- [magento/module-media-gallery-integration](https://developer.adobe.com/commerce/php/module-reference/module-media-gallery-integration/): 100.4.7
- [magento/module-media-gallery-metadata](https://developer.adobe.com/commerce/php/module-reference/module-media-gallery-metadata/): 100.4.6
- [magento/module-media-gallery-metadata-api](https://developer.adobe.com/commerce/php/module-reference/module-media-gallery-metadata-api/): 100.4.5
- [magento/module-media-gallery-renditions](https://developer.adobe.com/commerce/php/module-reference/module-media-gallery-renditions/): 100.4.6
- [magento/module-media-gallery-renditions-api](https://developer.adobe.com/commerce/php/module-reference/module-media-gallery-renditions-api/): 100.4.5
- [magento/module-media-gallery-synchronization](https://developer.adobe.com/commerce/php/module-reference/module-media-gallery-synchronization/): 100.4.7
- [magento/module-media-gallery-synchronization-api](https://developer.adobe.com/commerce/php/module-reference/module-media-gallery-synchronization-api/): 100.4.6
- [magento/module-media-gallery-synchronization-metadata](https://developer.adobe.com/commerce/php/module-reference/module-media-gallery-synchronization-metadata/): 100.4.4
- [magento/module-media-gallery-ui](https://developer.adobe.com/commerce/php/module-reference/module-media-gallery-ui/): 100.4.7
- [magento/module-media-gallery-ui-api](https://developer.adobe.com/commerce/php/module-reference/module-media-gallery-ui-api/): 100.4.6
- [magento/module-media-storage](https://developer.adobe.com/commerce/php/module-reference/module-media-storage/): 100.4.7
- [magento/module-message-queue](https://developer.adobe.com/commerce/php/module-reference/module-message-queue/): 100.4.8
- [magento/module-msrp](https://developer.adobe.com/commerce/php/module-reference/module-msrp/): 100.4.7
- [magento/module-msrp-configurable-product](https://developer.adobe.com/commerce/php/module-reference/module-msrp-configurable-product/): 100.4.5
- [magento/module-msrp-grouped-product](https://developer.adobe.com/commerce/php/module-reference/module-msrp-grouped-product/): 100.4.5
- [magento/module-multishipping](https://developer.adobe.com/commerce/php/module-reference/module-multishipping/): 100.4.8
- [magento/module-mysql-mq](https://developer.adobe.com/commerce/php/module-reference/module-mysql-mq/): 100.4.6
- [magento/module-new-relic-reporting](https://developer.adobe.com/commerce/php/module-reference/module-new-relic-reporting/): 100.4.6
- [magento/module-newsletter](https://developer.adobe.com/commerce/php/module-reference/module-newsletter/): 100.4.8
- [magento/module-newsletter-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-newsletter-graph-ql/): 100.4.5
- [magento/module-offline-payments](https://developer.adobe.com/commerce/php/module-reference/module-offline-payments/): 100.4.6
- [magento/module-offline-shipping](https://developer.adobe.com/commerce/php/module-reference/module-offline-shipping/): 100.4.7
- [magento/module-open-search](https://developer.adobe.com/commerce/php/module-reference/module-open-search/): 100.4.2
- [magento/module-order-cancelation](https://developer.adobe.com/commerce/php/module-reference/module-order-cancellation/): 100.4.1
- [magento/module-order-cancelation-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-order-cancellation-graph-ql/): 100.4.1
- [magento/module-order-cancelation-ui](https://developer.adobe.com/commerce/php/module-reference/module-order-cancellation-ui/): 100.4.1
- [magento/module-page-cache](https://developer.adobe.com/commerce/php/module-reference/module-page-cache/): 100.4.8
- [magento/module-payment](https://developer.adobe.com/commerce/php/module-reference/module-payment/): 100.4.8
- [magento/module-payment-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-payment-graph-ql/): 100.4.3
- [magento/module-paypal](https://developer.adobe.com/commerce/php/module-reference/module-paypal/): 101.0.8
- [magento/module-paypal-captcha](https://developer.adobe.com/commerce/php/module-reference/module-paypal-captcha/): 100.4.5
- [magento/module-paypal-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-paypal-graph-ql/): 100.4.6
- [magento/module-persistent](https://developer.adobe.com/commerce/php/module-reference/module-persistent/): 100.4.8
- [magento/module-product-alert](https://developer.adobe.com/commerce/php/module-reference/module-product-alert/): 100.4.7
- [magento/module-product-video](https://developer.adobe.com/commerce/php/module-reference/module-product-video/): 100.4.8
- [magento/module-quote](https://developer.adobe.com/commerce/php/module-reference/module-quote/): 101.2.8
- [magento/module-quote-analytics](https://developer.adobe.com/commerce/php/module-reference/module-quote-analytics/): 100.4.7
- [magento/module-quote-bundle-options](https://developer.adobe.com/commerce/php/module-reference/module-quote-bundle-options/): 100.4.4
- [magento/module-quote-configurable-options](https://developer.adobe.com/commerce/php/module-reference/module-quote-configurable-options/): 100.4.4
- [magento/module-quote-downloadable-links](https://developer.adobe.com/commerce/php/module-reference/module-quote-downloadable-links/): 100.4.4
- [magento/module-quote-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-quote-graph-ql/): 100.4.8
- [magento/module-related-product-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-related-product-graph-ql/): 100.4.5
- [magento/module-release-notification](https://developer.adobe.com/commerce/php/module-reference/module-release-notification/): 100.4.6
- [magento/module-remote-storage](https://developer.adobe.com/commerce/php/module-reference/module-remote-storage/): 100.4.6
- [magento/module-reports](https://developer.adobe.com/commerce/php/module-reference/module-reports/): 100.4.8
- [magento/module-require-js](https://developer.adobe.com/commerce/php/module-reference/module-require-js/): 100.4.4
- [magento/module-review](https://developer.adobe.com/commerce/php/module-reference/module-review/): 100.4.8
- [magento/module-review-analytics](https://developer.adobe.com/commerce/php/module-reference/module-review-analytics/): 100.4.5
- [magento/module-review-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-review-graph-ql/): 100.4.4
- [magento/module-robots](https://developer.adobe.com/commerce/php/module-reference/module-robots/): 101.1.4
- [magento/module-rss](https://developer.adobe.com/commerce/php/module-reference/module-rss/): 100.4.6
- [magento/module-rule](https://developer.adobe.com/commerce/php/module-reference/module-rule/): 100.4.7
- [magento/module-sales](https://developer.adobe.com/commerce/php/module-reference/module-sales/): 103.0.8
- [magento/module-sales-analytics](https://developer.adobe.com/commerce/php/module-reference/module-sales-analytics/): 100.4.5
- [magento/module-sales-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-sales-graph-ql/): 100.4.8
- [magento/module-sales-layer](https://developer.adobe.com/commerce/php/module-reference/module-sales-inventory/): 100.4.5
- [magento/module-sales-rule](https://developer.adobe.com/commerce/php/module-reference/module-sales-rule/): 101.2.8
- [magento/module-sales-rule-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-sales-rule-graph-ql/): 100.4.1
- [magento/module-sales-sequence](https://developer.adobe.com/commerce/php/module-reference/module-sales-sequence/): 100.4.5
- [magento/module-sample-data](https://developer.adobe.com/commerce/php/module-reference/module-sample-data/): 100.4.6
- [magento/module-search](https://developer.adobe.com/commerce/php/module-reference/module-search/): 101.1.8
- [magento/module-security](https://developer.adobe.com/commerce/php/module-reference/module-security/): 100.4.8
- [magento/module-send-kompis](https://developer.adobe.com/commerce/php/module-reference/module-send-friend/): 100.4.6
- [magento/module-send-kompis-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-send-friend-graph-ql/): 100.4.4
- [magento/module-shipping](https://developer.adobe.com/commerce/php/module-reference/module-shipping/): 100.4.8
- [magento/module-sitemap](https://developer.adobe.com/commerce/php/module-reference/module-sitemap/): 100.4.7
- [magento/module-store](https://developer.adobe.com/commerce/php/module-reference/module-store/): 101.1.8
- [magento/module-store-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-store-graph-ql/): 100.4.6
- [magento/module-swagger](https://developer.adobe.com/commerce/php/module-reference/module-swagger/): 100.4.7
- [magento/module-swagger-webapi](https://developer.adobe.com/commerce/php/module-reference/module-swagger-webapi/): 100.4.4
- [magento/module-swagger-webapi-async](https://developer.adobe.com/commerce/php/module-reference/module-swagger-webapi-async/): 100.4.4
- [magento/module-swatches](https://developer.adobe.com/commerce/php/module-reference/module-swatches/): 100.4.8
- [magento/module-swatches-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-swatches-graph-ql/): 100.4.6
- [magento/module-swatches-layered-navigation](https://developer.adobe.com/commerce/php/module-reference/module-swatches-layered-navigation/): 100.4.4
- [magento/module-tax](https://developer.adobe.com/commerce/php/module-reference/module-tax/): 100.4.8
- [magento/module-tax-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-tax-graph-ql/): 100.4.4
- [magento/module-tax-import-export](https://developer.adobe.com/commerce/php/module-reference/module-tax-import-export/): 100.4.7
- [magento/module-theme](https://developer.adobe.com/commerce/php/module-reference/module-theme/): 101.1.8
- [magento/module-theme-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-theme-graph-ql/): 100.4.5
- [magento/module-translation](https://developer.adobe.com/commerce/php/module-reference/module-translation/): 100.4.8
- [magento/module-ui](https://developer.adobe.com/commerce/php/module-reference/module-ui/): 101.2.8
- [magento/module-ups](https://developer.adobe.com/commerce/php/module-reference/module-ups/): 100.4.8
- [magento/module-url-rewrite](https://developer.adobe.com/commerce/php/module-reference/module-url-rewrite/): 102.0.7
- [magento/module-url-rewrite-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-url-rewrite-graph-ql/): 100.4.7
- [magento/module-user](https://developer.adobe.com/commerce/php/module-reference/module-user/): 101.2.8
- [magento/module-usps](https://developer.adobe.com/commerce/php/module-reference/module-usps/): 100.4.7
- [magento/module-variable](https://developer.adobe.com/commerce/php/module-reference/module-variable/): 100.4.6
- [magento/module-vault](https://developer.adobe.com/commerce/php/module-reference/module-vault/): 101.2.8
- [magento/module-vault-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-vault-graph-ql/): 100.4.4
- [magento/module-version](https://developer.adobe.com/commerce/php/module-reference/module-version/): 100.4.5
- [magento/module-webapi](https://developer.adobe.com/commerce/php/module-reference/module-webapi/): 100.4.7
- [magento/module-webapi-async](https://developer.adobe.com/commerce/php/module-reference/module-webapi-async/): 100.4.6
- [magento/module-webapi-security](https://developer.adobe.com/commerce/php/module-reference/module-webapi-security/): 100.4.5
- [magento/module-weee](https://developer.adobe.com/commerce/php/module-reference/module-weee/): 100.4.8
- [magento/module-weee-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-weee-graph-ql/): 100.4.5
- [magento/module-widget](https://developer.adobe.com/commerce/php/module-reference/module-widget/): 101.2.8
- [magento/module-önsklist](https://developer.adobe.com/commerce/php/module-reference/module-wishlist/): 101.2.8
- [magento/module-önsklist-analytics](https://developer.adobe.com/commerce/php/module-reference/module-wishlist-analytics/): 100.4.6
- [magento/module-önsklist-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-wishlist-graph-ql/): 100.4.8
- magento/page-builder: 1.7.5
- magento/security-package: 1.1.7
- magento/theme-adminhtml-backend: 100.4.8
- magento/theme-front-blank: 100.4.8
- magento/theme-front-luma: 100.4.8
- magento/zend-cache: ^1.16
- magento/zend-db: ^1.16
- magento/zend-pdf: ^1.16
- monolog/monolog: ^3.6
- opensearch-project/opensearch-php: ^2.3
- pelago/avgränsare: ^7.0
- php: ~8.2.0|~8.3.0||~8.4.0
- php-amqplib/php-amqplib: ^3.2
- phpseclib/mcrypt_compat: ^2.0
- phpseclib/phpseclib: ^3.0
- psr/log: ^2 || ^3
- ramsey/uuid: ^4.2
- symbol/konsol: ^6.4
- symbol/intl: ^6.4
- symfony/mailer: ^6.4
- symbol/mime: ^6.4
- symbol/process: ^6.4
- symbol/sträng: ^6.4
- tedivm/jkrink: ^1.4
- tubalmartin/cssmin: ^4.1
- web-token/jwt-framework: ^3.4
- webonyx/graphql-php: ^15.0
- wikimedia/less.php: ^5.0

## Tredjepartslicenser

### Apache-2.0, LGPL-2.1-only

<table>
  <thead>
    <tr>
      <th>Namn</th>
      <th>Typ</th>
      <th>Beskrivning</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/opensearch-project/opensearch-php">opensearch-project/opensearch-php</a>
    </td>
    <td>Bibliotek</td>
    <td>PHP-klient för OpenSearch</td>
  </tr>
  </tbody>
</table>

### Apache-2.0

<table>
  <thead>
    <tr>
      <th>Namn</th>
      <th>Typ</th>
      <th>Beskrivning</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/adobe/stock-api-libphp">astock/stock-api-libphp</a>
    </td>
    <td>Bibliotek</td>
    <td>Adobe Stock API-bibliotek</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/awslabs/aws-crt-php">aws/aws-crt-php</a>
    </td>
    <td>Bibliotek</td>
    <td>AWS Common Runtime for PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/aws/aws-sdk-php">aws/aws-sdk-php</a>
    </td>
    <td>Bibliotek</td>
    <td>AWS SDK for PHP - Använd Amazon Web Services i PHP-projekt</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/opentelemetry-php/api">open-telemetry/api</a>
    </td>
    <td>Bibliotek</td>
    <td>API för OpenTelemetry PHP.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/opentelemetry-php/context">open-telemetry/context</a>
    </td>
    <td>Bibliotek</td>
    <td>Context implementation for OpenTelemetry PHP.</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree
    </td>
    <td>Metapackage</td>
    <td>Braintree Magento</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/wikimedia/less.php">wikimedia/less.php</a>
    </td>
    <td>Bibliotek</td>
    <td>PHP-port för LESS-processor</td>
  </tr>
  </tbody>
</table>

### BSD-2-klausul

<table>
  <thead>
    <tr>
      <th>Namn</th>
      <th>Typ</th>
      <th>Beskrivning</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/Bacon/BaconQrCode">bacon/bacon-qr-code</a>
    </td>
    <td>Bibliotek</td>
    <td>BaconQrCode är en QR-kodgenerator för PHP.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/DASPRiD/Enum">dasprid/enum</a>
    </td>
    <td>Bibliotek</td>
    <td>PHP 7.1 enum implementation</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/webimpress/safe-writer">webimpress/safe-writer</a>
    </td>
    <td>Bibliotek</td>
    <td>Verktyg för att skriva filer på ett säkert sätt, för att undvika konkurrensförhållanden</td>
  </tr>
  </tbody>
</table>

### BSD-3-klausul

<table>
  <thead>
    <tr>
      <th>Namn</th>
      <th>Typ</th>
      <th>Beskrivning</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/colinmollenhour/Cm_Cache_Backend_File">colinMovie/cache-backend-file</a>
    </td>
    <td>Magento-modul</td>
    <td>Zend_Cache_Backend_File-serverdelen har mycket dålig prestanda för att rensa med taggar, vilket gör den oanvändbar när antalet cachelagrade objekt ökar. Den här serverdelen gör många ändringar, vilket ger en rejäl prestandaökning, särskilt för tagghantering.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/colinmollenhour/php-redis-session-abstract">colinblöenhour/php-redis-session-abstract</a>
    </td>
    <td>Bibliotek</td>
    <td>En Redis-baserad sessionshanterare med optimistisk låsning</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/duosecurity/duo_universal_php">duosecurity/duo_universal_php</a>
    </td>
    <td>Bibliotek</td>
    <td>En PHP-implementering av Duo Universal SDK.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/firebase/php-jwt">firebase/php-jwt</a>
    </td>
    <td>Bibliotek</td>
    <td>Ett enkelt bibliotek för kodning och avkodning av JSON Web Tokens (JWT) i PHP. Ska överensstämma med den aktuella specifikationen.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-captcha">laminas/laminas-captcha</a>
    </td>
    <td>Bibliotek</td>
    <td>Generera och validera CAPTCHA med Figlets, images, ReCaptcha med flera</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-code">laminas/laminas-code</a>
    </td>
    <td>Bibliotek</td>
    <td>Tillägg till API:t för PHP-reflektion, statisk kodskanning och kodgenerering</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-config">laminas/laminas-config</a>
    </td>
    <td>Bibliotek</td>
    <td>innehåller ett kapslat objektegenskapsbaserat användargränssnitt för åtkomst av konfigurationsdata i programkoden</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-di">laminas/laminas-di</a>
    </td>
    <td>Bibliotek</td>
    <td>Automatisk beroendeinjektion för PSR-11-behållare</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-escaper">laminas/laminas-escape</a>
    </td>
    <td>Bibliotek</td>
    <td>Undvik säkert HTML, HTML-attribut, JavaScript, CSS och URL:er</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-eventmanager">laminas/laminas-eventManager</a>
    </td>
    <td>Bibliotek</td>
    <td>Utlös och lyssna på händelser i ett PHP-program</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-feed">laminas/laminas-feed</a>
    </td>
    <td>Bibliotek</td>
    <td>innehåller funktioner för att skapa och använda RSS- och Atom-flöden</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-filter">laminas/laminas-filter</a>
    </td>
    <td>Bibliotek</td>
    <td>Filtrera och normalisera data och filer programmatiskt</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-http">laminas/laminas-http</a>
    </td>
    <td>Bibliotek</td>
    <td>Ger ett enkelt gränssnitt för att utföra HTTP-begäranden (Hyper-Text Transfer Protocol)</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-i18n">laminas/laminas-i18n</a>
    </td>
    <td>Bibliotek</td>
    <td>Ange översättningar för programmet och filtrera och validera internationella värden</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-json">laminas/laminas-json</a>
    </td>
    <td>Bibliotek</td>
    <td>erbjuder bekväma metoder för att serialisera inbyggda PHP till JSON och avkoda JSON till inbyggda PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-loader">laminas/laminas-loader</a>
    </td>
    <td>Bibliotek</td>
    <td>Inläsningsstrategier för automatisk inläsning och plugin-program</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-modulemanager">laminas/laminas-modulemanager</a>
    </td>
    <td>Bibliotek</td>
    <td>Modulärt programsystem för laminas-mvc-program</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-mvc">laminas/laminas-mvc</a>
    </td>
    <td>Bibliotek</td>
    <td>Laminas händelsestyrda MVC-lager, inklusive MVC-program, styrenheter och plugin-program</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-permissions-acl">laminas/laminas-permissions-acl</a>
    </td>
    <td>Bibliotek</td>
    <td>Tillhandahåller en enkel och flexibel ACL-implementering (access control list) för behörighetshantering</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-recaptcha">laminas/laminas-recaptcha</a>
    </td>
    <td>Bibliotek</td>
    <td>OOP-wrapper för ReCaptcha-webbtjänsten</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-router">laminas/laminas-router</a>
    </td>
    <td>Bibliotek</td>
    <td>Flexibelt routningssystem för HTTP- och konsolapplikationer</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-server">laminas/laminas-server</a>
    </td>
    <td>Bibliotek</td>
    <td>Skapa reflektionsbaserade RPC-servrar</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-servicemanager">laminas/laminas-servicemanager</a>
    </td>
    <td>Bibliotek</td>
    <td>Behållare för fabriksstyrd beroendeinjektion</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-session">laminas/laminas-session</a>
    </td>
    <td>Bibliotek</td>
    <td>Objektorienterat gränssnitt för PHP-sessioner och -lagring</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-soap">laminas/laminas-soap</a>
    </td>
    <td>Bibliotek</td>
    <td></td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-stdlib">laminas/laminas-stdlib</a>
    </td>
    <td>Bibliotek</td>
    <td>SPL-tillägg, matrisverktyg, felhanterare med mera</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-text">laminas/laminas-text</a>
    </td>
    <td>Bibliotek</td>
    <td>Skapa FIGlets och textbaserade tabeller</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-translator">laminas/laminas-translator</a>
    </td>
    <td>Bibliotek</td>
    <td>Gränssnitt för Translator-komponenten av laminas-i18n</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-uri">laminas/laminas-uri</a>
    </td>
    <td>Bibliotek</td>
    <td>En komponent som underlättar manipulering och validering av URI (Uniform Resource Identifiers)</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-validator">laminas/laminas-validator</a>
    </td>
    <td>Bibliotek</td>
    <td>Valideringsklasser för ett stort antal domäner och möjlighet att kedja validerare för att skapa komplexa valideringskriterier</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-view">laminas/laminas-view</a>
    </td>
    <td>Bibliotek</td>
    <td>Flexibla visningslager med stöd för flera visningslager, stödfunktioner med mera</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/marc-mabe/php-enum">marc-mabe/php-enum</a>
    </td>
    <td>Bibliotek</td>
    <td>Enkel och snabb implementering av uppräkningar med inbyggd PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/nikic/PHP-Parser">nikic/php-parser</a>
    </td>
    <td>Bibliotek</td>
    <td>En PHP-parser skriven i PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/phpfui/recaptcha">phpfui/recaptcha</a>
    </td>
    <td>Bibliotek</td>
    <td>Klientbibliotek för Google reCAPTCHA för PHP 8.4 och senare</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/tedious/JShrink">tedivm/jkrink</a>
    </td>
    <td>Bibliotek</td>
    <td>Javascript-minifier inbyggd i PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/tubalmartin/YUI-CSS-compressor-PHP-port">tubalmartin/cssmin</a>
    </td>
    <td>Bibliotek</td>
    <td>En PHP-port för YUI CSS-komprimeraren</td>
  </tr>
  </tbody>
</table>

### BSD-3-Clause-Modification

<table>
  <thead>
    <tr>
      <th>Namn</th>
      <th>Typ</th>
      <th>Beskrivning</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/colinmollenhour/Cm_Cache_Backend_Redis">colinkvart/hour/cache-backend-redis</a>
    </td>
    <td>Magento-modul</td>
    <td>Zend_Cache backend använder Redis med fullständigt stöd för taggar.</td>
  </tr>
  </tbody>
</table>

### ISC

<table>
  <thead>
    <tr>
      <th>Namn</th>
      <th>Typ</th>
      <th>Beskrivning</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/paragonie/sodium_compat">paragonie/natrium_compat</a>
    </td>
    <td>Bibliotek</td>
    <td>Ren PHP-implementering av libnatrium; använder PHP-tillägget om det finns</td>
  </tr>
  </tbody>
</table>

### LGPL-2.1-eller-senare

<table>
  <thead>
    <tr>
      <th>Namn</th>
      <th>Typ</th>
      <th>Beskrivning</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/ezyang/htmlpurifier">ezyang/htmlpurifier</a>
    </td>
    <td>Bibliotek</td>
    <td>Standardkompatibelt HTML-filter som skrivits i PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-amqplib/php-amqplib">php-amqplib/php-amqplib</a>
    </td>
    <td>Bibliotek</td>
    <td>Tidigare videlalvaro/php-amqplib.  Det här biblioteket är en ren PHP-implementering av AMQP-protokollet. Den har testats mot RabbitMQ.</td>
  </tr>
  </tbody>
</table>

### MIT

<table>
  <thead>
    <tr>
      <th>Namn</th>
      <th>Typ</th>
      <th>Beskrivning</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/braintree/braintree_php">braintree/braintree_php</a>
    </td>
    <td>Bibliotek</td>
    <td>Braintree PHP Client Library</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/brick/math">brick/math</a>
    </td>
    <td>Bibliotek</td>
    <td>Arbitrary-precision aritmetic library</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/brick/varexporter">brick/varexporter</a>
    </td>
    <td>Bibliotek</td>
    <td>Ett kraftfullt alternativ till var_export(), som kan exportera stängningar och objekt utan __set_state()</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ChristianRiesen/base32">Christian-riesen/base32</a>
    </td>
    <td>Bibliotek</td>
    <td>Base32-kodare/avkodare enligt RFC 4648</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/colinmollenhour/credis">colinblöenhour/credis</a>
    </td>
    <td>Bibliotek</td>
    <td>Credis är ett lättviktsgränssnitt för Redis nyckelvärdenhet som omsluter phpredis-biblioteket när det är tillgängligt för bättre prestanda.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/ca-bundle">disposition/ca-bundle</a>
    </td>
    <td>Bibliotek</td>
    <td>Gör att du kan hitta en sökväg till systemets CA-paket och inkluderar en reservanslutning till Mozilla CA-paketet.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/class-map-generator">dispositör/klass-map-generator</a>
    </td>
    <td>Bibliotek</td>
    <td>Verktyg för att skanna PHP-kod och generera klasskartor.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/composer">disposition/disposition</a>
    </td>
    <td>Bibliotek</td>
    <td>Composer hjälper dig att deklarera, hantera och installera beroenden av PHP-projekt. Det ser till att du har rätt hög överallt.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/metadata-minifier">disposition/metadata-minifier</a>
    </td>
    <td>Bibliotek</td>
    <td>Liten verktygsbibliotek som hanterar miniatyrbilder och utbyggnad av metadata.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/pcre">disposition/pcre</a>
    </td>
    <td>Bibliotek</td>
    <td>PCRE-paketeringsbibliotek som erbjuder typsäkra preg_*-ersättningar.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/semver">disposition/server</a>
    </td>
    <td>Bibliotek</td>
    <td>Semversionsbibliotek som erbjuder verktyg, versionskontrollerad tolkning och validering.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/spdx-licenses">Composer/spdx-licenses</a>
    </td>
    <td>Bibliotek</td>
    <td>SPDX-licenslista och valideringsbibliotek.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/xdebug-handler">dispositör/xdebug-handler</a>
    </td>
    <td>Bibliotek</td>
    <td>Startar om en process utan Xdebug.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/doctrine/lexer">doctrine/lexer</a>
    </td>
    <td>Bibliotek</td>
    <td>PHP Doctrine Lexer-parserbibliotek som kan användas i uppifrån och ned, rekursiva fallparametrar.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/egulias/EmailValidator">egulias/email-validator</a>
    </td>
    <td>Bibliotek</td>
    <td>Ett bibliotek för validering av e-post mot flera RFC:er</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/elastic/elastic-transport-php">elastisk/transport</a>
    </td>
    <td>Bibliotek</td>
    <td>PHP-bibliotek för HTTP-transport för elastiska produkter</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/elastic/elasticsearch-php">elasticsearch/elasticsearch</a>
    </td>
    <td>Bibliotek</td>
    <td>PHP-klient för Elasticsearch</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/endroid/qr-code">endroid/qr-code</a>
    </td>
    <td>Bibliotek</td>
    <td>Endroid QR-kod</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ezimuel/guzzlestreams">ezimuel/guzzlestreams</a>
    </td>
    <td>Bibliotek</td>
    <td>Gbit guzzle/streams (övergiven) som ska användas med elasticsearch-php</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ezimuel/ringphp">ezimuel/ringphp</a>
    </td>
    <td>Bibliotek</td>
    <td>Gummigaffel/RingPHP (övergiven) som ska användas med elasticsearch-php</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/guzzle/guzzle">guzzlehttp/guzzle</a>
    </td>
    <td>Bibliotek</td>
    <td>Guzzle är ett PHP HTTP-klientbibliotek</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/guzzle/promises">guzzlehttp/promise</a>
    </td>
    <td>Bibliotek</td>
    <td>Bibliotek med löften om pussel</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/guzzle/psr7">guzzlehttp/psr7</a>
    </td>
    <td>Bibliotek</td>
    <td>Implementering av PSR-7-meddelanden som även innehåller vanliga verktygsmetoder</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/jsonrainbow/json-schema">justinrainbow/json-schema</a>
    </td>
    <td>Bibliotek</td>
    <td>Ett bibliotek som validerar ett json-schema.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/flysystem">Lag/flygsystem</a>
    </td>
    <td>Bibliotek</td>
    <td>Filarkiveringssammanfattning för PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/flysystem-aws-s3-v3">leag/flysystem-aws-s3-v3</a>
    </td>
    <td>Bibliotek</td>
    <td>AWS S3-filsystemadapter för flygsystem.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/flysystem-local">Lag/flysystem-local</a>
    </td>
    <td>Bibliotek</td>
    <td>Lokal filsystemadapter för flygsystemet.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/mime-type-detection">Identifiering av ligg/mime-typ</a>
    </td>
    <td>Bibliotek</td>
    <td>Mime-type detection for Flysystem</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/monolog">monolog/monolog</a>
    </td>
    <td>Bibliotek</td>
    <td>Skickar loggarna till filer, socketar, inkorgar, databaser och olika webbtjänster</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/jmespath/jmespath.php">mtdowling/jmespath.php</a>
    </td>
    <td>Bibliotek</td>
    <td>Ange deklarativt hur element ska extraheras från ett JSON-dokument</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/paragonie/constant_time_encoding">paragonie/constant_time_encoding</a>
    </td>
    <td>Bibliotek</td>
    <td>Konstanta implementeringar av RFC 4648-kodning (Base-64, Base-32, Base-16)</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/paragonie/random_compat">paragonie/random_compat</a>
    </td>
    <td>Bibliotek</td>
    <td>PHP 5.x-polyfill för random_bytes() och random_int() från PHP 7</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/MyIntervals/emogrifier">pelago/emogrifier</a>
    </td>
    <td>Bibliotek</td>
    <td>Konverterar CSS-format till infogade formatattribut i din HTML-kod</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-http/discovery">php-http/discovery</a>
    </td>
    <td>Composer-plugin</td>
    <td>Söker efter och installerar implementeringar av PSR-7, PSR-17, PSR-18 och HTTPlug</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-http/httplug">php-http/httplug</a>
    </td>
    <td>Bibliotek</td>
    <td>HTTPlug, HTTP-klientabstraktion för PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-http/promise">php-http/promise</a>
    </td>
    <td>Bibliotek</td>
    <td>Löfte som används för asynkrona HTTP-begäranden</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/PhpGt/CssXPath">phpgt/cssxpath</a>
    </td>
    <td>Bibliotek</td>
    <td>Konvertera CSS-väljare till XPath-frågor.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/PhpGt/Dom">phpgt/dom</a>
    </td>
    <td>Bibliotek</td>
    <td>Modern DOM API.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/PhpGt/PropFunc">phpgt/propfunc</a>
    </td>
    <td>Bibliotek</td>
    <td>Egenskapsåtkomst och mutatorfunktioner.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/phpseclib/mcrypt_compat">phpseclib/mcrypt_compat</a>
    </td>
    <td>Bibliotek</td>
    <td>PHP 5.x-8.x-polyfill för kryptering</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/phpseclib/phpseclib">phpseclib/phpseclib</a>
    </td>
    <td>Bibliotek</td>
    <td>PHP Secure Communications Library - Pure-PHP-implementeringar av RSA, AES, SSH2, SFTP, X.509 osv.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/cache">psr/cache</a>
    </td>
    <td>Bibliotek</td>
    <td>Gemensamt gränssnitt för att cacha bibliotek</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/clock">psr/clock</a>
    </td>
    <td>Bibliotek</td>
    <td>Gemensamt gränssnitt för att läsa klockan.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/container">psr/container</a>
    </td>
    <td>Bibliotek</td>
    <td>Gränssnitt för gemensam behållare (PHP FIG PSR-11)</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/event-dispatcher">psr/event-dispatcher</a>
    </td>
    <td>Bibliotek</td>
    <td>Standardgränssnitt för händelsehantering.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/http-client">psr/http-client</a>
    </td>
    <td>Bibliotek</td>
    <td>Gemensamt gränssnitt för HTTP-klienter</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/http-factory">psr/http-factory</a>
    </td>
    <td>Bibliotek</td>
    <td>PSR-17: Vanliga gränssnitt för PSR-7 HTTP-meddelandefabriker</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/http-message">psr/http-message</a>
    </td>
    <td>Bibliotek</td>
    <td>Gemensamt gränssnitt för HTTP-meddelanden</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/log">psr/log</a>
    </td>
    <td>Bibliotek</td>
    <td>Gemensamt gränssnitt för loggning av bibliotek</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ralouphie/getallheaders">ralouphie/getallheaders</a>
    </td>
    <td>Bibliotek</td>
    <td>En polyfyllning för getallheaders.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ramsey/collection">ramsey/collection</a>
    </td>
    <td>Bibliotek</td>
    <td>Ett PHP-bibliotek för att representera och ändra samlingar.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ramsey/uuid">ramsey/uuid</a>
    </td>
    <td>Bibliotek</td>
    <td>Ett PHP-bibliotek för generering och arbete med UUID (Universally Unique Identiters).</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/reactphp/promise">reagerar/utlovar</a>
    </td>
    <td>Bibliotek</td>
    <td>En lätt implementering av CommonJS Promises/A för PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/MyIntervals/PHP-CSS-Parser">sabberworm/php-css-parser</a>
    </td>
    <td>Bibliotek</td>
    <td>Parser for CSS Files written in PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/jsonlint">seld/jsonlint</a>
    </td>
    <td>Bibliotek</td>
    <td>JSON Linter</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/phar-utils">seld/phar-utils</a>
    </td>
    <td>Bibliotek</td>
    <td>Verktyg för PHAR-filformat, t.ex. när PHP hjälper dig</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/signal-handler">seld/signal-handler</a>
    </td>
    <td>Bibliotek</td>
    <td>Enkel, enkel signalhanterare som tyst misslyckas där signaler inte stöds för enkel plattformsoberoende utveckling</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Spomky-Labs/aes-key-wrap">spomky-labs/aes-key-wrap</a>
    </td>
    <td>Bibliotek</td>
    <td>AES Key Wrap for PHP.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Spomky-Labs/otphp">spomky-labs/otphp</a>
    </td>
    <td>Bibliotek</td>
    <td>Ett PHP-bibliotek för generering av engångslösenord enligt RFC 4226 (HOTP-algoritm) och RFC 6238 (TOTP-algoritm) som är kompatibelt med Google Authenticator</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Spomky-Labs/pki-framework">spomky-labs/pki-framework</a>
    </td>
    <td>Bibliotek</td>
    <td>Ett PHP-ramverk för hantering av infrastrukturer med publik nyckel. Det omfattar X.509-certifikat för offentlig nyckel, attributcertifikat, certifieringsbegäranden och validering av certifieringssökväg.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/config">symfony/config</a>
    </td>
    <td>Bibliotek</td>
    <td>Hjälper dig att hitta, ladda, kombinera, autofylla och validera konfigurationsvärden av alla slag</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/console">symbol/konsol</a>
    </td>
    <td>Bibliotek</td>
    <td>Förenklar skapandet av snygga och testbara kommandoradsgränssnitt</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/css-selector">symfony/css-selector</a>
    </td>
    <td>Bibliotek</td>
    <td>Konverterar CSS-väljare till XPath-uttryck</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/dependency-injection">symbol/beroendeinjicering</a>
    </td>
    <td>Bibliotek</td>
    <td>Används för att standardisera och centralisera det sätt på vilket objekt skapas i programmet</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/deprecation-contracts">symfony/deprecation-agreements</a>
    </td>
    <td>Bibliotek</td>
    <td>En allmän funktion och konvention som utlöser meddelanden om borttagning</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/error-handler">symfony/error-handler</a>
    </td>
    <td>Bibliotek</td>
    <td>Tillhandahåller verktyg för att hantera fel och underlätta felsökning av PHP-kod</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/event-dispatcher">symfony/event-dispatcher</a>
    </td>
    <td>Bibliotek</td>
    <td>Tillhandahåller verktyg som gör att programkomponenterna kan kommunicera med varandra genom att skicka händelser och lyssna på dem</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/event-dispatcher-contracts">symfony/event-dispatcher-agreements</a>
    </td>
    <td>Bibliotek</td>
    <td>Allmänna abstraktioner relaterade till skicka-händelse</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/filesystem">symfony/filesystem</a>
    </td>
    <td>Bibliotek</td>
    <td>Tillhandahåller grundläggande verktyg för filsystemet</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/finder">symfony/finder</a>
    </td>
    <td>Bibliotek</td>
    <td>Söker efter filer och kataloger via ett intuitivt flytande gränssnitt</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/http-client">symfony/http-client</a>
    </td>
    <td>Bibliotek</td>
    <td>Tillhandahåller kraftfulla metoder för att hämta HTTP-resurser synkront eller asynkront</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/http-client-contracts">symfony/http-client-agreements</a>
    </td>
    <td>Bibliotek</td>
    <td>Allmänna abstraktioner relaterade till HTTP-klienter</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/http-foundation">symfony/http-foundation</a>
    </td>
    <td>Bibliotek</td>
    <td>Definierar ett objektorienterat lager för HTTP-specifikationen</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/http-kernel">symfony/http-kernel</a>
    </td>
    <td>Bibliotek</td>
    <td>Tillhandahåller en strukturerad process för konvertering av en begäran till ett svar</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/intl">symfony/intl</a>
    </td>
    <td>Bibliotek</td>
    <td>Ger åtkomst till ICU-bibliotekets lokaliseringsdata</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/mailer">symfony/mailer</a>
    </td>
    <td>Bibliotek</td>
    <td>Hjälper dig att skicka e-post</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/mime">symfony/mime</a>
    </td>
    <td>Bibliotek</td>
    <td>Tillåter manipulering av MIME-meddelanden</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-ctype">symfony/polyfill-type</a>
    </td>
    <td>Bibliotek</td>
    <td>Symfonisk polyfyllning för typfunktioner</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-intl-grapheme">symfony/polyfill-intl-grapteme</a>
    </td>
    <td>Bibliotek</td>
    <td>Symfony polyfill for intl's grapheme_* functions</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-intl-idn">symfony/polyfill-intl-idn</a>
    </td>
    <td>Bibliotek</td>
    <td>Symfony polyfill for intl's id_to_ascii and id_to_utf8 functions</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-intl-normalizer">symfony/polyfill-intl-normalizer</a>
    </td>
    <td>Bibliotek</td>
    <td>Symfonisk polyfyllning för klassen Normalizer i AIR och relaterade funktioner</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-mbstring">symfony/polyfill-mbstring</a>
    </td>
    <td>Bibliotek</td>
    <td>Symfonisk polyfyllning för MbitString-tillägget</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php73">symfony/polyfill-php73</a>
    </td>
    <td>Bibliotek</td>
    <td>Symfonisk polyfill backporting vissa PHP 7.3+-funktioner ger lägre PHP-versioner</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php80">symfony/polyfill-php80</a>
    </td>
    <td>Bibliotek</td>
    <td>Symfonisk polyfill backporting vissa PHP 8.0+-funktioner till lägre PHP-versioner</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php81">symfony/polyfill-php81</a>
    </td>
    <td>Bibliotek</td>
    <td>Symfonisk polyfill backporterar vissa PHP 8.1+-funktioner till lägre PHP-versioner</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php82">symfony/polyfill-php82</a>
    </td>
    <td>Bibliotek</td>
    <td>Symfonisk polyfill backporting vissa PHP 8.2+-funktioner till lägre PHP-versioner</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php83">symfony/polyfill-php83</a>
    </td>
    <td>Bibliotek</td>
    <td>Symfonisk polyfill backporterar vissa PHP 8.3+-funktioner till lägre PHP-versioner</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/process">symfony/process</a>
    </td>
    <td>Bibliotek</td>
    <td>Kör kommandon i underprocesser</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/service-contracts">symfony/service-contract</a>
    </td>
    <td>Bibliotek</td>
    <td>Allmänna abstraktioner relaterade till skrivande tjänster</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/string">symbol/sträng</a>
    </td>
    <td>Bibliotek</td>
    <td>Ger ett objektorienterat API för strängar och hanterar byte, UTF-8-kodpunkter och grafemkluster på ett enhetligt sätt</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/var-dumper">symfony/var-dumper</a>
    </td>
    <td>Bibliotek</td>
    <td>Tillhandahåller mekanismer för att gå igenom valfri PHP-variabel</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/var-exporter">symfony/var-exporting</a>
    </td>
    <td>Bibliotek</td>
    <td>Tillåter export av serialiserbara PHP-datastrukturer till vanlig PHP-kod</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/yaml">symfony/yaml</a>
    </td>
    <td>Bibliotek</td>
    <td>Läser in och dumpar YAML-filer</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/web-token/jwt-framework">web-token/jwt-framework</a>
    </td>
    <td>Symfony-bundle</td>
    <td>JSON Object Signing and Encryption library for PHP and Symfony Bundle.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/webonyx/graphql-php">webonyx/graphql-php</a>
    </td>
    <td>Bibliotek</td>
    <td>En PHP-port för GraphQL referensimplementering</td>
  </tr>
  </tbody>
</table>

### OSL-3.0, AFL-3.0

<table>
  <thead>
    <tr>
      <th>Namn</th>
      <th>Typ</th>
      <th>Beskrivning</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      paypal/module-braintree-customer-balance
    </td>
    <td>Magento2-modul</td>
    <td>Ej tillämpligt</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree-present-card
    </td>
    <td>Magento2-modul</td>
    <td>Ej tillämpligt</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree-present-card-account
    </td>
    <td>Magento2-modul</td>
    <td>Ej tillämpligt</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree-present-wrapping
    </td>
    <td>Magento2-modul</td>
    <td>Ej tillämpligt</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree-graph-ql
    </td>
    <td>Magento2-modul</td>
    <td>Ej tillämpligt</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree-gain
    </td>
    <td>Magento2-modul</td>
    <td>Ej tillämpligt</td>
  </tr>
  </tbody>
</table>

### OSL-3.0

<table>
  <thead>
    <tr>
      <th>Namn</th>
      <th>Typ</th>
      <th>Beskrivning</th>
    </tr>
  </thead>
  <tbody>
  </tbody>
</table>

### PHP

<table>
  <thead>
    <tr>
      <th>Namn</th>
      <th>Typ</th>
      <th>Beskrivning</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/2tvenom/CBOREncode">2tvenom/cborencode</a>
    </td>
    <td>Bibliotek</td>
    <td>CBOR encoder for PHP</td>
  </tr>
  </tbody>
</table>

### egen

<table>
  <thead>
    <tr>
      <th>Namn</th>
      <th>Typ</th>
      <th>Beskrivning</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      paypal/module-braintree-core
    </td>
    <td>Magento2-modul</td>
    <td>Fork från modulen Magento Braintree 2.2.0 av Gene Commerce for PayPal.</td>
  </tr>
  </tbody>
</table>
