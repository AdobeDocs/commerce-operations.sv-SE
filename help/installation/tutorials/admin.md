---
title: Skapa, redigera eller låsa upp ett administratörskonto
description: Följ de här stegen för att hantera administratörskontot för ditt Adobe Commerce Admin-program.
feature: Install, User Account
exl-id: d87871a1-717d-4662-b84d-98a018518286
source-git-commit: aaed7dba7d11085eb8e2793cefffb8c8b082e750
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 0%

---

# Skapa, redigera eller låsa upp ett administratörskonto

Innan du kan använda det här kommandot måste du göra följande:

- [Skapa distributionskonfigurationen](deployment.md)
- [Aktivera minst Magento_Authorization och Magento_User-modulerna](manage-modules.md)
- Skapa databasschemat

>[!NOTE]
>
>Det enklaste sättet att skapa databasen är att använda kommandot `magento setup:upgrade`.

## Skapa eller redigera en administratör

Använd det här kommandot om du vill skapa en administratör eller redigera en befintlig administratör.

>[!NOTE]
>
>Om du redigerar en administratör kan bara `first name`, `last name` och `password` redigeras.

Kommandoanvändning:

```bash
bin/magento admin:user:create [--<parameter_name>=<value>, ...]
```

Där följande tabell definierar parametrar och värden:

| Namn | Värde | Obligatoriskt? |
|--- |-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--- |
| `--admin-firstname` | Administratörsanvändarens förnamn. | Ja |
| `--admin-lastname` | Administratörsanvändarens efternamn. | Ja |
| `--admin-email` | Administratörsanvändarens e-postadress. | Ja |
| `--admin-user` | Administratörsanvändarnamn. | Ja |
| `--admin-password` | Administratörslösenord. Lösenordet måste innehålla minst 12 tecken och måste innehålla minst ett alfabetiskt tecken och minst ett numeriskt tecken. <br><br>Adobe rekommenderar att du anger ett längre, mer komplext lösenord. Om lösenordssträngen innehåller specialtecken som kräver literal tolkning (t.ex. omvända snedstreck eller blanksteg) måste du omsluta lösenordet med enkla citattecken. | Ja |
| `--magento-init-params` | Lägg till i valfritt kommando för att anpassa parametrar för programinitiering<br/><br/>Till exempel: `MAGE_MODE=developer&MAGE_DIRS[base][path]=/var/www/example.com&MAGE_DIRS[cache][path]=/var/tmp/cache` | Nej |

Exempel på användning:

```bash
bin/magento admin:user:create --admin-firstname=John --admin-lastname=Doe --admin-email=j.doe@example.com --admin-user=j.doe --admin-password=A0b9%t3g
```

```
Created Magento administrator user named j.doe
```

Om du inte anger någon av de parametrar som krävs frågar programmet om dem i CLI:

```bash
bin/magento admin:user:create
```

```
Admin user: John
Admin password:
Admin email: j.doe.young@example.com
Admin first name: John
Admin last name: Doe Young
```

```
Created Magento administrator user named John
```

I följande exempel uppdateras `first name`, `last name` och `password` för `j.doe`-administratörsanvändaren:

```bash
bin/magento admin:user:create --admin-firstname="John X" --admin-lastname="Doe X" --admin-email=j.doe@example.com --admin-user=j.doe --admin-password=A1234567
```

```
Created Magento administrator user named j.doe
```

## Lås upp ett administratörskonto

Använd det här kommandot för att låsa upp kontot för en administratör som var låst, vanligtvis på grund av flera felaktiga inloggningsförsök.

```bash
bin/magento admin:user:unlock {username}
```

Du måste ange administratörens användarnamn. Exempel:

```bash
bin/magento admin:user:unlock admin
```

```
The user account "admin" has been unlocked
```

Om kontot inte är olåst eller om ett problem uppstår visas följande meddelande:

```
The user account "admin" was not locked or could not be unlocked
```

Kontrollera att användaren är administratör, att användaren är aktiv och att kontot är låst. Om du vill visa listan med låsta användare i administratören loggar du in som administratör och klickar på **System** > **Behörigheter** > **Låsta användare**.

Om kontot inte finns visas följande meddelande:

```
Couldn't find the user account "bob"
```
