---
title: "Post #22 Wprowadzenie do API."
date: 2025-03-07 00:54:46
author: Scripterix
slug: 22-post-api
post_id: 578
categories:
  - "Wyzwanie"
tags:
  []
original_url: "https://opengateweb.com/posts/22-post-api/"
---

# **Wprowadzenie do API: Jak Komunikują się Aplikacje?**

Czy kiedykolwiek zastanawiałeś się, jak aplikacje na Twoim telefonie lub komputerze wymieniają się informacjami? Jak aplikacja pogodowa pobiera dane o temperaturze, a aplikacja do zamawiania jedzenia wie, jakie restauracje są otwarte? Odpowiedź brzmi: **API**.

## **Czym jest API? (Definicja i Podstawy)**

API (**Application Programming Interface**) to interfejs programowania aplikacji. Można go porównać do kelnera w restauracji – Ty (aplikacja) składasz zamówienie (żądanie), a on dostarcza Ci potrzebne danie (dane) z kuchni (serwera).

W świecie programowania API to zestaw reguł i protokołów umożliwiających różnym aplikacjom komunikację i wymianę danych.

## **Gdzie Spotkasz API?**

API są wszechobecne w dzisiejszym cyfrowym świecie. Oto kilka przykładów:

- **Aplikacje mobilne i webowe** – integracja z usługami takimi jak płatności online (np. PayPal), mapy (np. Google Maps), media społecznościowe (np. Facebook, Twitter) czy systemy zarządzania zapasami.

- **Internet rzeczy (IoT)** – komunikacja między inteligentnymi urządzeniami a chmurą.

- **Mikrousługi** – budowanie aplikacji z małych, niezależnych modułów, które komunikują się za pomocą API.

- **Automatyzacja procesów** – integracja różnych systemów w celu usprawnienia pracy.

## **Rodzaje API**

Istnieje kilka rodzajów API, z których każdy ma swoje unikalne cechy:

- **REST API (Representational State Transfer)** – najpopularniejszy rodzaj API, oparty na standardach HTTP, prosty i skalowalny.

- **SOAP API (Simple Object Access Protocol)** – starszy, bardziej złożony standard, często stosowany w systemach korporacyjnych.

- **RPC API (Remote Procedure Call)** – umożliwia zdalne wywoływanie funkcji na serwerze.

## **Metody HTTP: Język Komunikacji API**

API często wykorzystują protokół HTTP do wymiany danych. Oto najważniejsze metody:

- **GET** – pobiera dane z serwera.

- **POST** – wysyła nowe dane na serwer.

- **PUT** – aktualizuje istniejące dane.

- **DELETE** – usuwa dane.

### **Pobieranie danych za pomocą metody GET i fetch()**

W JavaScript można pobrać dane z API za pomocą funkcji fetch().

javascriptKopiujEdytujfetch('https://przykladoweapi.com/uzytkownicy') // Adres API
  .then(response => response.json()) // Parsowanie odpowiedzi do JSON
  .then(data => console.log(data)) // Wyświetlenie danych w konsoli
  .catch(error => console.error('Błąd:', error)); // Obsługa błędów

**Wyjaśnienie kodu:**

- fetch('https://przykladoweapi.com/uzytkownicy') – wysyła żądanie GET do API.

- .then(response => response.json()) – konwertuje odpowiedź do formatu JSON.

- .then(data => console.log(data)) – wyświetla otrzymane dane.

- .catch(error => console.error('Błąd:', error)) – obsługuje ewentualne błędy.

## **Dlaczego Warto Korzystać z API?**

- **Automatyzacja** – API umożliwiają integrację i automatyzację procesów.

- **Dane w czasie rzeczywistym** – dostęp do aktualnych informacji z różnych źródeł.

- **Bezpieczeństwo** – kontrola dostępu do danych.

- **Łatwość tworzenia aplikacji** – możliwość korzystania z gotowych usług.

## **Darmowe API – Gdzie Znaleźć?**

Wiele organizacji oferuje darmowe API, które można wykorzystać w swoich projektach:

- **API pogodowe** (np. OpenWeatherMap)

- **API jakości powietrza**

- **API do quizów i gier**

- **API danych geograficznych**

## **Narzędzia i Platformy Wspomagające Pracę z API**

- **Swagger, Postman** – testowanie i dokumentowanie API.

- **Zapier, Integromat** – łączenie różnych aplikacji i usług.

## **Tworzenie Własnego API w Express.js**

Jeśli chcesz stworzyć własne API, pomocny będzie **Express.js** – popularny framework Node.js.

### **Przykładowy serwer API w Express.js**

javascriptKopiujEdytujconst express = require('express');
const app = express();
const port = 3000;

app.get('/produkty', (req, res) => {
  const produkty = [
    { id: 1, nazwa: 'Laptop', cena: 2500 },
    { id: 2, nazwa: 'Myszka', cena: 50 },
  ];
  res.json(produkty);
});

app.listen(port, () => {
  console.log(`Serwer działa na porcie ${port}`);
});

Ten kod tworzy serwer, który zwraca listę produktów w formacie JSON po wysłaniu żądania GET na /produkty.

## **Podsumowanie**

API to fundament współczesnych aplikacji, umożliwiający wymianę danych i integrację usług. Mam nadzieję, że ten artykuł pomógł Ci zrozumieć podstawy API oraz sposoby ich wykorzystania w praktyce. W aplikacji Teachers Grade Book zastosowałem [Express.JS i metody API zobacz](https://opengateweb.com/posts/15-post-app-teachers-2/).
