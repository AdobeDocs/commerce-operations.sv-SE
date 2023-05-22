---
title: Krav för distribution
description: Se en lista över förutsättningar för att distribuera Commerce till ett utvecklings-, bygg- eller produktionssystem.
feature: Configuration, Deploy
exl-id: 9ea0eeff-e0f8-4532-887c-5d7f07d89ddd
source-git-commit: dcc283b901917e3681863370516771763ae87462
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 0%

---

# Krav för utveckling, bygge och produktion av system

Filbehörigheter och ägarskap måste vara enhetliga i alla utvecklings-, bygg- och produktionssystem. För att detta ska fungera måste du antingen:

- Allt av följande:

   - Ställ in samma användarnamn för filsystemets ägare på alla system
   - Se till att webbservern körs som samma användare i alla system
   - Kontrollera att filsystemägaren finns i webbservergruppen på alla system

- Ändra behörigheter och ägarskap för Commerce-filsystem på varje system efter behov med hjälp av följande riktlinjer:

   - Utveckling och byggteknik: [Ange ägarskap och behörigheter före installation (två användare)](file-system-permissions.md#set-up-two-owners-for-default-or-developer-mode)
   - Produktion: [Äganderätt och tillstånd för handel inom utveckling och produktion](file-system-permissions.md)

>[!INFO]
>
>Om du väljer det här sättet måste du ange filsystembehörigheter och ägarskap varje gång du hämtar kod från ditt byggsystem (om filsystemets ägare eller webbserveranvändaren är olika på ditt byggsystem).
