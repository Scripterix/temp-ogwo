---
title: "Post #51 DB Test PHP MySql Apps"
date: 2025-04-11 18:08:37
author: Scripterix
slug: 51-db-test
post_id: 974
categories:
  - "Coding Corner"
  - "Wyzwanie"
tags:
  - "crud"
  - "data-base"
  - "php"
  - "portfolio"
  - "programming"
original_url: "https://opengateweb.com/posts/51-db-test/"
---

DB Test PHP MySql Apps to prosta aplikacja z zapisem do bazy w środowisku lokalnym. Tworzę projekt edukacujnie i do portfolio. Będzie zawierał dobrą dokumentację jak to przećwiczyć na swoim środowisku lokalnym.

## Fukcjonalność jeszcze nieokkreślona

Obecnie zawiera tablicę users służącą do logowania - uproszonego bez potwierdzania mailowego. Pole Bio użytkownika do edycji oraz sesję i drobny feauture pokazujący w Toast ile jest zalogowanych użytkowników.

## Dokumentacja Techniczna

- **Konfiguracja Projektu**

Aby uruchomić projekt lokalnie, wykonałem następujące kroki:

- Pobrałem i zainstalowałem XAMPP (lub inny lokalny serwer) na swoim komputerze.

- Utworzyłem folder dla swojego projektu w katalogu htdocs (np. phpsandbox/test-baza).

- Skopiowałem wszystkie pliki projektu, w tym index.php, register.php, login.php i about.php, do tego folderu.

- Uruchomiłem Apache i MySQL w panelu sterowania XAMPP.

- W przeglądarce przeszedłem do [//localhost:3000/phpmyadmin](https://localhost:3000/phpmyadmin), aby skonfigurować bazę danych.

## **Konfiguracja Bazy Danych**

Aby skonfigurować bazę danych MySQL i utworzyć niezbędne tabele, wykonałem następujące kroki:

Utworzyłem nową bazę danych o nazwie baza_test_login_data. W tej bazie danych utworzyłem tabelę o nazwie users z następującymi kolumnami: id - INT, klucz główny, autoinkrementacja firstName - VARCHAR(50), imię użytkownika secondName - VARCHAR(50), nazwisko użytkownika email - VARCHAR(100), unikalny, adres e-mail użytkownika password - VARCHAR(255), hasło bio - TEXT, opcjonalne pole na biografię użytkownika

## **Rejestracja Użytkownika**

Plik register.php obsługuje rejestrację użytkownika. Działa w następujący sposób:

Gdy użytkownik przesyła formularz rejestracyjny, jego dane wejściowe są walidowane, aby upewnić się, że wszystkie pola są wypełnione. Skrypt sprawdza, czy adres e-mail już istnieje w bazie danych. Jeśli tak, wyświetlane jest ostrzeżenie. Jeśli adres e-mail jest unikalny, dane użytkownika są zapisywane, a wyświetlany jest komunikat o sukcesie. Hasło jest przechowywane w postaci haszowanej dla bezpieczeństwa, przy użyciu funkcji password_hash().

## **Logowanie Użytkownika**

Plik login.php umożliwia zalogowanie zarejestrowanym użytkownikom:

Po przesłaniu formularza, adres e-mail i hasło są walidowane względem bazy danych. Jeśli dane uwierzytelniające są poprawne, użytkownik otrzymuje dostęp. Dla bezpieczeństwa funkcja password_verify() jest używana do porównania hasła haszowanego z bazą danych.

## **Walidacja i Alerty**

Aby poprawić doświadczenie użytkownika, dodałem alerty Bootstrap dla komunikatów zwrotnych:

Alert sukcesu: Wyświetlany, gdy użytkownik pomyślnie się zarejestruje. Alert ostrzeżenia: Wskazuje, że adres e-mail jest już używany podczas rejestracji. Alert błędu: Wyświetlany, jeśli wystąpi błąd podczas rejestracji.

## **Pliki Kodu i Ich Funkcje**

index.php - Strona główna aplikacji. register.php - Zawiera formularz rejestracyjny i logikę PHP do dodawania użytkowników do bazy danych. login.php - Obsługuje logowanie użytkownika i uwierzytelnianie. about.php - Strona dokumentacji technicznej (ta strona). db.php - Zawiera kod połączenia z bazą danych przy użyciu mysqli. menu.php - Pasek nawigacyjny zawarty na każdej stronie dla łatwej nawigacji.

## **Przykładowy Kod Połączenia z Bazą Danych**

Poniżej znajduje się przykład kodu używanego do połączenia z bazą danych w db.php:

// ...
$conn = mysqli_connect($servername, $username, $password, $dbname);

// Check connection
if (!$conn) {
    die("Connection failed: " . mysqli_connect_error());
}
// ...

- Bezpieczeństwo i Najlepsze Praktyki

Hasła są haszowane przed przechowywaniem w bazie danych dla bezpieczeństwa. Pole e-mail jest unikalne w bazie danych, zapobiegając duplikatom rejestracji. Używane są przygotowane zapytania, aby zapobiec iniekcji SQL. Dla dodatkowego bezpieczeństwa należy rozważyć implementację SSL i zarządzania sesjami użytkowników.
