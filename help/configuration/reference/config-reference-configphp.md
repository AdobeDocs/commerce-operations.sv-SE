---
title: config.php-referens
description: Se en lista med värden i filen config.php.
source-git-commit: 96fe0c5eeaa029347c829c39547ee5e473c8d04d
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 0%

---


# config.php-referens

The `config.php` filen innehåller följande avsnitt:

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

## scope

Innehåller en matris med konfigurationsvärden för omfång. Den har följande delnoder:

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

Läs mer om [Handelsomfång][scopes].

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

[Moduler]: https://devdocs.magento.com/videos/fundamentals/create-a-new-module/
[scopes]: https://docs.magento.com/user-guide/configuration/scope.html
[Teman]: https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/themes/theme-create.html
