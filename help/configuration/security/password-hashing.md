---
title: Lösenordshashning
description: Läs om strategier för lösenordshashning och implementering.
feature: Configuration, Security
exl-id: 2865d041-950a-4d96-869c-b4b35f5c4120
source-git-commit: 79c8a15fb9686dd26d73805e9d0fd18bb987770d
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# Lösenordshashning

För närvarande använder Commerce sin egen strategi för lösenordshashning, som bygger på olika PHP-hash-algoritmer. Commerce stöder flera algoritmer som `MD5`, `SHA256` eller `Argon 2ID13`. Om tillägget Natrium är installerat (som standard installerat i PHP 7.3) väljs `Argon 2ID13` som standardalgoritm för hashning. Annars är `SHA256` standardvärdet. Commerce kan använda den inbyggda PHP `password_hash`-funktionen med stöd för Argon 2i-algoritm.

För att undvika att kompromissa med äldre lösenord som har hashats med föråldrade algoritmer som `MD5`, erbjuder den aktuella implementeringen en metod för att uppgradera hash-koden utan att ändra det ursprungliga lösenordet. I allmänhet har lösenordshash följande format:

```text
password_hash:salt:version<n>:version<n>
```

Där `version<n>`..`version<n>` representerar alla hash-algoritmversioner som används för lösenordet. Dessutom lagras salt-värdet alltid tillsammans med lösenordshash, så att vi kan återställa hela kedjan med algoritmer. Ett exempel ser ut så här:

```text
a853b06f077b686f8a3af80c98acfca763cf10c0e03597c67e756f1c782d1ab0:8qnyO4H1OYIfGCUb:1:2
```

Den första delen representerar lösenordshash. Den andra, `8qnyO4H1OYIfGCUb`, är saltet. De två sista är de olika hash-algoritmerna: 1 är `SHA256` och 2 är `Argon 2ID13`. Det innebär att kundens lösenord ursprungligen hashas med `SHA256`, och därefter uppdaterades algoritmen med `Argon 2ID13` och hash-koden återställdes med Argon.

## Uppgradera hash-strategi

Se hur hash-uppgraderingsmekanismen ser ut. Anta att det ursprungligen hashades ett lösenord med `MD5` och att algoritmen sedan uppdaterades flera gånger med Argon 2ID13. I följande diagram visas hash-uppgraderingsflödet.

![Arbetsflöde för hash-uppgradering](../../assets/configuration/hash-upgrade-algorithm.png)

Varje hash-algoritm använder den tidigare lösenordshashen för att generera en ny hash. Commerce lagrar inte det ursprungliga, råa lösenordet.

![Hash-uppgraderingsstrategi](../../assets/configuration/hash-upgrade-strategy.png)

Som nämndes ovan kan lösenordshash-koden ha flera hash-versioner av det ursprungliga lösenordet.
Så här fungerar lösenordsverifieringsfunktionen under en kundautentisering.

```php
def verify(password, hash):
    restored = password

    hash_map = extract(hash)
    # iterate through all versions specified in the received hash [md5, sha256, argon2id13]
    for version in hash_map.get_versions():
        # generate new hash based on password/previous hash, salt and version
        restored = hash_func(salt . restored, version)

    # extract only password hash from the hash:salt:version chain
    hash = hash_map.get_hash()

    return compare(restored, hash)
```

Eftersom Commerce lagrar alla hash-versioner av lösenord som används tillsammans med lösenordshash kan vi återställa hela hash-kedjan under lösenordsverifieringen. Hash-verifieringsmekanismen liknar hash-uppgraderingsstrategin: baserat på versioner som lagras tillsammans med lösenordshash genererar algoritmen hash-värden från det angivna lösenordet och returnerar jämförelseresultatet mellan hash-kodat lösenord och den databaslagrade hash-koden.

## Implementering

Klassen `\Magento\Framework\Encryption\Encryptor` ansvarar för generering och verifiering av lösenordshash. Kommandot [`bin/magento customer:hash:upgrade`](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/cli-reference/commerce-on-premises#customerhashupgrade) uppgraderar en hash för kundlösenordet till den senaste hash-algoritmen.
