---
source-git-commit: b63fa9a8b2b59f6e8dfd7003e75c66caf99d5e81
workflow-type: tm+mt
source-wordcount: '154'
ht-degree: 0%

---
# Oktober 2024 säkerhetsuppdateringar i korthet

Den här versionen innehåller följande högdagrar:

* **TinyMCE-uppgradering** - [WYSIWYG-redigeraren](https://experienceleague.adobe.com/sv/docs/commerce-admin/content-design/wysiwyg/editor) i Admin använder nu den senaste versionen av TinyMCE-beroendet (7.3-&#x200B;).

   * TinyMCE 7.3 ger en förbättrad användarupplevelse, bättre samarbete och ökad effektivitet. TinyMCE 5 har tagits bort från versionslinjen 2.4.8. &#x200B;

   * Eftersom ett säkerhetsproblem ([CVE-2024-38357](https://nvd.nist.gov/vuln/detail/CVE-2024-38357)) rapporterades i TinyMCE 5.10, uppgraderades beroendet för alla versionsrader som stöds och inkluderades i alla säkerhetspatchar från oktober 2024:

      * 2.4.7-p3
      * 2.4.6-p8
      * 2.4.5-p10
      * 2.4.4-p11

* **Require.js-uppgradering** - Adobe Commerce använder nu den senaste versionen av Require.js (2.3.7).

   * Eftersom ett säkerhetsproblem ([CVE-2024-38999](https://nvd.nist.gov/vuln/detail/CVE-2024-38999)) rapporterades i Require.js 2.3.6, uppgraderades beroendet för alla versionsrader som stöds och inkluderades i alla säkerhetspatchar från oktober 2024:

      * 2.4.7-p3
      * 2.4.6-p8
      * 2.4.5-p10
      * 2.4.4-p11

>[!NOTE]
>
>Dessa uppdateringar är bakåtkompatibla och bör inte påverka anpassningar och tillägg. &#x200B;
