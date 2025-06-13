---
title: 'ACSD-50512: Fel vid uppdatering av startdatum för en hämtningsbar mellanlagringsuppdatering'
description: Använd korrigeringsfilen ACSD-51892 för att åtgärda prestandaproblemet i Adobe Commerce där felet *Den hämtningsbara länken inte är relaterad till produkten.Kontrollera länken och försök igen*, som inträffar när du uppdaterar startdatumet för en hämtningsbar mellanlagringsuppdatering.
feature: Products, Staging
role: Admin
exl-id: 9c3b4d45-c500-46a7-8679-a8aa9e0a66d6
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# ACSD-50512: Fel vid uppdatering av startdatum för hämtningsbar mellanlagringsuppdatering

Korrigeringen ACSD-50512 åtgärdar ett problem där felet *Den hämtningsbara länken inte är relaterad till produkten. Verifiera länken och försök igen*, inträffar när startdatumet för en hämtningsbar mellanlagringsuppdatering för produkten uppdateras. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.33 har installerats. Korrigerings-ID är ACSD-51502. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Felet *Den hämtningsbara länken är inte relaterad till produkten. Verifiera länken och försök igen*, inträffar när startdatumet för en hämtningsbar mellanlagringsuppdatering för produkten uppdateras.

<u>Steg som ska återskapas</u>:

1. Skapa en nedladdningsbar produkt med *nedladdningsbara länkar* och *exempellänkar*.
1. Skapa en schemalagd uppdatering för samma produkt och spara produkten.
1. Redigera den förkonfigurerade schemalagda uppdateringen (från steg 2) och ändra startdatumet.
1. Spara den schemalagda uppdateringen.

<u>Förväntade resultat</u>:

Ändringarna i den schemalagda uppdateringen har sparats.

<u>Faktiska resultat</u>:

Du får felmeddelandet: *Den hämtningsbara länken är inte relaterad till produkten. Verifiera länken och försök igen*.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
