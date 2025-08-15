---
title: Aktivera eller inaktivera moduler
description: Följ de här stegen för att hantera Adobe Commerce-moduler.
exl-id: 7155950a-a66a-4254-a71c-1a9aeab47606
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '572'
ht-degree: 0%

---

# Aktivera eller inaktivera moduler

Det här kommandot har inga krav.

## Modulstatus

Använd följande kommando för att lista aktiverade och inaktiverade moduler:

```bash
bin/magento module:status [--enabled] [--disabled] <module-list>
```

Plats

* `--enabled` visar alla aktiverade moduler.
* `--disabled` visar alla inaktiverade moduler.
* `<module-list>` är en blankstegsavgränsad lista med moduler som kontrollerar statusen. Om ett modulnamn innehåller specialtecken omger du namnet med enkla eller dubbla citattecken.

>[!NOTE]
>
>Du kan inte aktivera eller inaktivera moduler direkt i molnprojekt. Du måste köra dessa kommandon lokalt och sedan skicka ändringarna till filen `app/etc/config.php` för en miljö. Se [Projektarbetsflöde för Pro: Arbetsflöde för distribution](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/pro-develop-deploy-workflow.html#deployment-workflow).

## Aktivera modul, inaktivera

Använd följande kommando om du vill aktivera eller inaktivera tillgängliga moduler:

```bash
bin/magento module:enable [-c|--clear-static-content] [-f|--force] [--all] <module-list>
```

```bash
bin/magento module:disable [-c|--clear-static-content] [-f|--force] [--all] <module-list>
```

Plats

* `<module-list>` är en utrymmesavgränsad lista med moduler som ska aktiveras eller inaktiveras. Om ett modulnamn innehåller specialtecken omger du namnet med enkla eller dubbla citattecken.
* `--all` om du vill aktivera eller inaktivera alla moduler samtidigt.
* `-f` eller `--force` för att tvinga en modul att aktiveras eller inaktiveras trots beroenden. Se [Om att aktivera och inaktivera moduler](#about-enabling-and-disabling-modules) innan du använder det här alternativet.
* `-c` eller `--clear-static-content` rensar [genererade statiska vyfiler](../../configuration/cli/static-view-file-deployment.md).

  Om det inte går att rensa statiska vyfiler kan det uppstå problem om det finns flera filer med samma namn och du inte rensar alla.

  På grund av de [statiska återgångsreglerna](../../configuration/cli/static-view-file-deployment.md) kan med andra ord fel fil visas om du inte rensar statiska filer och det finns mer än en fil med namnet `logo.svg` som är annorlunda.

Om du till exempel vill inaktivera modulen `Magento_Weee` anger du:

```bash
bin/magento module:disable Magento_Weee
```

Viktig information om att aktivera och inaktivera moduler finns i [Om att aktivera och inaktivera moduler](#about-enabling-and-disabling-modules).

## Uppdatera databasen

Om du har aktiverat en eller flera moduler kör du följande kommando för att uppdatera databasen:

```bash
bin/magento setup:upgrade
```

Rensa sedan cacheminnet:

```bash
bin/magento cache:clean
```

## Aktivera och inaktivera moduler

Med Adobe Commerce kan du aktivera eller inaktivera tillgängliga moduler, dvs. alla Adobe-moduler eller tredjepartsmoduler som är tillgängliga.

Vissa moduler är beroende av andra moduler. I så fall kanske du inte kan aktivera eller inaktivera en modul eftersom den är beroende av andra moduler.

Dessutom kan det finnas *moduler som är i konflikt* som inte kan aktiveras samtidigt.

Exempel:

* Modul A är beroende av modul B. Du kan inte inaktivera modul B om du inte först inaktiverar modul A.

* Modul A är beroende av modul B, som båda är inaktiverade. Du måste aktivera modul B innan du kan aktivera modul A.

* Modul A står i konflikt med modul B. Du kan inaktivera modul A och modul B, eller så kan du inaktivera någon av modulerna, men du *kan inte* aktivera modul A och modul B samtidigt.

* Beroenden deklareras i fältet `require` i Adobe Commerce `composer.json`-filen för varje modul. Konflikter deklareras i fältet `conflict` i modulens `composer.json`-filer. Vi använder den informationen för att skapa ett beroendediagram: `A->B` innebär att modul A är beroende av modul B.

* En *beroendekedja* är sökvägen från en modul till en annan. Om modul A till exempel är beroende av modul B och modul B är beroende av modul C, är beroendekedjan `A->B->C`.

Om du försöker aktivera eller inaktivera en modul som är beroende av andra moduler visas beroendediagrammet i felmeddelandet.

>[!NOTE]
>
>Det är möjligt att modul A:s `composer.json` deklarerar en konflikt med modul B, men inte omvänt.

*Endast kommandorad:* Använd det valfria argumentet `--force` om du vill tvinga en modul att aktiveras eller inaktiveras oavsett dess beroenden.

>[!NOTE]
>
>Om du använder `--force` kan du inaktivera din butik och orsaka problem med åtkomsten till administratören.
