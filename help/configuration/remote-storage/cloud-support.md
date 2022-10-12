---
title: Fjärrlagring för Commerce i molninfrastruktur
description: Mer information om hur du konfigurerar fjärrlagring för Adobe Commerce om molninfrastruktur finns i vägledningen.
source-git-commit: 9a5993c9a65ad210f1a9682734730f235bbc3d44
workflow-type: tm+mt
source-wordcount: '175'
ht-degree: 0%

---


# Konfigurera fjärrlagring för Commerce i molninfrastruktur

Om du väljer att använda fjärrlagringslösningen med ett Adobe Commerce-projekt för molninfrastruktur använder du [Amazon S3](https://docs.fastly.com/en/guides/amazon-s3) i _Snabbt_ dokumentation som säkerställer att Snabb bildoptimering fungerar med AWS S3.

Var redo med [Autentiseringsuppgifter snabbt](https://devdocs.magento.com/cloud/cdn/configure-fastly.html#cloud-fastly-creds). I Pro-projekt kan du använda SSH för att ansluta till servern och hämta inloggningsuppgifterna snabbt från `/mnt/shared/fastly_tokens.txt` -fil. För mellanlagrings- och produktionsmiljöer finns unika autentiseringsuppgifter. Du måste hämta autentiseringsuppgifterna för varje miljö.

Fortsätt konfigurera fjärrlagring för molnprojekt med följande uppgifter:

1. Konfigurera en [Snabb integration med backend](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/Edge-Modules/EDGE-MODULE-OTHER-CMS-INTEGRATION.md).

1. Skapa VCL-logik för [AWS S3-autentisering](https://docs.fastly.com/en/guides/amazon-s3#using-an-amazon-s3-private-bucket).

1. Skapa VCL-logik för [backend-begäranden till AWS S3-bucket](https://developer.fastly.com/reference/vcl/variables/backend-connection/req-backend/).
