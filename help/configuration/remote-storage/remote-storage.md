---
title: Konfigurera fjärrlagring
description: Lär dig hur du konfigurerar modulen Fjärrlagring för det lokala handelsprogrammet.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '505'
ht-degree: 0%

---

# Konfigurera fjärrlagring

Modulen Fjärrlagring ger möjlighet att lagra mediefiler och schemalägga import/export i en beständig fjärrlagringsbehållare med hjälp av en lagringstjänst som AWS S3. Som standard är [!DNL Commerce] sparar mediefiler i samma filsystem som innehåller programmet. Detta är ineffektivt för komplexa konfigurationer med flera servrar och kan leda till försämrade prestanda när resurser delas. Med modulen Fjärrlagring kan du lagra mediefiler i `pub/media` katalog och importera/exportera filer i `var` för fjärrobjektets lagringskatalog för att utnyttja möjligheten att ändra storlek på serversidans bilder.

>[!INFO]
>
>Fjärrlagring är endast tillgängligt i version 2.4.2 och senare. Se [2.4.2 Versionsinformation](https://devdocs.magento.com/guides/v2.4/release-notes/open-source-2-4-2.html).

>[!INFO]
>
>Fjärrlagringsmodulen har _begränsad_ stöd för Adobe Commerce i molninfrastruktur. Adobe kan inte felsöka nätverkskorttjänsten från tredje part helt.

![schemabild](../../assets/configuration/remote-storage-schema.png)

## Alternativ för fjärrlagring

Du kan konfigurera fjärrlagring med `remote-storage` med [`setup` CLI, kommando][setup]. The `remote-storage` -alternativet har följande syntax:

```text
--remote-storage-<parameter-name>="<parameter-value>"
```

The `parameter-name` refererar till den specifika parametern för fjärrlagring. I följande tabell visas de parametrar som är tillgängliga för konfiguration av fjärrlagring:

| Kommandoradsparameter | Parameternamn | Beskrivning | Standardvärde |
|--- |--- |--- |--- |
| `remote-storage-driver` | drivrutin | Kortnamn<br>Möjliga värden:<br>**fil**: Inaktiverar fjärrlagring och använder det lokala filsystemet <br>**aws-s3**: Använd [Amazon Simple Storage Service (Amazon S3)](remote-storage-aws-s3.md) | ingen |
| `remote-storage-bucket` | bucket | Objektets lagrings- eller behållarnamn | ingen |
| `remote-storage-prefix` | prefix | Valfritt prefix (plats inuti objektlagring) | tom |
| `remote-storage-region` | region | Regionnamn | ingen |
| `remote-storage-key` | åtkomstnyckel | Valfri åtkomstnyckel | tom |
| `remote-storage-secret` | hemlig nyckel | Valfri hemlig nyckel | tom |

### Lagringskort

Standardlagringsplatsen finns i det lokala filsystemet. A _lagringskort_ gör att du kan ansluta till en lagringstjänst och lagra dina filer var som helst. [!DNL Commerce] har stöd för konfigurering av följande lagringstjänster:

- [Amazon Simple Storage Service (Amazon S3)](remote-storage-aws-s3.md)

## Aktivera fjärrlagring

Du kan installera fjärrlagring under en ny [!DNL Commerce] installera eller lägga till den i en befintlig Commerce-instans med `remote-storage` parameternamn- och värdepar med `setup` CLI-kommandon. Minimalt måste du ange lagringsutrymmet `driver`, `bucket`och `region`.

Följande exempel aktiverar fjärrlagring med en AWS S3-lagringskort i USA:

- Installera ny [!DNL Commerce] med fjärrlagring

   ```bash
   bin/magento setup:install --remote-storage-driver="aws-s3" --remote-storage-bucket="myBucket" --remote-storage-region="us-east-1"
   ```

- Aktivera fjärrlagring på befintlig [!DNL Commerce]

   ```bash
   bin/magento setup:config:set --remote-storage-driver="aws-s3" --remote-storage-bucket="myBucket" --remote-storage-region="us-east-1"
   ```

## Begränsningar

Du kan inte ha både fjärrlagring och databaslagring aktiverat samtidigt. Inaktivera databaslagring om du använder fjärrlagring.

```bash
bin/magento config:set system/media_storage_configuration/media_database 0
```

Om du aktiverar fjärrlagring kan det påverka din etablerade utvecklingsupplevelse. Vissa PHP-filfunktioner kanske inte fungerar som förväntat. Användning av Commerce Framework för filåtgärder måste verkställas.

Listan över förbjudna inbyggda PHP-funktioner finns i [Magento Coding Standard] databas.

## Migrera innehåll

När du har aktiverat fjärrlagring för ett specifikt kort kan du använda CLI för att migrera befintliga _media_ till fjärrlagringsutrymmet.

```bash
./magento2ce/bin/magento remote-storage:sync
```

>[!INFO]
>
>Synkroniseringskommandot migrerar bara filer i `pub/media` katalog, _not_ import-/exportfilerna i `var` katalog. Se [Schemalagd import/export][import-export] i _Handbok för Commerce 2.4_.

<!-- link definitions -->

[import-export]: https://docs.magento.com/user-guide/system/data-scheduled-import-export.html
[nginx-module]: http://nginx.org/en/docs/http/ngx_http_image_filter_module.html
[Magento Coding Standard]: https://github.com/magento/magento-coding-standard/blob/develop/Magento2/Sniffs/Functions/DiscouragedFunctionSniff.php
[setup]: https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-deployment.html#instgde-cli-subcommands-configphp