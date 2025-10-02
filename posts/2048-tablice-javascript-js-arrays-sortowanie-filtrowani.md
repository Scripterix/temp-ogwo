---
title: "Tablice JavaScript JS Arrays – sortowanie, filtrowanie i średnia ocen krok po kroku. Post #73"
date: 2025-09-09 20:23:59
author: Scripterix
slug: tablice-javascript-js-arrays-sortowanie-filtrowanie-i-srednia-ocen-krok-po-kroku
post_id: 2048
categories:
  - "Coding Corner"
  - "Wyzwanie"
tags:
  - "js dom"
  - "programming"
original_url: "https://opengateweb.com/posts/tablice-javascript-js-arrays-sortowanie-filtrowanie-i-srednia-ocen-krok-po-kroku/"
---

## Jak sortować tablice w JavaScript. Średnia ocen w tablicy JS.

## Spis treści

- Wprowadzenie – dlaczego akurat tablice w JavaScript

- Demo użytkowników – jak działa nasz przykład

- Błąd w sortowaniu – co poszło nie tak

- Refaktoryzacja – jedno obliczenie, wiele użyć

- Wyniki i testy – co się zmieniło

- Kolejne kroki – co można dodać jeszcze

- QA – najczęściej zadawane pytania

## Wprowadzenie – dlaczego akurat tablice w JavaScript

Tablice to serce pracy z danymi w JS. Gdy masz listę ocen studentów, zamówień w sklepie czy po prostu kolekcję liczb, to właśnie tablica pozwala je przefiltrować, posortować i podsumować.

W tym przykładzie zbudowaliśmy mini-aplikację, która prezentuje **listę sześciu użytkowników** z losowymi identyfikatorami i ocenami. To nasz poligon do nauki metod map, filter, reduce i sort.

## Demo użytkowników – jak działa nasz przykład

Na stronie array.html pojawia się tabela z użytkownikami. Mamy tam:

- imię i nazwisko,

- 16-cyfrowy identyfikator (badgeId),

- listę ocen,

- oraz średnią.

Poniżej funkcja generująca BadgeID oraz tablica. W tej funkcji znajduje się więcej dlatego nie ma domknięcia. Całość przykładu w repozytorium [GitHub JS Arrays](https://github.com/Scripterix/Array-JS)

// Helper: generate 16-digit numeric string
    function generateBadgeId() {
      return Array.from({ length: 16 }, () => Math.floor(Math.random() * 10)).join('');
    }

    // Helper: average of number array
    function avg(arr) {
      return arr.length ? Math.round(arr.reduce((s, v) => s + v, 0) / arr.length) : 0;
    }

    // Prepare 6 users (deterministic names, badgeId random, marks random)
    const users = [
      { userFirstName: 'Alice', userSecondName: 'Johnson', badgeId: generateBadgeId(), marks: [78, 85, 91, 69, 72] },
      { userFirstName: 'Ben', userSecondName: 'Martinez', badgeId: generateBadgeId(), marks: [55, 62, 58, 70, 60] },
      { userFirstName: 'Carla', userSecondName: 'Nguyen', badgeId: generateBadgeId(), marks: [92, 88, 95, 90, 93] },
      { userFirstName: 'Daniel', userSecondName: 'Smith', badgeId: generateBadgeId(), marks: [40, 52, 47, 35, 50] },
      { userFirstName: 'Eva', userSecondName: 'Khan', badgeId: generateBadgeId(), marks: [81, 79, 85, 77, 83] },
      { userFirstName: 'Felix', userSecondName: 'Brown', badgeId: generateBadgeId(), marks: [66, 70, 64, 68, 72] }
    ];

Do tego dochodzą przyciski:

- **Render Users** – wyświetla tabelę,

- **Run Examples** – pokazuje w konsoli użycie metod tablicowych,

- **Filter** – wybiera np. dobrych uczniów (avg ≥ 75),

- **Sort** – alfabetycznie po imieniu lub po średniej ocen.

## Błąd w sortowaniu – co poszło nie tak

Pierwotna wersja kodu miała drobny problem:średnia była liczona **na bieżąco w kilku miejscach** (avg(u.marks)), przez co sortowanie potrafiło zwracać różne wyniki albo działało wolniej.

Przykład:

const sorted = currentList.slice().sort((a, b) => avg(a.marks) - avg(b.marks));

Taki zapis sprawia, że dla każdego porównania funkcja avg liczy od nowa całą tablicę ocen.

## Refaktoryzacja – jedno obliczenie, wiele użyć

Rozwiązanie? **Precompute** – policzyć raz, a potem korzystać wiele razy.

Dodaliśmy więc właściwość avgMark:

users.forEach(u => { 
  u.avgMark = avg(u.marks); 
});

Od tego momentu:

- filtrowanie (good vs help),

- sortowanie (rosnąco/malejąco),

- podsumowanie średnich,

- logi w konsoli (runExamples)

korzystają zawsze z tej jednej wartości. Dzięki temu sortowanie jest spójne i szybsze.

## Wyniki i testy – co się zmieniło

Przyciski działają stabilnie:

- **Sort by First Name** układa listę poprawnie od A do Z,

- **Sort by Average** zawsze pokazuje kolejność od najlepszego studenta w dół,

- **Filter** nie gubi logiki i używa tych samych danych co reszta,

- **Summary** wyświetla najlepszą osobę i średnią całej grupy, a jeśli klikniemy kogoś na stronie głównej (index.html), to podświetli się na zielono.

Testy w DevTools (F12 → Console) pokazują też przykłady metod map, reduce i find.

## Kolejne kroki – co można dodać jeszcze

- **Przełącznik kierunku sortowania** (A→Z / Z→A).

- **Ikony strzałek** przy nagłówkach tabeli.

- **Mini testy jednostkowe** sprawdzające, czy wyniki są zawsze zgodne z oczekiwaniami.

- **Pokazanie mediany** obok średniej dla ciekawszego porównania.

## QA – najczęściej zadawane pytania

**Czy trzeba zawsze dodawać nową właściwość (avgMark) do obiektu?**Nie, można też tworzyć nowe obiekty (immutability). Tutaj uprościliśmy zapis dla czytelności i wydajności.

**Czy sortowanie w JS jest stabilne?**Od ES2019 tak – czyli jeśli dwie osoby mają identyczną średnią, zachowają kolejność wejściową.

**Dlaczego reduce jest używany tak często w przykładach?**Bo pozwala z listy ocen zrobić jedną liczbę – sumę albo średnią – w bardzo elegancki sposób.

Przykład omawiany powyżej możesz pobrać i modyfikować z repozytorium **[Scripterix na GitHub JS Arrays](https://github.com/Scripterix/Array-JS).** To naprawdę mały projekt, ale idealny do nauki. Jeśli chcesz wynieść z niego coś więcej niż tylko kliknięcie w przyciski, spróbuj:

- **Modyfikować dane wejściowe** – dodaj nowych użytkowników albo zmień oceny i zobacz, jak zmienia się wynik sortowania i filtrowania.

- **Dopisać nowe metody tablicowe** – np. some, every, slice.

- **Refaktorować kod** – spróbuj inaczej policzyć średnią albo dodać medianę.

- **Budować na małych krokach** – każdy commit w repo to mały eksperyment, który przybliża Cię do zrozumienia JavaScript.

Takie mikroprojekty najlepiej sprawdzają się, gdy regularnie je rozwijasz i **wrzucasz na GitHub** – dzięki temu tworzysz portfolio i ślad swojej nauki, a nie tylko „pamięć w głowie”.
