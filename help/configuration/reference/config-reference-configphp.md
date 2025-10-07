---
title: config.php-referens
description: Lär dig mer om filvärdena och avsnitten för config.php för Adobe Commerce-konfiguration. Upptäck metodtips för moduler, omfattningar, systeminställningar och driftsättning.
exl-id: 9b355d6d-ea66-480b-ad96-0ea9e7e61844
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '158'
ht-degree: 0%

---

# config.php-referens

Filen `config.php` innehåller följande avsnitt:

| Namn | Beskrivning |
| --------- | -------------------|
| `i18n` | Alla textbundna översättningsdata. Läsning från det här avsnittet stöds inte. |
| `modules` | Listan över aktiverade och inaktiverade moduler. |
| `scopes` | Listan över butiker, butiksgrupper och webbplatser med relaterad information. |
| `system` | Systemkonfigurationer som krävs för statisk innehållsdistribution. |
| `themes` | Konfigurationen av installerade teman. |

## moduler

Innehåller en array med moduler och deras lägen. Om modulen är aktiverad är värdet 1. I annat fall är värdet 0.

```conf
'modules' => [
    'Magento_Store' => 1,
    'Magento_Theme' => 0,
    'Magento_Backend' => 0,
    'Magento_Eav' => 1
]
```

Läs mer om [Moduler].

## omfattningar

Innehåller en array med scopets konfigurationsvärden. Den har följande delnoder:

| Namn | Beskrivning |
| ---------- | -----------------------------------|
| `websites` | Webbplatskonfiguration |
| `groups` | Lagrar konfiguration |
| `stores` | Konfiguration av butiksvyer |

```conf
'scopes' => [
  'websites' => [
    'admin' => [
      'website_id' => '0',
      'code' => 'admin',
      'name' => 'Admin',
      'sort_order' => '0',
      'default_group_id' => '0',
      'is_default' => '0'
    ]
  ],
  'groups' => [
    0 => [
      'group_id' => '0',
      'website_id' => '0',
      'code' => 'default',
      'name' => 'Default',
      'root_category_id' => '0',
      'default_store_id' => '0'
    ]
  ],
  'stores' => [
    'admin' => [
      'store_id' => '0',
      'code' => 'admin',
      'website_id' => '0',
      'group_id' => '0',
      'name' => 'Admin',
      'sort_order' => '0',
      'is_active' => '1'
    ]
  ]
]
```

Läs mer om [Commerce-scope][scopes].

## system

Innehåller en matris med konfigurationsvärden för systemfält.

```conf
'system'=> [
    'default' =>[
        'checkout' => [
            'cart' => [
                'delete_quote_after' => 31
            ]
        ]
    ]
]
```

Läs mer om [Systemspecifika konfigurationer](config-reference-sens.md).

## teman

Innehåller en array med värden för temakonfiguration.

```conf
'themes' => [
  'frontend/Magento/luma' => [
    'parent_id' => 'Magento/blank',
    'theme_path' => 'Magento/luma',
    'theme_title' => 'Magento Luma',
    'is_featured' => '0',
    'area' => 'frontend',
    'type' => '0',
    'code' => 'Magento/luma'
  ]
]
```

Läs mer om [Teman].

<!-- link definitions -->

[Moduler]: https://experienceleague.adobe.com/docs/commerce-learn/tutorials/backend-development/create-module.html?lang=sv-SE
[scopes]: https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html?lang=sv-SE#scope-settings
[Teman]: https://developer.adobe.com/commerce/frontend-core/guide/themes/create-storefront/
