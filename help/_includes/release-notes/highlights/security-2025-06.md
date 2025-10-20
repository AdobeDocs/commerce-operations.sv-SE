---
source-git-commit: c71367c553dce66c146540389461f36eaa529bfc
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 0%

---
# Säkerhetsuppdateringar från juni 2025

Den här versionen innehåller följande högdagrar:

* **API-prestandaförbättring** - Åtgärdar prestandaförsämring i asynkrona webb-API-slutpunkter som introducerades efter den föregående säkerhetspatchen.<!-- AC-14078 -->

* **Åtkomstkorrigering för CMS Blockerar** - Åtgärdar ett fel där administratörsanvändare med begränsade behörigheter (till exempel tillgång för enbart försäljning) inte kunde visa listsidan för [!UICONTROL CMS Blocks].

  Tidigare påträffade dessa användare ett fel på grund av saknade konfigurationsparametrar efter installation av tidigare säkerhetsuppdateringar.<!-- AC-14087 -->

* **Kompatibilitet för cookie-begränsning** - Korrigerar en bakåtkompatibel ändring som involverar konstanten `MAX_NUM_COOKIES` i ramverket. Den här uppdateringen återställer förväntat beteende och säkerställer kompatibilitet för tillägg och anpassningar som interagerar med cookie-gränser.<!-- AC-14475 -->

* **Asynkrona åtgärder** - Begränsade asynkrona åtgärder för att åsidosätta tidigare kundorder.<!-- AC-13917 -->

* **Korrigering för CVE-2025-47110** - Åtgärdar en säkerhetslucka i e-postmallar.<!-- AC-14695 -->

>[!BEGINSHADEBOX]

Korrigeringen för CVE-2025-47110 finns även som en isolerad korrigeringsfil. Mer information finns i [kunskapsbasartikeln](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/security-update-available-for-adobe-commerce-apsb25-50).

>[!ENDSHADEBOX]