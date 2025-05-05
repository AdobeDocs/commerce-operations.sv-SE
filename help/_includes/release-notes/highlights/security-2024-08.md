---
source-git-commit: b63fa9a8b2b59f6e8dfd7003e75c66caf99d5e81
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 0%

---
# Säkerhetsuppdateringar från augusti 2024

Den här versionen innehåller följande högdagrar:

* **Hastighetsbegränsning för[!DNL one-time passwords]** - Följande nya systemkonfigurationsalternativ finns nu tillgängliga för att aktivera hastighetsbegränsning vid [!DNL two-factor authentication (2FA)] [!DNL one-time password (OTP)] -validering:

   * [!UICONTROL **Gräns för nya försök för tvåfaktorsautentisering**]
   * [!UICONTROL **Tvåfaktorautentisering, utelåsningstid (sekunder)**]

  Adobe rekommenderar att man ställer in ett tröskelvärde för 2FA-validering av engångslösenord för att begränsa antalet nya försök att mildra brutna attacker. Mer information finns i [Säkerhet > 2FA](https://experienceleague.adobe.com/sv/docs/commerce-admin/config/security/2fa) i _referenshandboken för konfiguration_. <!-- AC-12095 -->

* **Rotation av krypteringsnyckel** - Nu finns ett nytt CLI-kommando tillgängligt för ändring av krypteringsnyckeln. Mer information finns i artikeln [Troubleshooting Encryption Key Rotation (Felsökning av krypteringsnyckelrotation): CVE-2024-34102](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/troubleshooting-encryption-key-rotation-cve-2024-34102) i kunskapsbasen.

* **Korrigera för [CVE-2020-27511](https://nvd.nist.gov/vuln/detail/CVE-2020-27511)** - Åtgärdar ett [!DNL Prototype.js] säkerhetsproblem.<!-- AC-11936 -->

* **Korrigera för [CVE-2024-39397](https://nvd.nist.gov/vuln/detail/CVE-2024-39397)** - Åtgärdar ett säkerhetslucka för fjärrexekvering av kod. Säkerhetsluckan påverkar handlare som använder webbservern Apache för lokala eller självhanterade distributioner. Den här korrigeringen finns även som en isolerad korrigering. Mer information finns i artikeln [Säkerhetsuppdatering för Adobe Commerce - APSB24-61](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/security-update-available-for-adobe-commerce-apsb24-61) i kunskapsbasen.<!-- ACSD-60551 -->
