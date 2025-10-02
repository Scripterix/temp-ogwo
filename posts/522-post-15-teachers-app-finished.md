---
title: "Post #15 Teachers App Finished"
date: 2025-02-27 07:10:00
author: Scripterix
slug: 15-post-app-teachers-2
post_id: 522
categories:
  - "Coding Corner"
  - "Wyzwanie"
tags:
  - "api"
  - "crud"
  - "Express.js"
  - "teachers grade book"
original_url: "https://opengateweb.com/posts/15-post-app-teachers-2/"
---

## Teachers App Finished

Aplikacja ma pełną funkcjonalność CRUD. Została dodana do repozytorium jako nowy branch - z dopiskiem finished.

## Kilka słów o logice działania

- **Gradebook:** Jak działa, jeśli nie czytałeś poprzednich [postów](https://opengateweb.com/wpisy/) Applikacja Teacher's Grade book jest zrobiona z API studnetów i pliku logbook.json oraz Express.js Java Script i Bootsrap.

- **CRUD:** na pierwszej stronie są dodane rekordy i wyświetlone w tabeli poniżej. Jest formularz do dodawania nowego studenta Imię Ocena ( A, B etc) oraz Wiek.

- **Po dodaniu:** wyświetla się potwierdzenie oraz uaktulanienie tabeli. W tabeli jest klikalna ikona "Edit-Pencil", która pobiera wybrane dane według uuid i przenosi na stronę Edycji. Dane są do poprawienia i zatwierdzenia. Tu znajduje się także przycisk Delete.

- **Tech:** Express i plik logbook.json zapisują i manipulują metodami. Dodatkowo Id jest tworzone automatycznie dzięki uuid. Zastosowałem metodę reload oraz redirect po kliknięciu Dismiss alertu z powiadomieniem.

## API i Express

Duże objaśniejie developerskie i rozwiązania manipulacji metodami znajdują się pliku **readme.MD** w repozytorium Scripterix w branch **"finished"** Branch main był zrobiony częściowo. [GitHub Repo Teacher's -b finished](https://github.com/Scripterix/crud-express-json/tree/finished) Metody API jakie są stosowane w Express.JS są omawiane w [Post #22 API.](https://opengateweb.com/posts/22-post-api/)

## Jestem zadowolony z pierwszego samodzielnego CRUD

Oparcie Crud na API i endpointach dla danych mniej wrażliwych lub ogólnych i tworzenie warstwy Backendowej i Front-Endowej daje dużo frajdy i jest wielościeżkowe w sensie podejścia. Można wszystko zorganizować na kilka sposobów. **Creativissimo**

## App Teacher's Grade logbook rozwinięcie

Planuje albo użyć Webpack i zrobić "bundle" aby umieścić Appkę w Portfolio lub zastosować i poznać się lepiej z Docker'em. Jeśli chcesz poznać kod aplikacji zapraszam do **[Repo](https://github.com/Scripterix/crud-express-json/tree/finished)**.
