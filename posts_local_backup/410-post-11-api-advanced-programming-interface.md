---
title: "Post #11 API Advanced Programming Interface"
date: 2025-02-21 10:45:24
author: Scripterix
slug: 11-post-api
post_id: 410
categories:
  - "Coding Corner"
  - "Wyzwanie"
tags:
  - "api"
  - "JSON"
original_url: "https://opengateweb.com/posts/11-post-api/"
---

## API - Advanced Programming Interface

Tworzę applikację gdzie będę zapisywał w JSON dane. Będzie to początkowo simple CRUD ale z API i na bazie frameworks Express. Będzie zabawnie aplikacja Teachers Grade logbook. Więcej w [poście #12](/posts/12-post-teachers/).

**API (Interfejs programowania aplikacji)**

API, czyli Interfejs Programowania Aplikacji, to zestaw reguł i protokołów, które pozwalają aplikacjom na komunikację ze sobą. Może to obejmować komunikację między różnymi komponentami w obrębie jednej aplikacji lub między różnymi aplikacjami działającymi na różnych platformach. API definiuje, jakie rodzaje żądań można wysyłać do systemu, jakie informacje można uzyskać oraz jak odpowiedzi są zwracane.

**Async/Await**

**Json-Server**

JSON-Server to narzędzie, które pozwala szybko stworzyć lokalny serwer HTTP, który obsługuje operacje CRUD (Create, Read, Update, Delete) na danych przechowywanych w formacie JSON. Jest to przydatne narzędzie do szybkiego prototypowania aplikacji lub testowania interfejsów API. Umożliwia ono definiowanie prostych plików JSON jako bazy danych, a następnie udostępnia je poprzez prosty interfejs HTTP, pozwalając na interakcję z nimi za pomocą standardowych żądań HTTP, takich jak GET, POST, PUT i DELETE.

** Express.js**

Express.js jest minimalistycznym i elastycznym frameworkiem aplikacji internetowych dla Node.js. Jest to jedno z najpopularniejszych narzędzi do tworzenia serwerów HTTP w środowisku Node.js. Express.js zapewnia prostą i intuicyjną warstwę abstrakcji nad wbudowanym modułem HTTP w Node.js, co ułatwia tworzenie aplikacji internetowych.

**Oto kilka kluczowych cech Express.js**

**Minimalizm** Express.js jest minimalistycznym frameworkiem, co oznacza, że dostarcza tylko podstawowe funkcje do obsługi żądań HTTP, ale jest równocześnie elastyczny i umożliwia rozbudowę za pomocą różnych wtyczek i middleware'ów.

**Routing** Express.js zapewnia proste i wydajne mechanizmy routingu, dzięki którym można definiować ścieżki URL i odpowiadające im funkcje obsługujące żądania HTTP.

**Middleware** Middleware w Express.js to funkcje, które są wywoływane sekwencyjnie przez aplikację Express.js w celu przetwarzania żądań HTTP. Pozwalają one na wykonywanie różnych operacji, takich jak uwierzytelnianie, logowanie, obsługa błędów, parsowanie ciała żądania i wiele innych.

**Obsługa szablonów** Express.js wspiera różne silniki szablonów, takie jak Pug (dawniej Jade), EJS, Handlebars, co ułatwia generowanie dynamicznych stron internetowych.

**Obsługa plików statycznych** Możliwość obsługi plików statycznych, takich jak pliki CSS, JavaScript, obrazy, itp., dzięki czemu można dostarczać zasoby statyczne do klienta.

**Wsparcie dla middleware'ów zewnętrznych** Istnieje wiele gotowych middleware'ów i wtyczek dostępnych dla Express.js, co pozwala na łatwe rozszerzanie funkcjonalności aplikacji.

**Express.js** jest często wykorzystywany do tworzenia zarówno prostych serwerów API, jak i zaawansowanych aplikacji internetowych, takich jak strony internetowe, aplikacje jednostronicowe (Single Page Applications - SPA), serwisy internetowe, i wiele innych. Dzięki swojej elastyczności, wydajności i rozbudowanej społeczności, Express.js pozostaje jednym z najpopularniejszych narzędzi w ekosystemie Node.js.

**Metody HTTP**

Oto kilka podstawowych metod HTTP:

****GET:**** Służy do pobierania danych z określonego zasobu na serwerze. Przesyła zapytanie do serwera w celu pobrania danych.

****POST:**** Służy do przesyłania danych do serwera w celu utworzenia lub aktualizacji zasobu. Często wykorzystywane do przesyłania formularzy lub wysyłania danych z aplikacji.

****PUT:**** Służy do aktualizacji zasobu na serwerze. Przesyła cały zasób do serwera, który ma zostać zaktualizowany.

****DELETE:**** Służy do usuwania zasobu na serwerze. Przesyła żądanie usunięcia określonego zasobu.

****PATCH:**** Służy do częściowej aktualizacji zasobu na serwerze. Jest podobny do metody PUT, ale aktualizuje tylko określone części zasobu.

****HEAD:**** Podobne do metody GET, ale serwer zwraca tylko nagłówki odpowiedzi bez samego zasobu. Często używane do sprawdzania statusu zasobu bez konieczności pobierania go w całości.

****OPTIONS:**** Służy do pobrania informacji o dostępnych metodach HTTP na danym zasobie. Często używane do sprawdzania, jakie metody są dozwolone dla danego zasobu.

****TRACE:**** Służy do diagnostyki, przesyłając żądanie z powrotem do klienta w celu zbadania zmian, jakie zaszły w trakcie przetwarzania przez serwer.

****CONNECT:**** Używane do ustanowienia tunelu do serwera, zazwyczaj używane w przypadku tunelowania zabezpieczonych połączeń, takich jak SSL.

To są podstawowe metody HTTP używane w komunikacji między klientem a serwerem.

W poście następnym rozwijam przykład prostej APP [Post #12](/posts/12-post-teachers/)
