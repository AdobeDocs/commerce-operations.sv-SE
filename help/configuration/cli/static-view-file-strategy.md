---
title: Distributionsstrategier för statiska vyfiler
description: Läs om distributionsstrategier för Commerce-programmet.
feature: Configuration, Deploy, Extensions
exl-id: 12ebbd36-f813-494f-9515-54ce697ca2e4
source-git-commit: 403a5937561d82b02fd126c95af3f70b0ded0747
workflow-type: tm+mt
source-wordcount: '482'
ht-degree: 0%

---

# Distributionsstrategier för statiska vyfiler

När du distribuerar statiska vyfiler kan du välja en av de tre tillgängliga strategierna. Vart och ett av dem ger optimala distributionsresultat för olika användningsområden:

- [Standard](#standard-strategy): den vanliga distributionsprocessen.
- [Snabb](#quick-strategy) (_standard_): minimerar tiden som krävs för distribution när filer för fler än en språkinställning distribueras.
- [Kompakt](#compact-strategy): minimerar utrymmet som tas av de publicerade vyfilerna.

I följande avsnitt beskrivs implementeringsdetaljer och funktioner för varje strategi.

## Standardstrategi

När standardstrategin används distribueras alla statiska vyfiler för alla paket, det vill säga bearbetas av [`\Magento\Framework\App\View\Asset\Publisher`](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/View/Asset/Publisher.php).

Mer information finns i [Distribuera statiska vyfiler](../cli/static-view-file-deployment.md).

## Snabbstrategi

Den snabba strategin utför följande åtgärder:

1. För varje tema väljs ett valfritt språkområde och alla filer för det här språkområdet distribueras, som i standardstrategin.
1. För alla andra språkområden i temat:

   1. Filer som åsidosätter det distribuerade språket definieras och distribueras.
   1. Alla andra filer betraktas som lika för alla språkområden och kopieras från det distribuerade språkområdet.

>[!INFO]
>
>Av _liknande_, menar vi filer som är oberoende av språkområdet, temat eller området. Dessa filer kan innehålla CSS, bilder och teckensnitt.

Den här metoden minimerar den driftsättningstid som krävs för flera språkområden, även om många filer är duplicerade.

## Kompakt strategi

Med den kompakta strategin undviker du filduplicering genom att lagra liknande filer i `base` underkataloger.

För det mest optimerade resultatet fördelas tre omfång för möjlig likhet: område, tema och språkområde. The `base` underkataloger skapas för alla kombinationer av dessa omfattningar.

Filerna distribueras till dessa underkataloger enligt följande mönster.

| Mönster | Beskrivning |
| ------- | ----------- |
| `<area>/<theme>/<locale>` | Filer som är specifika för ett visst område, tema och språk |
| `<area>/<theme>/default` | Filer som liknar alla språkområden i ett visst tema i ett visst område. |
| `<area>/Magento/base/<locale>` | Filer som är specifika för ett visst område och en viss språkinställning, men liknande för alla teman. |
| `<area>/Magento/base/default` | Filer som är specifika för ett visst område, men liknande för alla teman och språkområden. |
| `base/Magento/base/<locale>` | Filer som liknar alla områden och teman, men som är specifika för en viss språkinställning. |
| `base/Magento/base/default` | Liknande för alla områden, teman och språkområden. |

### Mappa distribuerade filer

Den distributionsmetod som används i den kompakta strategin innebär att filer ärvs från basteman och språkområden. De här arvsrelationerna lagras i kartfilerna för varje kombination av område, tema och språkområde. Det finns separata kartfiler för PHP och JS:

- `map.php`
- `requirejs-map.js`

The `map.php` filen används av [`Magento\Framework\View\Asset\Repository`](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/View/Asset/Repository.php) för att skapa korrekta URL:er.

The `requirejs-map.js` används av `baseUrlResolver` plugin för RequireJS.

Exempel på `map.php`:

```php?start_inline=1
return [
    'Magento_Checkout::cvv.png' => [
        'area' => 'frontend',
        'theme' => 'Magento/luma',
        'locale' => 'en_US',
    ],
    '...' => [
        'area' => '...',
        'theme' => '...',
        'locale' => '...'
    ]
];
```

Exempel på `requirejs-map.js`:

```js
require.config({
    "config": {
       "baseUrlInterceptor": {
            "jquery.js": "../../../../base/Magento/base/en_US/"
        }
    }
});
```

## Tips för tilläggsutvecklare

Om du vill skapa URL:er till statiska vyfiler använder du [`\Magento\Framework\View\Asset\Repository::createAsset()`](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/View/Asset/Repository.php#L211-L244).

Använd inte URL-sammanfogningar för att undvika problem med att statiska filer inte hittas och inte visas under sidåtergivning.
