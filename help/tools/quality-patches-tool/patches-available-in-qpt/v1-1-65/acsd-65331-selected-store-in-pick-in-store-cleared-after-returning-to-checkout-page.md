---
title: 'ACSD-65331: Det valda arkivet i [!UICONTROL Pick in Store] har rensats efter återgång till kassan'
description: Använd korrigeringsfilen ACSD-65331 för att åtgärda Adobe Commerce-problemet där den valda butiken under alternativet [!UICONTROL Pick In Store] rensas när användare upprepade gånger återgår till utcheckningssidan.
feature: Inventory
role: Admin, Developer
type: Troubleshooting
exl-id: 10aaf898-feca-4485-90f6-6b3a9ea013b2
source-git-commit: dc5df9e918adffe8d6901478a676d9da36b33bcc
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---

# ACSD-65331: Det valda arkivet i **[!UICONTROL Pick in Store]** har rensats efter återgång till kassan

Korrigeringen ACSD-65331 åtgärdar ett problem där den valda butiken under alternativet **[!UICONTROL Pick In Store]** rensas när användare upprepade gånger återgår till utcheckningssidan. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.65 har installerats. Korrigerings-ID är ACSD-65331. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.9.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7-p3

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.7-p5

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Det valda arkivet under alternativet **[!UICONTROL Pick In Store]** rensas när användare upprepade gånger återgår till utcheckningssidan.

<u>Steg som ska återskapas</u>:

1. Aktivera **[!UICONTROL In-Store Delivery]** genom att gå till **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Delivery Methods]** > **[!UICONTROL In-Store Delivery]**.
1. Konfigurera en giltig [!DNL Google] API-nyckel för [!UICONTROL Google Distance Provider] genom att gå till **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Google Distance Provider]**.
1. Gå till **[!UICONTROL Stores]** > **[!UICONTROL Sources]** > **[!UICONTROL Add New Source]** om du vill lägga till en ny källa med följande information:

   * **[!UICONTROL Latitude]**: *41.917344*
   * **[!UICONTROL Longitude]**: *-88.102569*
   * **[!UICONTROL Use as Pickup Location]**: *Ja*
   * **[!UICONTROL Country]**: *USA*
   * **[!UICONTROL State]**: *Illinois*
   * **[!UICONTROL City]**: *Carol Stream*
   * **[!UICONTROL Street]**: *565 E. Fullerton Ave.*
   * **[!UICONTROL Postcode]**: *60188*

1. Gå till **[!UICONTROL Stores]** > **[!UICONTROL Stocks]** > **[!UICONTROL Add New Stock]** för att skapa en ny aktie.

   Tilldela den nya källan och huvudwebbplatsen till det här arkivet.
1. Redigera alla produkter och:

   1. Tilldela den till den nya källan.
   1. Ange status till *[!UICONTROL In Stock]* och kvantitet till större än 0.

1. Kör omindexerarna.
1. I butiken skapar du en ny kund och anger en adress i Kalifornien som standardadress för fakturering och leverans.
1. Lägg till ytterligare en Illinois-adress till samma kund (ej standard).
1. Lägg den konfigurerade produkten i kundvagnen och fortsätt till **[!UICONTROL Checkout]**.
1. Välj Illinois-adressen, välj **[!UICONTROL Pick In Store]** som leveransmetod och klicka på **[!UICONTROL Next]**.
1. Vänta tills källan har lästs in och klicka på **[!UICONTROL Next]**.
1. Gå tillbaka till hemsidan.
1. Gå till sidan **[!UICONTROL Checkout]** igen.

<u>Förväntade resultat</u>:

Det valda arkivet ska förbli tillgängligt under **[!UICONTROL Pick In Store]**.

<u>Faktiska resultat</u>:

Leveranssteget börjar läsas in och dirigeras om till **[!UICONTROL Pick In Store]**, men ingen butik visas.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
