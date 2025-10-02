---
title: "Post #12 App Teachers Grade logbook"
date: 2025-02-23 03:22:32
author: Scripterix
slug: 12-post-teachers
post_id: 507
categories:
  - "Wyzwanie"
tags:
  []
original_url: "https://opengateweb.com/posts/12-post-teachers/"
---

**API - App Teachers Grade logbook**

**Rozwinięcie funkcjonalności aplikacji na podstawie dostarczonych założeń:**

**Serwer (server.js)**

Ten plik w języku JavaScript wykorzystuje framework Express do tworzenia punktów końcowych API.

Punkty te obsługują operacje CRUD (Create - Tworzenie, Read - Odczyt, Update - Aktualizacja, Delete - Usuwanie) na danych dotyczących studentów.

Oprócz obsługi API, serwer dostarcza również statyczne pliki HTML, CSS i JavaScript dla interfejsu użytkownika.

**Struktura strony klienckiej (public/)**

Ten folder zawiera statyczne pliki stanowiące interfejs użytkownika aplikacji, są to kolejno:

- index.html Główna strona widoczna dla użytkownika, wyświetlająca listę studentów oraz obsługująca formularz kreacji nowego studenta.

- edit.html Strona zawierająca formularz do edycji informacji o danym studencie. Funkcja Create

- main.js Plik JavaScript obsługujący interakcję z serwerem poprzez wywołania API.

**Logika**

Pobieranie danych o studentach za pomocą żądań "fetch".

Aktualizuje istniejących danych lub dodanie nowego wpisu.

Odpowiada za aktualizację interfejsu użytkownika na podstawie odpowiedzi serwera.

**Magazynowanie danych (logbook.json)**

Ten plik przechowuje dane dotyczące studentów w formacie JSON. JSON ****(JavaScript Object Notation)**** to sposób reprezentacji struktur danych, takich jak listy i obiekty, w formacie czytelnym dla ludzi. Kod serwerowy odczytuje informacje z tego pliku, aby wyświetlać studentów, a także zapisuje wszelkie aktualizacje lub nowe wpisy.

**Kompilowanie (webpack.config.js)**

Skończona app będzie spakowana w JS. Ten plik jest opcjonalny, będzie dopisany na koniec CRUD. Czym jest Webpack? Webpack to narzędzie do zarządzania i kompilowania kodu JavaScript po stronie klienta. Kompilowanie łączy wszystkie oddzielne pliki JavaScript w jeden zoptymalizowany plik. Poprawia to wydajność i ułatwia zarządzanie kodem.

**Ogólne założenia App**

Ogólnie rzecz biorąc, ta struktura aplikacji tworzy prostą aplikację CRUD do zarządzania danymi dotyczącymi studentów. Serwer obsługuje przechowywanie i logikę danych, podczas gdy interfejs strony klienckiej umożliwia użytkownikom wyświetlanie, edytowanie i potencjalne usuwanie informacji o studentach.

**Dodatkowe uwagi**

Powyższy opis jest ogólnym zarysowaniem funkcjonalności. Dokładna implementacja może się różnić w zależności od konkretnych wymagań aplikacji.

Zastanawiam się nad dodaniem mechanizmów uwierzytelniania i autoryzacji, aby chronić dane studentów przed nieuprawnionym dostępem i dla formułu praktyki.

Zaimplementowanie responsywnego wyglądu strony internetowej może zapewnić optymalne wrażenia użytkownika na różnych urządzeniach. Realizacja przez Bootstrap.

Dokumentacja kodu ułatwi innym zrozumienie i rozwijanie aplikacji w przyszłości. Mozna to sprawdzić na stronie About applikacji lub na GitHub.

** GitHub commands practice**

Od dobrej powtórki GitHub czyli Git versjononowanie i praca z repozytorium większość projektów jest przesyłana na GitHub lub tworzone są Gist do ponownego wykorzystania.

[Git Hub Repositorium](https://github.com/Scripterix/crud-express-json)

[Więcej objaśnień w post #13](/posts/13-post-crud/)
