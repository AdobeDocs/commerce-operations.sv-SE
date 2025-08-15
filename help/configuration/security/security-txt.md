---
title: Security.txt
description: Lär dig hur du kan tillhandahålla information som hjälper säkerhetsforskare att rapportera säkerhetsluckor.
feature: Configuration, Security
badge: label="Bidragen av Kalpesh Mehta från Corra" type="Informative" url="https://solutionpartners.adobe.com/s/directory/detail/corra" tooltip="Kalpesh Mehta"
exl-id: ddafd03c-77b2-42e8-b593-7d655d08e9c3
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 0%

---

# Security TXT-fil

När forskare upptäcker säkerhetsluckor saknas ofta lämpliga rapporteringskanaler. Därför rapporteras inte vissa sårbarheter. Syftet med filen `security.txt` [filformat](https://datatracker.ietf.org/doc/html/draft-foudil-securitytxt-09) är att ge säkerhetsforskare den information de kan använda för att rapportera sina upptäckter.

Handläggarna kan ange sin kontaktinformation för [säkerhetsproblemrapportering](https://experienceleague.adobe.com/sv/docs/commerce-admin/systems/security/security-issue-reporting) från Commerce _Admin_. För utvecklare innehåller modulen `Magento_Securitytxt` följande funktioner:

- Tillåter att säkerhetskonfigurationer sparas från _administratören_.
- Innehåller en router som matchar programåtgärdsklassen för begäranden till filerna `.well-known/security.txt` och `.well-known/security.txt.sig`.
- Hanterar innehållet i `.well-known/security.txt`- och `.well-known/security.txt.sig`-filerna.

En giltig `security.txt`-fil kan se ut så här:

```text
Contact: mailto:security@example.com
Contact: tel:+1-201-555-0123
Encryption: https://example.com/pgp.asc
Acknowledgement: https://example.com/security/hall-of-fame
Policy: https://example.com/security-policy.html
Signature: https://example.com/.well-known/security.txt.sig
```

Så här skapar du signaturfilen `security.txt` (`security.txt.sig`):

```bash
gpg -u KEYID --output security.txt.sig --armor --detach-sig security.txt
```

Så här verifierar du signaturen:

```bash
gpg --verify security.txt.sig security.txt
```
