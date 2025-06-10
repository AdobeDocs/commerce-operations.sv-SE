---
source-git-commit: f9cc5ab0cb1b64455e12081ffbf719e0f2a791ad
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 0%

---
# Säkerhetsuppdateringar från juni 2025

Den här versionen innehåller följande högdagrar:

* **API-prestandaförbättring** - Åtgärdar prestandaförsämring i asynkrona webb-API-slutpunkter som introducerades efter den föregående säkerhetspatchen.<!-- AC-14078 -->

* **Åtkomstkorrigering för CMS Blockerar** - Åtgärdar ett fel där administratörsanvändare med begränsade behörigheter (till exempel tillgång för enbart försäljning) inte kunde visa listsidan för [!UICONTROL CMS Blocks].

  Tidigare påträffade dessa användare ett fel på grund av saknade konfigurationsparametrar efter installation av tidigare säkerhetsuppdateringar.<!-- AC-14087 -->

* **Kompatibilitet för cookie-begränsning** - Korrigerar en bakåtkompatibel ändring som involverar konstanten `MAX_NUM_COOKIES` i ramverket. Den här uppdateringen återställer förväntat beteende och säkerställer kompatibilitet för tillägg och anpassningar som interagerar med cookie-gränser.<!-- AC-14475 -->

* **Korrigering för CVE-2024-34104** - Åtgärdar ett fel i auktoriseringen.<!-- AC-13917 -->

* **Korrigering för CVE-2025-47110** - Åtgärdar en säkerhetslucka i e-postmallar.<!-- AC-14695 -->

* **Korrigering för VULN-31547** - Åtgärdar ett kategorifel med kanoniska länkar.<!-- AC-14713 -->

>[!BEGINSHADEBOX]

Korrigeringar för CVE-2025-47110 VULN-31547 finns också tillgängliga som en isolerad korrigering. Mer information finns i [kunskapsbasartikeln](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/security-update-available-for-adobe-commerce-apsb25-50).

>[!ENDSHADEBOX]
