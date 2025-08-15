---
source-git-commit: 6ca34e8713f4f138961786de206cd360f0bc1be7
workflow-type: tm+mt
source-wordcount: '131'
ht-degree: 0%

---
# Säkerhetsuppdateringar från februari 2025

Den här versionen innehåller följande högdagrar:

* **Hantera krypteringsnycklar och kryptera om data** - Omdesignad hantering av krypteringsnycklar för att förbättra användbarheten och eliminera tidigare begränsningar och fel.<!-- AC-12679 -->

  Nya CLI-kommandon finns nu tillgängliga för [ändring av](https://experienceleague.adobe.com/sv/docs/commerce-admin/systems/security/encryption-key)-nycklar och [omkryptering](https://developer.adobe.com/commerce/php/development/security/data-encryption/) av vissa systemkonfigurationer, betalningar och anpassade fältdata. Det finns inte längre stöd för att ändra nycklar i administratörsgränssnittet i den här versionen. Du måste använda CLI-kommandona.

* **Korrigera för [CVE-2025-24434](https://nvd.nist.gov/vuln/detail/CVE-2025-24434)** - Åtgärdar ett auktoriseringsfel.

  Den här korrigeringen finns även som en isolerad korrigering. Mer information finns i [kunskapsbasartikeln](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/security-update-available-for-adobe-commerce-apsb25-08).<!-- AC-12755 -->

* **Nedgradering av TinyMCE-version** - TinyMCE-beroendet har nedgraderats från version 7 till 6.8.5 för att åtgärda problem med licensieringskompatibilitet.

  Ändringen säkerställer fortsatt efterlevnad medan Adobe utvärderar en alternativ WYSIWYG-redigerare med öppen källkod.
