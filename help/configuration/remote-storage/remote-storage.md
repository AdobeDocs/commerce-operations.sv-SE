---
title: Konfigurera fjärrlagring
description: Lär dig hur du konfigurerar modulen Fjärrlagring för det lokala Commerce-programmet.
feature: Configuration, Storage
exl-id: 0428f889-46b0-44c9-8bd9-98c1be797011
source-git-commit: 4caabd1578e56b74600441c9c779b7b2dfd06987
workflow-type: tm+mt
source-wordcount: '521'
ht-degree: 0%

---

# Konfigurera fjärrlagring

Modulen Fjärrlagring ger möjlighet att lagra mediefiler och schemalägga import och export i en beständig fjärrlagringsbehållare med hjälp av en lagringstjänst som AWS S3.

Som standard lagras mediefiler i samma filsystem som innehåller programmet i Adobe Commerce. Detta är ineffektivt för komplexa konfigurationer med flera servrar och kan leda till försämrade prestanda när resurser delas. Med modulen Fjärrlagring kan du lagra mediefiler i katalogen `pub/media` och importera/exportera filer i katalogen `var` i fjärrobjektets lagringsutrymme för att dra nytta av storleksändringen på serversidan.

>[!BEGINSHADEBOX]

Du kan inte ha både fjärrlagring _och_-databaslagring aktiverat samtidigt. Du måste inaktivera databaslagring innan du aktiverar fjärrlagring.

```bash
bin/magento config:set system/media_storage_configuration/media_database 0
```

Om du aktiverar fjärrlagring kan det påverka din etablerade utvecklingsupplevelse. Vissa PHP-filfunktioner kanske inte fungerar som förväntat. Commerce Framework måste användas för filåtgärder. Listan över förbjudna inbyggda PHP-funktioner finns i databasen [magento-coding-standard](https://github.com/magento/magento-coding-standard/blob/develop/Magento2/Sniffs/Functions/DiscouragedFunctionSniff.php) .

>[!ENDSHADEBOX]

>[!INFO]
>
>- Fjärrlagring finns endast för Commerce version 2.4.2 och senare. Se versionsinformationen för [2.4.2](https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/magento-open-source/2-4-2).
>
>- Fjärrlagringsmodulen har _begränsat_ stöd för Adobe Commerce i molninfrastrukturen. Adobe kan inte felsöka nätverkskortstjänsten från tredje part. Mer information om hur du implementerar fjärrlagring för molnprojekt finns i [Konfigurera fjärrlagring för Commerce i molninfrastruktur](cloud-support.md) .

![Diagram över fjärrlagringskonfigurationen som illustrerar relationen mellan lokal lagring och molnlagring](../../assets/configuration/remote-storage-schema.png)

## Alternativ för fjärrlagring

Du kan konfigurera fjärrlagring med alternativet `remote-storage` med kommandot [`setup` CLI ](../../installation/tutorials/deployment.md). Alternativet `remote-storage` har följande syntax:

```text
--remote-storage-<parameter-name>="<parameter-value>"
```

`parameter-name` refererar till den specifika parametern för fjärrlagring. I följande tabell visas de parametrar som är tillgängliga för konfigurering av fjärrlagring:

| Kommandoradsparameter | Parameternamn | Beskrivning | Standardvärde |
|--- |--- |--- |--- |
| `remote-storage-driver` | drivrutin | Kortnamn<br>Möjliga värden:<br>**file**: Inaktiverar fjärrlagring och använder det lokala filsystemet <br>**aws-s3**: Använd [Amazon Simple Storage Service (Amazon S3)](remote-storage-aws-s3.md) | ingen |
| `remote-storage-bucket` | bucket | Objektets lagrings- eller behållarnamn | ingen |
| `remote-storage-prefix` | prefix | Valfritt prefix (plats inuti objektlagring) | tom |
| `remote-storage-region` | region | Regionnamn | ingen |
| `remote-storage-key` | åtkomstnyckel | Valfri åtkomstnyckel | tom |
| `remote-storage-secret` | hemlig nyckel | Valfri hemlig nyckel | tom |

### Lagringskort

Standardlagringsplatsen finns i det lokala filsystemet. Med ett _lagringskort_ kan du ansluta till en lagringstjänst och lagra dina filer var som helst. [!DNL Commerce] stöder konfigurering av följande lagringstjänster:

- [Amazon Simple Storage Service (Amazon S3)](remote-storage-aws-s3.md)

## Aktivera fjärrlagring

Du kan installera fjärrlagring under en Adobe Commerce-installation eller lägga till fjärrlagring i en befintlig Commerce-instans. I följande exempel visas varje metod som använder en uppsättning `remote-storage`-parametrar med Commerce `setup` CLI-kommandon. Minimalt måste du ange lagringsutrymmet `driver`, `bucket` och `region`.

- Exempel: Installera Commerce med fjärrlagring

  ```bash
  bin/magento setup:install --remote-storage-driver="aws-s3" --remote-storage-bucket="myBucket" --remote-storage-region="us-east-1"
  ```

- Exempel: Aktivera fjärrlagring på befintlig Commerce

  ```bash
  bin/magento setup:config:set --remote-storage-driver="aws-s3" --remote-storage-bucket="myBucket" --remote-storage-region="us-east-1"
  ```

>[!TIP]
>
>Information om Adobe Commerce molninfrastruktur finns i [Konfigurera fjärrlagring för Commerce i molninfrastrukturen](cloud-support.md).

## Migrera innehåll

När du har aktiverat fjärrlagring för ett specifikt kort kan du använda CLI för att migrera befintliga _media_ -filer till fjärrlagringen.

```bash
./magento2ce/bin/magento remote-storage:sync
```

>[!INFO]
>
>Synkroniseringskommandot migrerar bara filer i katalogen `pub/media`, _inte_ import-/exportfilerna i katalogen `var`. Se [Schemalagd import/export](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-scheduled-import-export.html) i användarhandboken för _Commerce 2.4_.

<!-- link definitions -->

[import-export]: https://docs.magento.com/user-guide/system/data-scheduled-import-export.html
