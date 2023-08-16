---
source-git-commit: e883ab0e6fca468bd3701e6789ac5132c7f1ee4d
workflow-type: tm+mt
source-wordcount: '2491'
ht-degree: 0%

---
# Magento Open Source-paket

<!-- The 'packages' variable contains the 'packages' node of the '_data/codebase/open-source/composer_lock_beta.json' file
 -->

<!-- The 'packages-dev' variable contains the 'packages-dev' node of the '_data/codebase/open-source/composer_lock_beta.json' file
 -->

<!-- The 'product' variable contains data of the 'magento/product-community-edition' package
 -->

<!-- The edition variable contains `open-source` value from the _data/names.yml file
 -->

Magento Open Source använder Composer för att hantera PHP-paket.

The `composer.json` filen deklarerar paketlistan, medan `composer.lock` filen lagrar en fullständig lista över de paket (en fullständig version av varje paket och dess beroenden) som används för att skapa en installation av Adobe Commerce eller Magento Open Source.

Följande referensdokumentation genereras från `composer.lock` och omfattar de paket som ingår i Magento Open Source 2.4.7-beta1.

## Beroenden

`magento/product-community-edition 2.4.7-beta1` har följande beroenden:

```config
adobe-commerce/adobe-ims-metapackage: ^2.2
adobe-commerce/os-extensions-metapackage: ~1.0
colinmollenhour/cache-backend-file: ^1.4
colinmollenhour/cache-backend-redis: ^1.14
colinmollenhour/credis: ^1.13
colinmollenhour/php-redis-session-abstract: ^1.5
composer/composer: ^2.0, !=2.2.16
doctrine/annotations: ^1.13
elasticsearch/elasticsearch: ~7.17.0 || ~8.5.0
ext-bcmath: *
ext-ctype: *
ext-curl: *
ext-dom: *
ext-gd: *
ext-hash: *
ext-iconv: *
ext-intl: *
ext-mbstring: *
ext-openssl: *
ext-pdo_mysql: *
ext-simplexml: *
ext-soap: *
ext-sodium: *
ext-xsl: *
ext-zip: *
ezyang/htmlpurifier: ^4.16
guzzlehttp/guzzle: ^7.5
laminas/laminas-captcha: ^2.12
laminas/laminas-code: ^4.5
laminas/laminas-db: ^2.15
laminas/laminas-di: ^3.7
laminas/laminas-escaper: ^2.10
laminas/laminas-eventmanager: ^3.5
laminas/laminas-feed: ^2.17
laminas/laminas-file: ^2.11
laminas/laminas-filter: ^2.17
laminas/laminas-http: ^2.15
laminas/laminas-i18n: ^2.17
laminas/laminas-mail: ^2.16
laminas/laminas-mime: ^2.9
laminas/laminas-modulemanager: ^2.11
laminas/laminas-mvc: ^3.3
laminas/laminas-oauth: ^2.4
laminas/laminas-permissions-acl: ^2.10
laminas/laminas-servicemanager: ^3.16
laminas/laminas-soap: ^2.10
laminas/laminas-stdlib: ^3.11
laminas/laminas-uri: ^2.9
laminas/laminas-validator: ^2.23
league/flysystem: ^2.4
league/flysystem-aws-s3-v3: ^2.4
lib-libxml: *
magento/adobe-stock-integration: 2.1.6-beta1
magento/composer: ^1.9.0
magento/composer-dependency-version-audit-plugin: ^0.1
magento/framework: 103.0.7-beta1
magento/framework-amqp: 100.4.5-beta1
magento/framework-bulk: 101.0.3-beta1
magento/framework-message-queue: 100.4.7-beta1
magento/inventory-metapackage: 1.2.7-beta1
magento/language-de_de: 100.4.0
magento/language-en_us: 100.4.0
magento/language-es_es: 100.4.0
magento/language-fr_fr: 100.4.0
magento/language-nl_nl: 100.4.0
magento/language-pt_br: 100.4.0
magento/language-zh_hans_cn: 100.4.0
magento/magento-composer-installer: >=0.4.0
magento/magento2-base: 2.4.7-beta1
magento/module-admin-analytics: 100.4.6-beta1
magento/module-admin-notification: 100.4.6-beta1
magento/module-advanced-pricing-import-export: 100.4.7-beta1
magento/module-advanced-search: 100.4.5-beta1
magento/module-amqp: 100.4.4-beta1
magento/module-analytics: 100.4.7-beta1
magento/module-async-config: 100.4.0-beta1
magento/module-asynchronous-operations: 100.4.7-beta1
magento/module-authorization: 100.4.7-beta1
magento/module-aws-s3: 100.4.5-beta1
magento/module-backend: 102.0.7-beta1
magento/module-backup: 100.4.7-beta1
magento/module-bundle: 101.0.7-beta1
magento/module-bundle-graph-ql: 100.4.7-beta1
magento/module-bundle-import-export: 100.4.6-beta1
magento/module-cache-invalidate: 100.4.5-beta1
magento/module-captcha: 100.4.7-beta1
magento/module-cardinal-commerce: 100.4.5-beta1
magento/module-catalog: 104.0.7-beta1
magento/module-catalog-analytics: 100.4.4-beta1
magento/module-catalog-cms-graph-ql: 100.4.3-beta1
magento/module-catalog-customer-graph-ql: 100.4.6-beta1
magento/module-catalog-graph-ql: 100.4.7-beta1
magento/module-catalog-import-export: 101.1.7-beta1
magento/module-catalog-inventory: 100.4.7-beta1
magento/module-catalog-inventory-graph-ql: 100.4.4-beta1
magento/module-catalog-rule: 101.2.7-beta1
magento/module-catalog-rule-configurable: 100.4.6-beta1
magento/module-catalog-rule-graph-ql: 100.4.4-beta1
magento/module-catalog-search: 102.0.7-beta1
magento/module-catalog-url-rewrite: 100.4.7-beta1
magento/module-catalog-url-rewrite-graph-ql: 100.4.5-beta1
magento/module-catalog-widget: 100.4.7-beta1
magento/module-checkout: 100.4.7-beta1
magento/module-checkout-agreements: 100.4.6-beta1
magento/module-checkout-agreements-graph-ql: 100.4.2
magento/module-cms: 104.0.7-beta1
magento/module-cms-graph-ql: 100.4.4-beta1
magento/module-cms-url-rewrite: 100.4.6-beta1
magento/module-cms-url-rewrite-graph-ql: 100.4.4
magento/module-compare-list-graph-ql: 100.4.3-beta1
magento/module-config: 101.2.7-beta1
magento/module-configurable-import-export: 100.4.5-beta1
magento/module-configurable-product: 100.4.7-beta1
magento/module-configurable-product-graph-ql: 100.4.7-beta1
magento/module-configurable-product-sales: 100.4.4-beta1
magento/module-contact: 100.4.6-beta1
magento/module-contact-graph-ql: 100.4.0-beta1
magento/module-cookie: 100.4.7-beta1
magento/module-cron: 100.4.7-beta1
magento/module-csp: 100.4.6-beta1
magento/module-currency-symbol: 100.4.5-beta1
magento/module-customer: 103.0.7-beta1
magento/module-customer-analytics: 100.4.4-beta1
magento/module-customer-downloadable-graph-ql: 100.4.3-beta1
magento/module-customer-graph-ql: 100.4.7-beta1
magento/module-customer-import-export: 100.4.7-beta1
magento/module-deploy: 100.4.7-beta1
magento/module-developer: 100.4.7-beta1
magento/module-dhl: 100.4.5
magento/module-directory: 100.4.7-beta1
magento/module-directory-graph-ql: 100.4.5-beta1
magento/module-downloadable: 100.4.7-beta1
magento/module-downloadable-graph-ql: 100.4.6
magento/module-downloadable-import-export: 100.4.5
magento/module-eav: 102.1.7-beta1
magento/module-eav-graph-ql: 100.4.4-beta1
magento/module-elasticsearch: 101.0.7-beta1
magento/module-elasticsearch-7: 100.4.7-beta1
magento/module-email: 101.1.7-beta1
magento/module-encryption-key: 100.4.5-beta1
magento/module-fedex: 100.4.5-beta1
magento/module-gift-message: 100.4.6-beta1
magento/module-gift-message-graph-ql: 100.4.5-beta1
magento/module-google-adwords: 100.4.4-beta1
magento/module-google-analytics: 100.4.3-beta1
magento/module-google-gtag: 100.4.2-beta1
magento/module-google-optimizer: 100.4.6-beta1
magento/module-graph-ql: 100.4.7-beta1
magento/module-graph-ql-cache: 100.4.4-beta1
magento/module-grouped-catalog-inventory: 100.4.4-beta1
magento/module-grouped-import-export: 100.4.5-beta1
magento/module-grouped-product: 100.4.7-beta1
magento/module-grouped-product-graph-ql: 100.4.7-beta1
magento/module-import-export: 101.0.7-beta1
magento/module-indexer: 100.4.7-beta1
magento/module-instant-purchase: 100.4.6-beta1
magento/module-integration: 100.4.7-beta1
magento/module-jwt-framework-adapter: 100.4.2
magento/module-jwt-user-token: 100.4.1
magento/module-layered-navigation: 100.4.7-beta1
magento/module-login-as-customer: 100.4.7-beta1
magento/module-login-as-customer-admin-ui: 100.4.7-beta1
magento/module-login-as-customer-api: 100.4.6-beta1
magento/module-login-as-customer-assistance: 100.4.6-beta1
magento/module-login-as-customer-frontend-ui: 100.4.5
magento/module-login-as-customer-graph-ql: 100.4.4-beta1
magento/module-login-as-customer-log: 100.4.5-beta1
magento/module-login-as-customer-page-cache: 100.4.5
magento/module-login-as-customer-quote: 100.4.4
magento/module-login-as-customer-sales: 100.4.5
magento/module-marketplace: 100.4.5-beta1
magento/module-media-content: 100.4.5-beta1
magento/module-media-content-api: 100.4.6-beta1
magento/module-media-content-catalog: 100.4.5-beta1
magento/module-media-content-cms: 100.4.5-beta1
magento/module-media-content-synchronization: 100.4.6-beta1
magento/module-media-content-synchronization-api: 100.4.5-beta1
magento/module-media-content-synchronization-catalog: 100.4.4-beta1
magento/module-media-content-synchronization-cms: 100.4.4-beta1
magento/module-media-gallery: 100.4.6-beta1
magento/module-media-gallery-api: 101.0.6-beta1
magento/module-media-gallery-catalog: 100.4.4-beta1
magento/module-media-gallery-catalog-integration: 100.4.4-beta1
magento/module-media-gallery-catalog-ui: 100.4.4-beta1
magento/module-media-gallery-cms-ui: 100.4.4-beta1
magento/module-media-gallery-integration: 100.4.6-beta1
magento/module-media-gallery-metadata: 100.4.5-beta1
magento/module-media-gallery-metadata-api: 100.4.4-beta1
magento/module-media-gallery-renditions: 100.4.5-beta1
magento/module-media-gallery-renditions-api: 100.4.4-beta1
magento/module-media-gallery-synchronization: 100.4.6-beta1
magento/module-media-gallery-synchronization-api: 100.4.5-beta1
magento/module-media-gallery-synchronization-metadata: 100.4.3-beta1
magento/module-media-gallery-ui: 100.4.6-beta1
magento/module-media-gallery-ui-api: 100.4.5-beta1
magento/module-media-storage: 100.4.6-beta1
magento/module-message-queue: 100.4.7-beta1
magento/module-msrp: 100.4.6-beta1
magento/module-msrp-configurable-product: 100.4.4-beta1
magento/module-msrp-grouped-product: 100.4.4-beta1
magento/module-multishipping: 100.4.7-beta1
magento/module-mysql-mq: 100.4.5-beta1
magento/module-new-relic-reporting: 100.4.5-beta1
magento/module-newsletter: 100.4.7-beta1
magento/module-newsletter-graph-ql: 100.4.4-beta1
magento/module-offline-payments: 100.4.5-beta1
magento/module-offline-shipping: 100.4.6-beta1
magento/module-open-search: 100.4.1-beta1
magento/module-page-cache: 100.4.7-beta1
magento/module-payment: 100.4.7-beta1
magento/module-payment-graph-ql: 100.4.1
magento/module-paypal: 101.0.7-beta1
magento/module-paypal-captcha: 100.4.4-beta1
magento/module-paypal-graph-ql: 100.4.4
magento/module-persistent: 100.4.7-beta1
magento/module-product-alert: 100.4.6-beta1
magento/module-product-video: 100.4.7-beta1
magento/module-quote: 101.2.7-beta1
magento/module-quote-analytics: 100.4.6-beta1
magento/module-quote-bundle-options: 100.4.3-beta1
magento/module-quote-configurable-options: 100.4.3-beta1
magento/module-quote-downloadable-links: 100.4.3-beta1
magento/module-quote-graph-ql: 100.4.7-beta1
magento/module-related-product-graph-ql: 100.4.4-beta1
magento/module-release-notification: 100.4.5-beta1
magento/module-remote-storage: 100.4.5-beta1
magento/module-reports: 100.4.7-beta1
magento/module-require-js: 100.4.3-beta1
magento/module-review: 100.4.7-beta1
magento/module-review-analytics: 100.4.4-beta1
magento/module-review-graph-ql: 100.4.3-beta1
magento/module-robots: 101.1.3-beta1
magento/module-rss: 100.4.4
magento/module-rule: 100.4.5
magento/module-sales: 103.0.7-beta1
magento/module-sales-analytics: 100.4.4-beta1
magento/module-sales-graph-ql: 100.4.6
magento/module-sales-inventory: 100.4.3
magento/module-sales-rule: 101.2.7-beta1
magento/module-sales-sequence: 100.4.4-beta1
magento/module-sample-data: 100.4.5-beta1
magento/module-search: 101.1.7-beta1
magento/module-security: 100.4.7-beta1
magento/module-send-friend: 100.4.5-beta1
magento/module-send-friend-graph-ql: 100.4.2
magento/module-shipping: 100.4.7-beta1
magento/module-sitemap: 100.4.6-beta1
magento/module-store: 101.1.7-beta1
magento/module-store-graph-ql: 100.4.5-beta1
magento/module-swagger: 100.4.6-beta1
magento/module-swagger-webapi: 100.4.3-beta1
magento/module-swagger-webapi-async: 100.4.3-beta1
magento/module-swatches: 100.4.7-beta1
magento/module-swatches-graph-ql: 100.4.4
magento/module-swatches-layered-navigation: 100.4.3-beta1
magento/module-tax: 100.4.7-beta1
magento/module-tax-graph-ql: 100.4.2
magento/module-tax-import-export: 100.4.6-beta1
magento/module-theme: 101.1.7-beta1
magento/module-theme-graph-ql: 100.4.3
magento/module-translation: 100.4.7-beta1
magento/module-ui: 101.2.7-beta1
magento/module-ups: 100.4.7-beta1
magento/module-url-rewrite: 102.0.6-beta1
magento/module-url-rewrite-graph-ql: 100.4.6-beta1
magento/module-user: 101.2.7-beta1
magento/module-usps: 100.4.6-beta1
magento/module-variable: 100.4.5-beta1
magento/module-vault: 101.2.7-beta1
magento/module-vault-graph-ql: 100.4.2
magento/module-version: 100.4.3
magento/module-webapi: 100.4.6-beta1
magento/module-webapi-async: 100.4.5-beta1
magento/module-webapi-security: 100.4.4-beta1
magento/module-weee: 100.4.7-beta1
magento/module-weee-graph-ql: 100.4.4-beta1
magento/module-widget: 101.2.7-beta1
magento/module-wishlist: 101.2.7-beta1
magento/module-wishlist-analytics: 100.4.5-beta1
magento/module-wishlist-graph-ql: 100.4.7-beta1
magento/page-builder: 1.7.4-beta1
magento/security-package: 1.1.6-beta1
magento/theme-adminhtml-backend: 100.4.6
magento/theme-frontend-blank: 100.4.7-beta1
magento/theme-frontend-luma: 100.4.7-beta1
magento/zend-cache: ^1.16
magento/zend-db: ^1.16
magento/zend-pdf: ^1.16
monolog/monolog: ^2.7
opensearch-project/opensearch-php: ^1.0 || ^2.0, <2.0.1
pelago/emogrifier: ^7.0
php: ~8.1.0||~8.2.0
php-amqplib/php-amqplib: ^3.2
phpseclib/mcrypt_compat: ^2.0
phpseclib/phpseclib: ^3.0
ramsey/uuid: ^4.2
symfony/console: ^5.4
symfony/intl: ^5.4
symfony/process: ^5.4
symfony/string: ^5.4
tedivm/jshrink: ^1.4
temando/module-shipping: 2.0.0
tubalmartin/cssmin: ^4.1
web-token/jwt-framework: ^3.1
webonyx/graphql-php: ^15.0
wikimedia/less.php: ^3.2
```

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
      elasticsearch/elasticsearch
    </td>
    <td>bibliotek</td>
    <td>PHP-klient för Elasticsearch</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/opensearch-project/opensearch-php.git">opensearch-project/opensearch-php</a>
    </td>
    <td>bibliotek</td>
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
      <a href="https://github.com/adobe/stock-api-libphp.git">astock stock-api-libphp</a>
    </td>
    <td>bibliotek</td>
    <td>Adobe Stock API-bibliotek</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/awslabs/aws-crt-php.git">aws/aws-crt-php</a>
    </td>
    <td>bibliotek</td>
    <td>AWS Common Runtime for PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/aws/aws-sdk-php.git">aws/aws-sdk-php</a>
    </td>
    <td>bibliotek</td>
    <td>AWS SDK for PHP - Använd Amazon Web Services i PHP-projekt</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree
    </td>
    <td>metapackage</td>
    <td>Braintree Magento</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/wikimedia/less.php.git">wikimedia/less.php</a>
    </td>
    <td>bibliotek</td>
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
      <a href="https://github.com/Bacon/BaconQrCode.git">bacon/bacon-qr-code</a>
    </td>
    <td>bibliotek</td>
    <td>BaconQrCode är en QR-kodgenerator för PHP.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/beberlei/assert.git">beberlei/assert</a>
    </td>
    <td>bibliotek</td>
    <td>Tunt bekräftelsebibliotek för indatavalidering i affärsmodeller.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/DASPRiD/Enum.git">dasprid/enum</a>
    </td>
    <td>bibliotek</td>
    <td>PHP 7.1 enum implementation</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/webimpress/safe-writer.git">webimpress/safe-writer</a>
    </td>
    <td>bibliotek</td>
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
      <a href="https://github.com/colinmollenhour/Cm_Cache_Backend_File.git">colinblöenhour/cache-backend-file</a>
    </td>
    <td>magento-module</td>
    <td>Zend_Cache_Backend_File-serverdelen har mycket dålig prestanda för att rensa med taggar, vilket gör den oanvändbar när antalet cachelagrade objekt ökar. Den här serverdelen gör många ändringar, vilket ger en rejäl prestandaökning, särskilt för tagghantering.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/colinmollenhour/php-redis-session-abstract.git">colinblöenhour/php-redis-session-abstract</a>
    </td>
    <td>bibliotek</td>
    <td>En Redis-baserad sessionshanterare med optimistisk låsning</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/firebase/php-jwt.git">firebase/php-jwt</a>
    </td>
    <td>bibliotek</td>
    <td>Ett enkelt bibliotek för kodning och avkodning av JSON Web Tokens (JWT) i PHP. Ska överensstämma med den aktuella specifikationen.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/google/recaptcha.git">google/recaptcha</a>
    </td>
    <td>bibliotek</td>
    <td>Klientbibliotek för reCAPTCHA, en kostnadsfri tjänst som skyddar webbplatser från skräppost och missbruk.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-captcha.git">laminas/laminas-captcha</a>
    </td>
    <td>bibliotek</td>
    <td>Generera och validera CAPTCHA med Figlets, images, ReCaptcha med flera</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-code.git">laminas/laminas-code</a>
    </td>
    <td>bibliotek</td>
    <td>Tillägg till API:t för PHP-reflektion, statisk kodskanning och kodgenerering</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-config.git">laminas/laminas-config</a>
    </td>
    <td>bibliotek</td>
    <td>innehåller ett kapslat objektegenskapsbaserat användargränssnitt för åtkomst av konfigurationsdata i programkoden</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-crypt.git">laminas/laminas-crypt</a>
    </td>
    <td>bibliotek</td>
    <td>Kraftfulla krypteringsverktyg och lösenordshash</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-db.git">laminas/laminas-db</a>
    </td>
    <td>bibliotek</td>
    <td>Databasförkortningslager, SQL-förkortning, resultatuppsättningsabstraktion och implementeringar av RowDataGateway och TableDataGateway</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-di.git">laminas/laminas-di</a>
    </td>
    <td>bibliotek</td>
    <td>Automatisk beroendeinjektion för PSR-11-behållare</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-escaper.git">laminas/laminas-escape</a>
    </td>
    <td>bibliotek</td>
    <td>Undvik säkert HTML, HTML, JavaScript, CSS och URL:er</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-eventmanager.git">laminas/laminas-eventmanager</a>
    </td>
    <td>bibliotek</td>
    <td>Utlös och lyssna på händelser i ett PHP-program</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-feed.git">laminas/laminas-feed</a>
    </td>
    <td>bibliotek</td>
    <td>innehåller funktioner för att skapa och använda RSS- och Atom-flöden</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-file.git">laminas/laminas-file</a>
    </td>
    <td>bibliotek</td>
    <td>Hitta PHP-klassfiler</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-filter.git">laminas/laminas-filter</a>
    </td>
    <td>bibliotek</td>
    <td>Filtrera och normalisera data och filer programmatiskt</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-http.git">laminas/laminas-http</a>
    </td>
    <td>bibliotek</td>
    <td>Ger ett enkelt gränssnitt för att utföra HTTP-begäranden (Hyper-Text Transfer Protocol)</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-i18n.git">laminas/laminas-i18n</a>
    </td>
    <td>bibliotek</td>
    <td>Ange översättningar för programmet och filtrera och validera internationella värden</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-json.git">laminas/laminas-json</a>
    </td>
    <td>bibliotek</td>
    <td>erbjuder bekväma metoder för att serialisera inbyggda PHP till JSON och avkoda JSON till inbyggda PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-loader.git">laminas/laminas-loader</a>
    </td>
    <td>bibliotek</td>
    <td>Inläsningsstrategier för automatisk inläsning och plugin-program</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-mail.git">laminas/laminas-mail</a>
    </td>
    <td>bibliotek</td>
    <td>Ger generaliserad funktionalitet för att sammanställa och skicka både text och MIME-kompatibla e-postmeddelanden i flera delar</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-math.git">laminas/laminas-math</a>
    </td>
    <td>bibliotek</td>
    <td>Skapa kryptografiskt säkra pseudoslumpmässiga siffror och hantera stora heltal</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-mime.git">laminas/laminas-mime</a>
    </td>
    <td>bibliotek</td>
    <td>Skapa och analysera MIME-meddelanden och -delar</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-modulemanager.git">laminas/laminas-modulemanager</a>
    </td>
    <td>bibliotek</td>
    <td>Modulärt programsystem för laminas-mvc-program</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-mvc.git">laminas/laminas-mvc</a>
    </td>
    <td>bibliotek</td>
    <td>Laminas händelsestyrda MVC-lager, inklusive MVC-program, styrenheter och plugin-program</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-oauth.git">laminas/laminas-oauth</a>
    </td>
    <td>bibliotek</td>
    <td></td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-permissions-acl.git">laminas/laminas-permissions-acl</a>
    </td>
    <td>bibliotek</td>
    <td>Tillhandahåller en enkel och flexibel ACL-implementering (access control list) för behörighetshantering</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-recaptcha.git">laminas/laminas-recaptcha</a>
    </td>
    <td>bibliotek</td>
    <td>OOP-wrapper för ReCaptcha-webbtjänsten</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-router.git">laminas/laminas-router</a>
    </td>
    <td>bibliotek</td>
    <td>Flexibelt routningssystem för HTTP- och konsolapplikationer</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-server.git">laminas/laminas-server</a>
    </td>
    <td>bibliotek</td>
    <td>Skapa reflektionsbaserade RPC-servrar</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-servicemanager.git">laminas/laminas-servicemanager</a>
    </td>
    <td>bibliotek</td>
    <td>Behållare för fabriksstyrd beroendeinjektion</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-session.git">laminas/laminas-session</a>
    </td>
    <td>bibliotek</td>
    <td>Objektorienterat gränssnitt för PHP-sessioner och -lagring</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-soap.git">laminas/laminas-soap</a>
    </td>
    <td>bibliotek</td>
    <td></td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-stdlib.git">laminas/laminas-stdlib</a>
    </td>
    <td>bibliotek</td>
    <td>SPL-tillägg, matrisverktyg, felhanterare med mera</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-text.git">laminas/laminas-text</a>
    </td>
    <td>bibliotek</td>
    <td>Skapa FIGlets och textbaserade tabeller</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-uri.git">laminas/laminas-uri</a>
    </td>
    <td>bibliotek</td>
    <td>En komponent som underlättar manipulering och validering av URI (Uniform Resource Identifiers)</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-validator.git">laminas/laminas-validator</a>
    </td>
    <td>bibliotek</td>
    <td>Valideringsklasser för ett stort antal domäner och möjlighet att kedja validerare för att skapa komplexa valideringskriterier</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-view.git">laminas/laminas-view</a>
    </td>
    <td>bibliotek</td>
    <td>Flexibla visningslager med stöd för flera visningslager, stödfunktioner med mera</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-zendframework-bridge.git">laminas/laminas-zendframework-bridge</a>
    </td>
    <td>bibliotek</td>
    <td>Alias för äldre ZF-klassnamn till motsvarande Laminas Project-värden.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/nikic/PHP-Parser.git">nikic/php-parser</a>
    </td>
    <td>bibliotek</td>
    <td>En PHP-parser skriven i PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/tedious/JShrink.git">tedivm/jcrink</a>
    </td>
    <td>bibliotek</td>
    <td>Javascript-minifier inbyggd i PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/tubalmartin/YUI-CSS-compressor-PHP-port.git">tubalmartin/cssmin</a>
    </td>
    <td>bibliotek</td>
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
      <a href="https://github.com/colinmollenhour/Cm_Cache_Backend_Redis.git">colinblöenhour/cache-backend-redis</a>
    </td>
    <td>magento-module</td>
    <td>Zend_Cache backend använder Redis med fullständigt stöd för taggar.</td>
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
      <a href="https://github.com/ezyang/htmlpurifier.git">ezyang/htmlpurifier</a>
    </td>
    <td>bibliotek</td>
    <td>Standardkompatibelt HTML-filter skrivet i PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-amqplib/php-amqplib.git">php-amqplib/php-amqplib</a>
    </td>
    <td>bibliotek</td>
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
      <a href="https://github.com/braintree/braintree_php.git">braintree/braintree_php</a>
    </td>
    <td>bibliotek</td>
    <td>Braintree PHP-klientbibliotek</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/brick/math.git">tegel/matte</a>
    </td>
    <td>bibliotek</td>
    <td>Arbitrary-precision aritmetic library</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/brick/varexporter.git">tegelsten/variexportör</a>
    </td>
    <td>bibliotek</td>
    <td>Ett kraftfullt alternativ till var_export(), som kan exportera stängningar och objekt utan __set_state()</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ChristianRiesen/base32.git">Christian-riesen/base32</a>
    </td>
    <td>bibliotek</td>
    <td>Base32-kodare/avkodare enligt RFC 4648</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/colinmollenhour/credis.git">colinblöenhour/credis</a>
    </td>
    <td>bibliotek</td>
    <td>Credis är ett lättviktsgränssnitt för Redis nyckelvärdenhet som omsluter phpredis-biblioteket när det är tillgängligt för bättre prestanda.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/ca-bundle.git">disposition/ca-bundle</a>
    </td>
    <td>bibliotek</td>
    <td>Gör att du kan hitta en sökväg till systemets CA-paket och inkluderar en reservanslutning till Mozilla CA-paketet.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/class-map-generator.git">dispositör/klass-map-generator</a>
    </td>
    <td>bibliotek</td>
    <td>Verktyg för att skanna PHP-kod och generera klasskartor.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/composer.git">disposition</a>
    </td>
    <td>bibliotek</td>
    <td>Composer hjälper dig att deklarera, hantera och installera beroenden av PHP-projekt. Det ser till att du har rätt hög överallt.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/metadata-minifier.git">disposition/metadata-minifier</a>
    </td>
    <td>bibliotek</td>
    <td>Liten verktygsbibliotek som hanterar miniatyrbilder och utbyggnad av metadata.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/pcre.git">disposition/pcre</a>
    </td>
    <td>bibliotek</td>
    <td>PCRE-paketeringsbibliotek som erbjuder typsäkra preg_*-ersättningar.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/semver.git">disposition/server</a>
    </td>
    <td>bibliotek</td>
    <td>Semversionsbibliotek som erbjuder verktyg, versionskontrollerad tolkning och validering.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/spdx-licenses.git">disposition/spdx-licenses</a>
    </td>
    <td>bibliotek</td>
    <td>SPDX-licenslista och valideringsbibliotek.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/xdebug-handler.git">disposition/xdebug-handler</a>
    </td>
    <td>bibliotek</td>
    <td>Startar om en process utan Xdebug.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/doctrine/annotations.git">doktrin/anteckningar</a>
    </td>
    <td>bibliotek</td>
    <td>Dokumentblockanteckningsparser</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/doctrine/deprecations.git">doktrin/borttagning</a>
    </td>
    <td>bibliotek</td>
    <td>Ett litet lager ovanpå trigger_error(E_USER_DEPRECATED) eller PSR-3-loggning med alternativ för att inaktivera alla borttagningar eller selektivt för paket.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/doctrine/lexer.git">doctrine/lexer</a>
    </td>
    <td>bibliotek</td>
    <td>PHP Doctrine Lexer-parserbibliotek som kan användas i uppifrån och ned, rekursiva fallparametrar.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/endroid/qr-code.git">endroid/qr-code</a>
    </td>
    <td>bibliotek</td>
    <td>Endroid QR-kod</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ezimuel/guzzlestreams.git">ezimuel/guzzlestreams</a>
    </td>
    <td>bibliotek</td>
    <td>Gbit guzzle/streams (övergiven) som ska användas med elasticsearch-php</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ezimuel/ringphp.git">ezimuel/ringphp</a>
    </td>
    <td>bibliotek</td>
    <td>Gummigaffel/RingPHP (övergiven) som ska användas med elasticsearch-php</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/guzzle/guzzle.git">guzzlehttp/guzzle</a>
    </td>
    <td>bibliotek</td>
    <td>Guzzle är ett PHP HTTP-klientbibliotek</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/guzzle/promises.git">guzzlehttp/promise</a>
    </td>
    <td>bibliotek</td>
    <td>Bibliotek med löften om pussel</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/guzzle/psr7.git">guzzlehttp/psr7</a>
    </td>
    <td>bibliotek</td>
    <td>Implementering av PSR-7-meddelanden som även innehåller vanliga verktygsmetoder</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/justinrainbow/json-schema.git">justinrainbow/json-schema</a>
    </td>
    <td>bibliotek</td>
    <td>Ett bibliotek som validerar ett json-schema.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/flysystem.git">guru/flygsystem</a>
    </td>
    <td>bibliotek</td>
    <td>Filarkiveringssammanfattning för PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/flysystem-aws-s3-v3.git">leag/flysystem-aws-s3-v3</a>
    </td>
    <td>bibliotek</td>
    <td>AWS S3-filsystemadapter för flygsystem.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/mime-type-detection.git">Detektering av ligans/mime-typ</a>
    </td>
    <td>bibliotek</td>
    <td>Mime-type detection for Flysystem</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/monolog.git">monolog/monolog</a>
    </td>
    <td>bibliotek</td>
    <td>Skickar loggarna till filer, socketar, inkorgar, databaser och olika webbtjänster</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/jmespath/jmespath.php.git">mtdowling/jmespath.php</a>
    </td>
    <td>bibliotek</td>
    <td>Ange deklarativt hur element ska extraheras från ett JSON-dokument</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/paragonie/constant_time_encoding.git">paragonie/constant_time_encoding</a>
    </td>
    <td>bibliotek</td>
    <td>Konstanta implementeringar av RFC 4648-kodning (Base-64, Base-32, Base-16)</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/paragonie/random_compat.git">paragonie/random_compat</a>
    </td>
    <td>bibliotek</td>
    <td>PHP 5.x-polyfill för random_bytes() och random_int() från PHP 7</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/MyIntervals/emogrifier.git">pelago/reliefer</a>
    </td>
    <td>bibliotek</td>
    <td>Konverterar CSS-format till textbundna formatattribut i HTML-koden</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/PhpGt/CssXPath.git">phpgt/cssxpath</a>
    </td>
    <td>bibliotek</td>
    <td>Konvertera CSS-väljare till XPath-frågor.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/PhpGt/Dom.git">phpgt/dom</a>
    </td>
    <td>bibliotek</td>
    <td>Det moderna DOM API:t för PHP-projekt.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/phpseclib/mcrypt_compat.git">phpseclib/mcrypt_compat</a>
    </td>
    <td>bibliotek</td>
    <td>PHP 5.x-8.x-polyfill för kryptering</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/phpseclib/phpseclib.git">phpseclib/phpseclib</a>
    </td>
    <td>bibliotek</td>
    <td>PHP Secure Communications Library - Pure-PHP-implementeringar av RSA, AES, SSH2, SFTP, X.509 osv.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/cache.git">psr/cache</a>
    </td>
    <td>bibliotek</td>
    <td>Gemensamt gränssnitt för att cacha bibliotek</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/clock.git">psr/klocka</a>
    </td>
    <td>bibliotek</td>
    <td>Gemensamt gränssnitt för att läsa klockan.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/container.git">psr/container</a>
    </td>
    <td>bibliotek</td>
    <td>Gränssnitt för gemensam behållare (PHP FIG PSR-11)</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/event-dispatcher.git">psr/event-dispatcher</a>
    </td>
    <td>bibliotek</td>
    <td>Standardgränssnitt för händelsehantering.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/http-client.git">psr/http-client</a>
    </td>
    <td>bibliotek</td>
    <td>Gemensamt gränssnitt för HTTP-klienter</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/http-factory.git">psr/http-factory</a>
    </td>
    <td>bibliotek</td>
    <td>Gemensamma gränssnitt för PSR-7 HTTP-meddelandefabriker</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/http-message.git">psr/http-message</a>
    </td>
    <td>bibliotek</td>
    <td>Gemensamt gränssnitt för HTTP-meddelanden</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/log.git">psr/log</a>
    </td>
    <td>bibliotek</td>
    <td>Gemensamt gränssnitt för loggning av bibliotek</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ralouphie/getallheaders.git">ralouphie/getallheaders</a>
    </td>
    <td>bibliotek</td>
    <td>En polyfyllning för getallheaders.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ramsey/collection.git">ramsey/collection</a>
    </td>
    <td>bibliotek</td>
    <td>Ett PHP-bibliotek för att representera och ändra samlingar.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ramsey/uuid.git">ramsey/uuid</a>
    </td>
    <td>bibliotek</td>
    <td>Ett PHP-bibliotek för generering och arbete med UUID (Universally Unique Identiters).</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/reactphp/promise.git">reagera/lova</a>
    </td>
    <td>bibliotek</td>
    <td>En lätt implementering av CommonJS Promises/A för PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/sabberworm/PHP-CSS-Parser.git">sabberworm/php-css-parser</a>
    </td>
    <td>bibliotek</td>
    <td>Parser for CSS Files written in PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/jsonlint.git">seld/jsonlint</a>
    </td>
    <td>bibliotek</td>
    <td>JSON Linter</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/phar-utils.git">seld/phar-utils</a>
    </td>
    <td>bibliotek</td>
    <td>Verktyg för PHAR-filformat, t.ex. när PHP hjälper dig</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/signal-handler.git">seld/signal-handler</a>
    </td>
    <td>bibliotek</td>
    <td>Enkel, enkel signalhanterare som tyst misslyckas där signaler inte stöds för enkel plattformsoberoende utveckling</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Spomky-Labs/aes-key-wrap.git">spomky-labs/aes-key-wrap</a>
    </td>
    <td>bibliotek</td>
    <td>AES Key Wrap for PHP.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Spomky-Labs/otphp.git">spomky-labs/otphp</a>
    </td>
    <td>bibliotek</td>
    <td>Ett PHP-bibliotek för generering av engångslösenord enligt RFC 4226 (HOTP-algoritm) och RFC 6238 (TOTP-algoritm) som är kompatibelt med Google Authenticator</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Spomky-Labs/pki-framework.git">spomky-labs/pki-framework</a>
    </td>
    <td>bibliotek</td>
    <td>Ett PHP-ramverk för hantering av infrastrukturer med publik nyckel. Det omfattar X.509-certifikat för offentlig nyckel, attributcertifikat, certifieringsbegäranden och validering av certifieringssökväg.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/config.git">symfony/config</a>
    </td>
    <td>bibliotek</td>
    <td>Hjälper dig att hitta, ladda, kombinera, autofylla och validera konfigurationsvärden av alla slag</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/console.git">symfony/console</a>
    </td>
    <td>bibliotek</td>
    <td>Förenklar skapandet av snygga och testbara kommandoradsgränssnitt</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/css-selector.git">symfony/css-selector</a>
    </td>
    <td>bibliotek</td>
    <td>Konverterar CSS-väljare till XPath-uttryck</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/dependency-injection.git">symfoni/beroendeinjicering</a>
    </td>
    <td>bibliotek</td>
    <td>Används för att standardisera och centralisera det sätt på vilket objekt skapas i programmet</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/deprecation-contracts.git">symfoni/utfasningsavtal</a>
    </td>
    <td>bibliotek</td>
    <td>En allmän funktion och konvention som utlöser meddelanden om borttagning</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/error-handler.git">symfony/error-handler</a>
    </td>
    <td>bibliotek</td>
    <td>Tillhandahåller verktyg för att hantera fel och underlätta felsökning av PHP-kod</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/event-dispatcher.git">symfony/event-dispatcher</a>
    </td>
    <td>bibliotek</td>
    <td>Tillhandahåller verktyg som gör att programkomponenterna kan kommunicera med varandra genom att skicka händelser och lyssna på dem</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/event-dispatcher-contracts.git">symbol/event-dispatcher-kontrakt</a>
    </td>
    <td>bibliotek</td>
    <td>Allmänna abstraktioner relaterade till skicka-händelse</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/filesystem.git">symbol/filsystem</a>
    </td>
    <td>bibliotek</td>
    <td>Tillhandahåller grundläggande verktyg för filsystemet</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/finder.git">symfony/finder</a>
    </td>
    <td>bibliotek</td>
    <td>Söker efter filer och kataloger via ett intuitivt flytande gränssnitt</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/http-foundation.git">symfony/http-foundation</a>
    </td>
    <td>bibliotek</td>
    <td>Definierar ett objektorienterat lager för HTTP-specifikationen</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/http-kernel.git">symfony/http-kernel</a>
    </td>
    <td>bibliotek</td>
    <td>Tillhandahåller en strukturerad process för konvertering av en begäran till ett svar</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/intl.git">symbol/intl</a>
    </td>
    <td>bibliotek</td>
    <td>Tillhandahåller ett PHP-ersättningslager för C intl-tillägget som innehåller ytterligare data från ICU-biblioteket</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-ctype.git">symfony/polyfill-type</a>
    </td>
    <td>bibliotek</td>
    <td>Symfonisk polyfyllning för typfunktioner</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-intl-grapheme.git">symfony/polyfill-intl-grapteme</a>
    </td>
    <td>bibliotek</td>
    <td>Symfony polyfill for intl's grapheme_* functions</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-intl-idn.git">symfony/polyfill-intl-id</a>
    </td>
    <td>bibliotek</td>
    <td>Symfony polyfill for intl's id_to_ascii and id_to_utf8 functions</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-intl-normalizer.git">symfony/polyfill-intl-normalizer</a>
    </td>
    <td>bibliotek</td>
    <td>Symfonisk polyfyllning för klassen Normalizer i AIR och relaterade funktioner</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-mbstring.git">symfony/polyfill-mbstring</a>
    </td>
    <td>bibliotek</td>
    <td>Symfonisk polyfyllning för MbitString-tillägget</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php72.git">symbol/polyfill-php72</a>
    </td>
    <td>bibliotek</td>
    <td>Symfonisk polyfill backporting vissa PHP 7.2+-funktioner ger lägre PHP-versioner</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php73.git">symbol/polyfill-php73</a>
    </td>
    <td>bibliotek</td>
    <td>Symfonisk polyfill backporting vissa PHP 7.3+-funktioner ger lägre PHP-versioner</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php80.git">symbol/polyfill-php80</a>
    </td>
    <td>bibliotek</td>
    <td>Symfonisk polyfill backporting vissa PHP 8.0+-funktioner till lägre PHP-versioner</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php81.git">symbol/polyfill-php81</a>
    </td>
    <td>bibliotek</td>
    <td>Symfonisk polyfill backporterar vissa PHP 8.1+-funktioner till lägre PHP-versioner</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/process.git">symfoni/process</a>
    </td>
    <td>bibliotek</td>
    <td>Kör kommandon i underprocesser</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/service-contracts.git">symfoni/serviceavtal</a>
    </td>
    <td>bibliotek</td>
    <td>Allmänna abstraktioner relaterade till skrivande tjänster</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/string.git">symfony/string</a>
    </td>
    <td>bibliotek</td>
    <td>Ger ett objektorienterat API för strängar och hanterar byte, UTF-8-kodpunkter och grafemkluster på ett enhetligt sätt</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/var-dumper.git">symfony/var-dumper</a>
    </td>
    <td>bibliotek</td>
    <td>Tillhandahåller mekanismer för att gå igenom valfri PHP-variabel</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/var-exporter.git">symfony/var-exporter</a>
    </td>
    <td>bibliotek</td>
    <td>Tillåter export av serialiserbara PHP-datastrukturer till vanlig PHP-kod</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thecodingmachine/safe.git">sättningsmaskin/säker</a>
    </td>
    <td>bibliotek</td>
    <td>PHP-kärnfunktioner som genererar undantag i stället för att returnera FALSE vid fel</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/web-token/jwt-framework.git">web-token/jwt-framework</a>
    </td>
    <td>symfony-bundle</td>
    <td>JSON Object Signing and Encryption library for PHP and Symfony Bundle.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/webmozarts/assert.git">webmozart/assert</a>
    </td>
    <td>bibliotek</td>
    <td>Kontroller för att validera metodens indata/utdata med bra felmeddelanden.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/webonyx/graphql-php.git">webonyx/graphql-php</a>
    </td>
    <td>bibliotek</td>
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
    <td>magento2-module</td>
    <td>Ej tillämpligt</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree-present-card-account
    </td>
    <td>magento2-module</td>
    <td>Ej tillämpligt</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree-present-wrapping
    </td>
    <td>magento2-module</td>
    <td>Ej tillämpligt</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree-graph-ql
    </td>
    <td>magento2-module</td>
    <td>Ej tillämpligt</td>
  </tr>
  <tr>
    <td>
      temando/module-shipping-remover
    </td>
    <td>magento2-module</td>
    <td>Tar bort Temando-transporttillägget för flera transportörer från Magento 2</td>
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
  <tr>
    <td>
      maskinvara/modulleverans
    </td>
    <td>metapackage</td>
    <td>Temando-utökning för flera transportföretag för Magento 2</td>
  </tr>
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
      <a href="https://github.com/2tvenom/CBOREncode.git">2tvenom/cborencode</a>
    </td>
    <td>bibliotek</td>
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
    <td>magento2-module</td>
    <td>Fork från modulen Magento Braintree 2.2.0 av Gene Commerce for PayPal.</td>
  </tr>
  </tbody>
</table>
