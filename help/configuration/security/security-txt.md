---
title: Security.txt
description: Lär dig hur du kan tillhandahålla information som hjälper säkerhetsforskare att rapportera säkerhetsluckor.
feature: Configuration, Security
badge: label="Bidragen av Kalpesh Mehta från Corra" type="Informative" url="https://solutionpartners.adobe.com/s/directory/detail/corra" tooltip="Kalpesh Mehta"
exl-id: ddafd03c-77b2-42e8-b593-7d655d08e9c3
source-git-commit: 56a2461edea2799a9d569bd486f995b0fe5b5947
workflow-type: tm+mt
source-wordcount: '150'
ht-degree: 0%

---

# Security TXT-fil

När forskare upptäcker säkerhetsluckor saknas ofta lämpliga rapporteringskanaler. Därför rapporteras inte vissa sårbarheter. Syftet med `security.txt` [filformat](https://datatracker.ietf.org/doc/html/draft-foudil-securitytxt-09) ska ge säkerhetsforskare den information de kan använda för att rapportera sina resultat.

Handlare kan ange sin kontaktinformation för [rapportering av säkerhetsproblem](https://docs.magento.com/user-guide/stores/security-issue-reporting.html) från handeln _Administratör_. För utvecklare `Magento_Securitytxt` i modulen finns följande funktioner:

- Tillåter att säkerhetskonfigurationer sparas från _Administratör_.
- Innehåller en router som matchar programåtgärdsklassen för begäranden till `.well-known/security.txt` och `.well-known/security.txt.sig` filer.
- Serverar innehållet i `.well-known/security.txt` och `.well-known/security.txt.sig` filer.

Ett giltigt `security.txt` filen kan se ut så här:

```text
Contact: mailto:security@example.com
Contact: tel:+1-201-555-0123
Encryption: https://example.com/pgp.asc
Acknowledgement: https://example.com/security/hall-of-fame
Policy: https://example.com/security-policy.html
Signature: https://example.com/.well-known/security.txt.sig
```

Skapa `security.txt` signatur (`security.txt.sig`):

```bash
gpg -u KEYID --output security.txt.sig --armor --detach-sig security.txt
```

Så här verifierar du signaturen:

```bash
gpg --verify security.txt.sig security.txt
```
