---
title: system.xml, referens
description: Läs om hur systemets XML-fil hanterar Commerce programkonfiguration.
feature: Configuration, System
badge: label="Bidragen av David Lambauer" type="Informative" url="https://github.com/DavidLambauer" tooltip="David Lambauer"
exl-id: a6c5de6c-e8da-4eca-bbfb-592904b2c53f
source-git-commit: e231a27d70e29b01c872b0655168e31f590d4876
workflow-type: tm+mt
source-wordcount: '2708'
ht-degree: 0%

---

# system.xml, referens

Med filen `system.xml` kan du hantera systemkonfigurationen för Commerce. Använd det här avsnittet som allmän referens för filen `system.xml`. Filen `system.xml` finns under `etc/adminhtml/system.xml` i ett visst Commerce 2-tillägg.

I följande kodutdrag visas filens vanligaste skelett:

```xml
<?xml version="1.0" ?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Config:etc/system_file.xsd">
    <system>
        <!-- PLACE YOUR MODULE SPECIFIC CONFIGURATION HERE -->
    </system>
</config>
```

>[!TIP]
>
>Om du vill ha omedelbar *XSD-validering i din IDE kan du köra `bin/magento dev:urn-catalog:generate [--ide IDE] [--] <path>`.

## Tabbar // Avsnitt // Grupper // Fält

I filen `system.xml` är det möjligt att definiera fyra olika typer av entiteter, som är relaterade till varandra. I följande avsnitt beskrivs relationen mellan flikar, avsnitt, grupper och fält. På följande skärmbild visas systemkonfigurationen för Commerce 2 i serverdelen Admin.
De röda fyrkanterna markerar de olika typer som definieras i filen `system.xml`:

![Skärmbild som visar ett konfigurerat avsnitt i administratören.](../../assets/configuration/magento2-system-configuration.png)

Flikar används för att dela olika konfigurationsområden semantiskt. Varje flik kan innehålla ett eller flera avsnitt som också kan kallas undermenyer. Ett avsnitt innehåller en eller flera grupper.
Varje grupp listar ett eller flera fält. Du kan också använda en grupp för att lägga till en allmän beskrivning för följande fält. Som nämnts kan varje grupp ha ett eller flera fält. Fält är den minsta enheten
i systemkonfigurationskontexten.

## Tabbar

En `<tab>`-tagg refererar till antingen en befintlig eller en ny flik i systemkonfigurationen.

### Flikattributsreferens

En `<tab>`-tagg kan ha följande attribut:

| Attribut | Beskrivning | Typ | Obligatoriskt |
|-------------|------------------------------------------------------------------------------------------------------------------------------------------|----------|----------|
| `id` | Definierar den identifierare som används för att referera till avsnittet. | `typeId` | obligatoriskt |
| `translate` | Definierar det fält som ska vara översättningsbart. Ange `label` för att göra etiketten översättningsbar. | `string` | valfri |
| `sortOrder` | Definierar sorteringsordningen för avsnittet. Ett högt antal flyttar avsnittet längst ned på sidan och ett lågt antal flyttar avsnittet uppåt. | `float` | valfri |
| `class` | Lägger till en definierad CSS-klass i det återgivna flikelementet HTML. | `string` | valfri |

### Fliknodreferens

En `<tab>`-tagg kan ha följande underordnade taggar:

| Nod | Beskrivning | Typ |
|---------|------------------------------------------------------|----------|
| `label` | Definierar den etikett som visas i förgrunden. | `string` |

### Exempel: Skapa en flik

I följande kodutdrag visas hur du skapar en ny flik med exempeldata.

```xml
<?xml version="1.0" ?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Config:etc/system_file.xsd">
    <system>
        <tab id="A_UNIQUE_ID" translate="label" class="a-custom-css-class-to-style-this-tab" sortOrder="10">
            <label>A meaningful label</label>
        </tab>
    </system>
</config>
```

Ovanstående kodutdrag skapar en ny flik med identifieraren `A_UNIQUE_ID`. När attributet `translate` definieras och refererar till etiketten, kan `label`-noden översättas. Under återgivningsprocessen kommer CSS-klassen `a-custom-css-class-to-style-this-tab` att användas på elementet HTML som skapades för den här fliken.
`sortOrder`-attributet med värdet `10` definierar tabbens position i listan över alla flikar när de återges.

## Avsnitt

En `<section>`-tagg refererar till antingen ett befintligt eller ett nytt avsnitt i systemkonfigurationen.

### Avsnittsattributreferens

En `<section>`-tagg kan ha följande attribut:

| Attribut | Beskrivning | Typ | Obligatoriskt |
|:----------------|:---------------------------------------------------------------------------------------------------------------------------------------------------|:---------|:---------|
| `id` | Definierar den identifierare som används för att referera till avsnittet. | `typeId` | obligatoriskt |
| `translate` | Definierar det fält som ska vara översättningsbart. Ange `label` för att göra etiketten översättningsbar. | `string` | valfri |
| `type` | Definierar indatatypen för det återgivna HTML-elementet. Standardvärdet är `text`. | `string` | valfri |
| `sortOrder` | Definierar sorteringsordningen för avsnittet. Ett högt tal flyttar avsnittet längst ned på sidan och ett lågt värde flyttar avsnittet uppåt. | `float` | valfri |
| `showInDefault` | Definierar om avsnittet visas i standardkonfigurationsomfånget. Ange `1` om du vill visa avsnittet och `0` om du vill dölja avsnittet. | `int` | valfri |
| `showInStore` | Definierar om avsnittet visas på butiksnivå. Ange `1` om du vill visa avsnittet och `0` om du vill dölja avsnittet. | `int` | valfri |
| `showInWebsite` | Definierar om avsnittet visas på webbplatsnivå. Ange `1` om du vill visa avsnittet och `0` om du vill dölja avsnittet. | `int` | valfri |
| `canRestore` | Anger om avsnittet kan återställas till standardvärdet. | `int` | valfri |
| `advanced` | Borttagen sedan 10.0.2. | `bool` | valfri |
| `extends` | Genom att ange en identifierare för ett annat avsnitt kommer innehållet i den här noden att utöka det avsnitt som du refererade till. | `string` | valfri |

### Avsnittsnodreferens

En `<section>`-tagg kan ha följande underordnade taggar:

| Nod | Beskrivning | Typ |
|------------------|-----------------------------------------------------------------------------------------------------------------------|---------------------|
| `label` | Definierar den etikett som visas i förgrunden. | `string` |
| `class` | Lägger till en definierad CSS-klass i det återgivna avsnittets HTML-element. | `string` |
| `tab` | Refererar till den associerade fliken. Förväntar flikens ID. | `typeTabId` |
| `header_css` | Varken använt eller utvärderat vid tidpunkten för detta skrivande. | `string` |
| `resource` | Refererar till en ACL-resurs för att ange behörighetsinställningar för det här avsnittet. | `typeAclResourceId` |
| `group` | Definiera en eller flera undergrupper. | `typeGroup` |
| `frontend_model` | Anger en annan kantmodell för att ändra återgivningen och ändra utdata. | `typeModel` |
| `include` | Används för att inkludera ytterligare `system_include.xsd`-kompatibla filer. Används vanligen för att strukturera stora `system.xml` filer. | `includeType` |

### Exempel: Skapa ett avsnitt och tilldela det till en flik

Följande kodfragment visar hur du använder det till att skapa ett nytt avsnitt.

```xml
<?xml version="1.0" ?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Config:etc/system_file.xsd">
    <system>
        <tab id="A_UNIQUE_ID" translate="label" class="a-custom-css-class-to-style-this-tab" sortOrder="10">
            <label>A meaningful label</label>
        </tab>

        <section id="A_UNIQUE_SECTION_ID" showInDefault="1" showInWebsite="0" showInStore="1" sortOrder="10" translate="label">
            <label>A meaningful section label</label>
            <tab>A_UNIQUE_ID</tab>
            <resource>VENDOR_MODULE::path_to_the_acl_resource</resource>
        </section>
    </system>
</config>
```

Avsnittet som beskrivs ovan definierar ID:t `A_UNIQUE_SECTION_ID`, som är synligt i standardkonfigurationsvyn och i en butikskontext. `label`-noden är översättningsbar. Avsnittet är associerat med fliken med ID:t `A_UNIQUE_ID`. Avsnittet kan bara nås av användare som har de behörigheter som definierats i åtkomstkontrollistan `VENDOR_MODULE::path_to_the_acl_resource`.

## Grupper

Taggen `<group>` används för att gruppera fält tillsammans.

### Gruppattributreferens

En `<group>`-tagg kan ha följande attribut:

| Attribut | Beskrivning | Typ | Obligatoriskt |
|:----------------|:---------------------------------------------------------------------------------------------------------------------------------------------------|:---------|:---------|
| `id` | Definierar den identifierare som används som referens för gruppen. | `typeId` | obligatoriskt |
| `translate` | Definierar de fält som ska vara översättningsbara. Ange `label` för att göra etiketten översättningsbar. Flera fält ska avgränsas med ett blanksteg. | `string` | valfri |
| `type` | Definierar indatatypen för det återgivna HTML-elementet. Standardvärdet är `text`. | `string` | valfri |
| `sortOrder` | Definierar sorteringsordningen för avsnittet. Ett högt tal flyttar avsnittet längst ned på sidan och ett lågt värde flyttar avsnittet uppåt. | `float` | valfri |
| `showInDefault` | Definierar om gruppen visas i standardkonfigurationsomfånget. Ange `1` om du vill visa gruppen och `0` om du vill dölja gruppen. | `int` | valfri |
| `showInStore` | Definierar om gruppen visas på butiksnivå. Ange `1` om du vill visa gruppen och `0` om du vill dölja gruppen. | `int` | valfri |
| `showInWebsite` | Definierar om gruppen visas på webbplatsnivå. Ange `1` om du vill visa gruppen och `0` om du vill dölja gruppen. | `int` | valfri |
| `canRestore` | Definierar om gruppen kan återställas till standardvärdet. | `int` | valfri |
| `advanced` | Borttagen sedan 10.0.2. | `bool` | valfri |
| `extends` | Genom att ange en identifierare för en annan grupp kommer innehållet i den här noden att utöka det avsnitt som du refererade till. | `string` | valfri |

### Gruppnodreferens

En `<group>`-tagg kan ha följande underordnade taggar:

| Nod | Beskrivning | Typ |
|-----------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------|
| `label` | Definierar den etikett som visas i förgrunden. | `string` |
| `fieldset_css` | Lägger till en eller flera CSS-klasser i en gruppfältuppsättning. | `string` |
| `frontend_model` | Anger en annan kantmodell för att ändra återgivningen och ändra utdata. | `typeModel` |
| `clone_model` | Anger en angiven modell för att klona fält. | `typeModel` |
| `clone_fields` | Kloning av fält har aktiverats eller inaktiverats. | `int` |
| `help_url` | Kan inte utökas. Se nedan. | `typeUrl` |
| `more_url` | Kan inte utökas. Se nedan. | `typeUrl` |
| `demo_link` | Kan inte utökas. Se nedan. | `typeUrl` |
| `comment` | Lägger till en kommentar under gruppetiketten. Genom att använda `<![CDATA[//]]>` HTML kan du använda det. | `string` |
| `hide_in_single_store_mode` | Anger om gruppen ska vara synlig i läget för en enskild butik. `1` döljer gruppen. `0` visar gruppen. | `int` |
| `field` | Definiera ett eller flera fält som ska vara tillgängliga under gruppen. | `field` |
| `group` | Definiera en eller flera undergrupper. | `unbounded` |
| `depends` | Kan användas för att deklarera beroenden för andra fält. Används endast för att visa specifika fält/grupper när ett angivet fält har värdet `1`. Den här noden förväntar sig en `section/group/field`-sträng. | `depends` |
| `attribute` | Anpassade attribut kan användas av klientmodeller. Används vanligen för att göra en viss kantmodell mer dynamisk. | `attribute` |
| `include` | Används för att inkludera ytterligare `system_include.xsd`-kompatibla filer. Används vanligen för att strukturera stora `system.xml` filer. | `includeType` |

>[!WARNING]
>
>Noderna `more_url`, `demo_url` och `help_url` definieras av en PayPal-frontmodell som bara används en gång. Dessa noder kan inte återanvändas.

### Exempel: Skapa en grupp för ett visst avsnitt

Följande kodfragment visar hur du kan skapa en ny grupp.

```xml
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Config:etc/system_file.xsd">
    <system>
        <tab id="A_UNIQUE_ID" translate="label" class="a-custom-css-class-to-style-this-tab" sortOrder="10">
            <label>A meaningful label</label>
        </tab>

        <section id="A_UNIQUE_SECTION_ID" showInDefault="1" showInWebsite="0" showInStore="1" sortOrder="10" translate="label">
            <label>A meaningful section label</label>
            <tab>A_UNIQUE_ID</tab>
            <resource>VENDOR_MODULE::path_to_the_acl_resource</resource>

            <group id="A_UNIQUE_GROUP_ID" translate="label comment" sortOrder="10" showInDefault="1" showInWebsite="0" showInStore="1">
                <label>A meaningful group label</label>
                <comment>An additional comment helping users to understand the effect when configuring the fields defined in this group.</comment>
                <!-- Add your fields here. -->
            </group>
        </section>
    </system>
</config>
```

Den grupp som beskrivs ovan definierar ID:t `A_UNIQUE_GROUP_ID`, som är synligt i standardkonfigurationsvyn och i en butikskontext. Både `label` och `comment` är markerade som översättningsbara.

## Fält

Taggen `<field>`-Tag används i `<group>`-taggar för att definiera specifika konfigurationsvärden.

### Fältattributreferens

En `<field>`-tagg kan ha följande attribut:

| Attribut | Beskrivning | Typ | Obligatoriskt |
|:----------------|:---------------------------------------------------------------------------------------------------------------------------------------------------|:---------|:---------|
| `id` | Definierar den identifierare som används som referens för fältet. | `typeId` | obligatoriskt |
| `translate` | Definierar de fält som ska vara översättningsbara. Ange `label` för att göra etiketten översättningsbar. Flera fält ska avgränsas med ett blanksteg. | `string` | valfri |
| `type` | Definierar indatatypen för det återgivna HTML-elementet. Standardvärdet är `text`. | `string` | valfri |
| `sortOrder` | Definierar sorteringsordningen för avsnittet. Ett högt antal flyttar avsnittet längst ned på sidan och ett lågt antal flyttar avsnittet uppåt. | `float` | valfri |
| `showInDefault` | Definierar om fältet visas i standardkonfigurationsomfånget. Ange `1` om du vill visa fältet och `0` om du vill dölja fältet. | `int` | valfri |
| `showInStore` | Definierar om fältet visas på butiksnivå. Ange `1` om du vill visa fältet och `0` om du vill dölja fältet. | `int` | valfri |
| `showInWebsite` | Definierar om fältet visas på webbplatsnivå. Ange `1` om du vill visa fältet och `0` om du vill dölja fältet. | `int` | valfri |
| `canRestore` | Definierar om fältet kan återställas till standardvärdet. | `int` | valfri |
| `advanced` | Borttagen sedan 10.0.2. | `bool` | valfri |
| `extends` | Genom att ange en identifierare för ett annat fält kommer innehållet i den här noden att utöka det avsnitt som du refererade till. | `string` | valfri |

### Fälttypsreferens

En `<field>`-tagg kan ha följande värden för attributet `type=""`:

| Typ | Beskrivning |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `text` | Textfält med en rad |
| `textarea` | Textblock |
| `select` | Normal listruta, kan behöva en anpassad `source_model`. Används även för `Yes/No` markeringar. Se `Magento\Search\Model\Adminhtml\System\Config\Source\Engine` för ett exempel. |
| `multiselect` | Som `select`, men flera alternativ är giltiga. |
| `button` | En knapp som utlöser en omedelbar händelse. Kräver en anpassad front end-modell för att definiera knapptexten och åtgärden. Se `Magento\ScheduledImportExport\Block\Adminhtml\System\Config\Clean` för ett exempel. |
| `obscure` | Ett textfält med värdet krypterat och visat som `**&#x200B;**`. Värdet visas inte om du ändrar typen med&quot;Inspect Element&quot; i webbläsaren. |
| `password` | Precis som `obscure`, förutom att det dolda värdet inte är krypterat, så visas värdet om du tvingar en ändring av typen med Inspect Element i webbläsaren. |
| `file` | Tillåter att en fil överförs för bearbetning. |
| `label` | Visar en etikett i stället för ett redigerbart fält. Använd den här typen när ett fält bara kan redigeras i specifika omfång, till exempel enbart butiksvynivå. |
| `time` | Kontroll för att ange tid med tre listrutor - timme, minut och sekund. |
| `allowspecific` | En flervalslista med specifika länder. Kräver en `source_model` som `Magento\Shipping\Model\Config\Source\Allspecificcountries` |
| `image` | Tillåter att en bild överförs. |
| `note` | Tillåter att en informationsanteckning läggs till på sidan. Den här typen kräver `frontend_model` för att återge anteckningen. |

Det går också att skapa en anpassad fälttyp. Detta görs ofta när en specialknapp med en åtgärd krävs. För att göra detta krävs två huvudelement:

- Skapa ett block i området `adminhtml`
- Anger sökvägen `type=""` till det här blocket

Själva blocket kräver minst en `__construct`-metod och en `getElementHtml()`-metod. [Magento_OfflineShipping](https://github.com/magento/magento2/blob/2.4/app/code/Magento/OfflineShipping) är ett enkelt exempel på en anpassad typ.

I modulen OfflineShipping definieras exportknappen i `Magento\OfflineShipping\Block\Adminhtml\Form\Field\Export` och fältdefinitionen ser ut så här:

```xml
<field id="export" translate="label" type="Magento\OfflineShipping\Block\Adminhtml\Form\Field\Export" sortOrder="5" showInDefault="0" showInWebsite="1" showInStore="0">
    <label>Export</label>
</field>
```

### Fältnodreferens

En `<field>`-tagg kan ha följande underordnade taggar:

| Nod | Beskrivning | Typ |
|-----------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------|
| `label` | Definierar den etikett som visas i förgrunden. | `string` |
| `comment` | Lägger till en kommentar under fältetiketten. Genom att använda `<![CDATA[//]]>` HTML kan du använda det. | `string` |
| `tooltip` | Ett annat möjligt klientelement som kan användas för att beskriva fältets betydelse. Visas som en liten ikon bredvid fältet. | `string` |
| `hint` | Visar ytterligare information. Endast tillgänglig med specifik `frontend_model`. | `string` |
| `frontend_class` | Lägger till en definierad CSS-klass i det återgivna avsnittets HTML-element. | `string` |
| `frontend_model` | Anger en annan kantmodell för att ändra återgivningen och ändra utdata. | `typeModel` |
| `backend_model` | Anger en annan serverdelsmodell för att ändra de konfigurerade värdena. | `typeModel` |
| `source_model` | Anger en annan källmodell som innehåller en viss uppsättning värden. | `typeModel` |
| `config_path` | Kan användas för att skriva över den allmänna konfigurationssökvägen för ett fält. | `typeConfigPath` |
| `validate` | Definiera olika valideringsregler (blankstegsavgränsade). En fullständig referenslista över tillgängliga valideringsregler finns nedan. | `string` |
| `can_be_empty` | Används när `type` är `multiselect` för att ange att ett fält kan vara tomt. | `int` |
| `if_module_enabled` | Används för att visa ett fält endast när en viss modul är aktiverad. | `typeModule` |
| `base_url` | Används i kombination med `upload_dir` för filöverföringar. | `typeUrl` |
| `upload_dir` | Ange en målkatalog för överföringar. Den här noden har ytterligare attribut och noder. Slå upp dem innan du använder det här. | `typeUploadDir` |
| `button_url` | Visar en knapp om `button_url` och `button_label` har angetts. Används vanligtvis i kombination med en anpassad frontmodell. | `typeUrl` |
| `button_label` | Visar en knapp om `button_label` och `button_url` har angetts. Används vanligtvis i kombination med en anpassad frontmodell. | `string` |
| `more_url` | Kan inte utökas. Se nedan. | `typeUrl` |
| `demo_url` | Kan inte utökas. Se nedan. | `typeUrl` |
| `hide_in_single_store_mode` | Anger om gruppen ska vara synlig i läget för en enskild butik. `1` döljer gruppen. `0` visar gruppen. | `int` |
| `options` | Används inte. Kan vara föråldrat. | `complexType` |
| `depends` | Kan användas för att deklarera beroenden till andra fält. Används för att endast visa specifika fält/grupper när ett angivet fält har värdet `1`. Den här noden förväntar sig en `section/group/field`-sträng. | `complexType` |
| `attribute` | Anpassade attribut kan användas av klientmodeller. Används vanligen för att göra en viss kantmodell mer dynamisk. | `complexType` |
| `requires` | Kan inte utökas. Se nedan. | `complexType` |

>[!WARNING]
>
>Noderna `more_url`, `demo_url`, `requires` och `options` definieras av en annan kärnbetalningsmodell och används bara en gång. Dessa noder kan inte återanvändas.

### Exempel: Skapa två fält i en viss grupp

```xml
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Config:etc/system_file.xsd">
    <system>
        <tab id="A_UNIQUE_ID" translate="label" class="a-custom-css-class-to-style-this-tab" sortOrder="10">
            <label>A meaningful label</label>
        </tab>

        <section id="A_UNIQUE_SECTION_ID" showInDefault="1" showInWebsite="0" showInStore="1" sortOrder="10" translate="label">
            <label>A meaningful section label</label>
            <tab>A_UNIQUE_ID</tab>
            <resource>VENDOR_MODULE::path_to_the_acl_resource</resource>

            <group id="A_UNIQUE_GROUP_ID" translate="label" sortOrder="10" showInDefault="1" showInWebsite="0" showInStore="1">
                <label>A meaningful group label</label>
                <comment>An additional comment helping users to understand the effect when configuring the fields defined in this group.</comment>

                <field id="A_UNIQUE_FIELD_ID" translate="label" sortOrder="10" showInDefault="0" showInWebsite="0" showInStore="1" type="select">
                    <label>Feature Flag Example</label>
                    <comment>This field is an example for a basic yes or no select.</comment>
                    <tooltip>Usually these kinds of fields are used to enable or disable a given feature. Other fields might be dependent to this and will only appear if this field is set to yes.</tooltip>
                    <source_model>Magento\Config\Model\Config\Source\Yesno</source_model>
                </field>

                <field id="ANOTHER_UNIQUE_FIELD_ID" translate="label" sortOrder="10" showInDefault="0" showInWebsite="0" showInStore="1" type="text">
                    <label>A meaningful field label</label>
                    <comment>A descriptive text explaining this configuration field.</comment>
                    <tooltip>Another possible frontend element that also can be used to describe the meaning of this field. Will be displayed as a small icon beside the field.</tooltip>
                    <validate>required-entry no-whitespace</validate> <!-- Field is required and must not contain any whitespace. -->
                    <if_module_enabled>VENDOR_MODULE</if_module_enabled>
                    <depends> <!-- This field will only be visible if the field with the id A_UNIQUE_FIELD_ID is set to value 1 -->
                        <field id="A_UNIQUE_FIELD_ID">1</field>
                    </depends>
                </field>
            </group>
        </section>
    </system>
</config>
```

I exemplet ovan skapas två fält, både synliga/konfigurerbara som standard och i butiksvyn. Båda fälten har en kommentar och ett verktygstips som beskriver syftet för användaren. `label`-noden är översättningsbar.
Fältet med identifieraren `ANOTHER_UNIQUE_FIELD_ID` är synligt när den angivna modulen i `if_module_enabled` är aktiverad globalt. Fältet validerar också dess värde mot reglerna `required-entry` och `no-whitespace`.
Fältet med identifieraren `A_UNIQUE_FIELD_ID` definierar en annan källmodell som tillhandahåller värdena `Yes` och `No`.

### Vanliga källmodeller

Följande källmodeller tillhandahålls av Commerce 2 Core. I allmänhet finns det många fler källmodeller. I följande lista beskrivs de vanligaste. Observera att dessa källmodeller kräver att fältattributet `type` anges till `select` för att fungera korrekt.

| Source Model | Beskrivning |
|-----------------------------------------------------------|------------------------------------------------------------------------------------------------------------|
| `Magento\Config\Model\Config\Source\Yesnocustom` | Tillhandahåller värdena `Yes`, `No` och `Specified`. |
| `Magento\Config\Model\Config\Source\Enabledisable` | Anger värdena `Enable`, `Disable`. Sparar värdena som `0` och `1` i databasen. |
| `Magento\AdminNotification\Model\Config\Source\Frequency` | Tillhandahåller värdena `1 Hour`,`2 Hours`,`6 Hours`,`12 Hours` och `24 Hours`. Värden sparas som heltal. |
| `Magento\Catalog\Model\Config\Source\TimeFormat` | Anger värden för tidsformatet (12 tim/24 tim). |
| `Magento\Cron\Model\Config\Source\Frequency` | Tillhandahåller värdena `Daily`, `Weekly` och `Monthly`. Värden sparas i databasen som `D`, `W` och `M`. |
| `Magento\GoogleAdwords\Model\Config\Source\Language` | Tillhandahåller värden för en tvåbokstavskod för ett visst språk i formatet ISO 639-1 (t.ex. en). |
| `Magento\Config\Model\Config\Source\Locale` | Tillhandahåller värden som liknar ovanstående, men innehåller en språkkod (t.ex. en_US). |

### Fältvalidering

Ett fält kan ha en eller flera valideringsklasser tilldelade för att säkerställa att användarens indata uppfyller kraven för tillägget. Valideringsregler kan tillämpas med taggen `<validate>`.
I följande exempel valideras ett fält och flera olika valideringsregler läggs till.

```xml
<field id="A_CUSTOM_IDENTIFIER" showInDefault="1" showInWebsite="0" showInStore="1">
    <validate>required-entry validate-clean-url no-whitespace</validate>
</field>
```

Följande valideringsregler är tillgängliga:

| Regel | Beskrivning |
|---------------------------------|-------------------------------------------------------------------------------------------------------------------------|
| `alphanumeric` | Endast bokstäver, siffror, blanksteg och understreck tillåts. |
| `integer` | Tillåter ett positivt eller negativt icke-decimaltal. |
| `ipv4` | Tillåter en giltig IP v4-adress. |
| `ipv6` | Tillåter en giltig IP v6-adress. |
| `letters-only` | Endast bokstäver tillåts. Exempel: `abcABC`. |
| `letters-with-basic-punc` | Tillåter endast bokstäver och skiljetecken.<br>Måste skicka följande uttryck: `/^[a-z\-.,()\u0027\u0022\s]+$/i`. |
| `mobileUK` | Tillåter ett (Storbritannien) mobiltelefonnummer. |
| `no-marginal-whitespace` | Tillåt inte blanktecken i början eller slutet av värdet. |
| `no-whitespace` | Tillåt inte blanksteg. |
| `phoneUK` | Tillåter ett (UK) telefonnummer. |
| `phoneUS` | Tillåter ett (US) telefonnummer. |
| `required-entry` | Tillåter inte ett tomt värde (motsvarande validering som `validate-no-empty`).<br>Meddelande om verifieringsfel:&quot;Detta är ett obligatoriskt fält.&quot; |
| `time` | Tillåter en giltig tid i 24-timmarsformat, mellan 00:00 och 23:59. Till exempel `15`, `15:05` eller `15:05:48`. |
| `time12h` | Tillåter en giltig tid i 12-timmarsformat, mellan 12:00 och 11:59:59:00. Till exempel `3 am`, `11:30 pm`, `02:15:00 pm`. |
| `validate-admin-password` | Tillåter 7 eller fler tecken med både numeriska och alfabetiska tecken. |
| `validate-alphanum-with-spaces` | Tillåter användning av bokstäver (a-z eller A-Z), siffror (0-9) eller mellanslag. |
| `validate-clean-url` | Tillåter en giltig URL. Till exempel `https://www.example.com` eller `www.example.com`. |
| `validate-currency-dollar` | Tillåter ett giltigt belopp (USD). Exempel: $100.00. |
| `validate-data` | Tillåter endast användning av bokstäver (a-z eller A-Z), siffror (0-9) eller understreck (\_).<br>Det första tecknet måste vara en bokstav.<br>(Måste matcha uttryck: `/^[A-Za-z]+[A-Za-z0-9_]+$/`)<br>Meddelande om verifieringsfel: &quot;Använd endast bokstäver (a-z eller A-Z), siffror (0-9) eller understreck (\_) i det här fältet, och det första tecknet ska vara en bokstav.&quot; |
| `validate-date-au` | Tvingar fram följande datumformat: dd/mm/åååå. Exempel: 17/03/2006 för den 17 mars 2006. |
| `validate-email` | Tillåter en giltig e-postadress. Exempel: johndoe@domain.com. |
| `validate-emailSender` | Tillåter en giltig e-postadress. Exempel: johndoe@domain.com. |
| `validate-fax` | Tillåter ett giltigt faxnummer. Exempel: 123-456-7890. |
| `validate-no-empty` | Tillåter inte ett tomt värde (motsvarande validering som `requried-entry`).<br>Meddelande om verifieringsfel: &quot;Tomt värde.&quot; |
| `validate-no-html-tags` | Tillåt inte användning av HTML-taggar. |
| `validate-password` | Tillåter 6 eller fler tecken. Radavstånd och avslutande blanksteg ignoreras. |
| `validate-phoneLax` | Tillåter ett giltigt telefonnummer. Exempel: (123) 456-7890 eller 123-456-7890. |
| `validate-phoneStrict` | Tillåter ett giltigt telefonnummer. Exempel: (123) 456-7890 eller 123-456-7890. |
| `validate-select` | Tvingar det valda alternativet att inte ha ett `null`-värde, ett strängvärde på `none` eller en stränglängd på 0. |
| `validate-ssn` | Tillåter ett giltigt (US) socialförsäkringsnummer. Exempel: 123-45-6789. |
| `validate-street` | Tillåter endast användning av bokstäver (a-z eller A-Z), siffror (0-9), blanksteg och&quot;#&quot;. |
| `validate-url` | Tillåter en giltig URL. Protokoll krävs (http://, https:// eller ftp://). |
| `validate-xml-identifier` | Tillåter en giltig XML-identifierare. Exempel: Something_1, block5, id-4. |
| `validate-zip-us` | Tillåter ett giltigt (US) postnummer. Exempel: 90602 eller 90602-1234. |
| `vinUS` | Tillåter (USA) identifieringsnummer för fordon (VIN). |

### Standardvärden

Standardvärden för fält kan anges i modulens `etc/config.xml`-fil genom att ange standardvärdet i noden `section/group/field_ID`.

#### Exempel: Anger standardvärdet för `ANOTHER_UNIQUE_FIELD_ID` (standardomfång)

```xml
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Store:etc/config.xsd">
    <default>
        <A_UNIQUE_SECTION_ID>
            <A_UNIQUE_GROUP_ID>
                <ANOTHER_UNIQUE_FIELD_ID>This is the default value</ANOTHER_UNIQUE_FIELD_ID>
            </A_UNIQUE_GROUP_ID>
        </A_UNIQUE_SECTION_ID>
    </default>
</config>
```

#### Exempel: Anger standardvärdet för `ANOTHER_UNIQUE_FIELD_ID` (webbplatsomfattning)

Använd taggen `websites` och ange standardvärdet för en specifik webbplats.

```xml
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Store:etc/config.xsd">
    <websites>
        <WEBSITE_CODE>
            <A_UNIQUE_SECTION_ID>
                <A_UNIQUE_GROUP_ID>
                    <ANOTHER_UNIQUE_FIELD_ID>This is the default value</ANOTHER_UNIQUE_FIELD_ID>
                </A_UNIQUE_GROUP_ID>
            </A_UNIQUE_SECTION_ID>
        </WEBSITE_CODE>
    </websites>
</config>
```
