---
title: "Post #50 Glide Jak zrobić kontent slider?"
date: 2025-04-10 16:34:10
author: Scripterix
slug: 50-glide
post_id: 970
categories:
  - "Design Hub"
  - "Wyzwanie"
tags:
  - "design-layout"
  - "front-end"
  - "tools"
original_url: "https://opengateweb.com/posts/50-glide/"
---

Kontent slider czy w innej nazwie karuzela to treść osadzona i serwująca różny kontent po przesunięciu strzałki lub automatycznie w wyznaczonym czasie.

## Jak Stworzyłem kontent slider za pomocą Glide.js

W mojej ostatniej przygodzie z frontendem postanowiłem zagłębić się w **Glide.js** i nauczyć się, jak zbudować slider, który będzie responsywny i prosty w implementacji. W tym wpisie podzielę się, jak dodałem zdjęcia, skonfigurowałem responsywność za pomocą @media, oraz jakie kroki pomogły mi zrozumieć tę bibliotekę.

## Co to Jest Glide.js?

[Glide.js](https://glidejs.com/) to lekka i szybka biblioteka JavaScript do tworzenia sliderów i karuzeli. Jest bardzo elastyczna, co oznacza, że możemy ją łatwo dostosować do własnych potrzeb - idealna do sliderów, które mają dobrze działać na różnych urządzeniach i ekranach.

## Przygotowanie Plików

Najpierw stworzyłem strukturę plików, która wyglądała następująco:

- **index.html** – główny plik HTML.

- **css/glide.core.css** oraz **css/glide.theme.css** – style biblioteki Glide.js.

- **glide.js** – główny plik JavaScript dla biblioteki.

- Folder **img** – zawierający zdjęcia, które chciałem dodać do slidera.

## Krok po Kroku: Tworzenie Slidera

### Krok 1: Dodanie HTML

W pliku index.html dodajemy podstawową strukturę slidera zgodnie z dokumentacją Glide.js. Wygląda to tak:

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Slider glide.js</title>
  <link rel="stylesheet" href="./css/glide.core.css">
  <link rel="stylesheet" href="./css/glide.theme.css">
</head>
<body>
  <div class="glide">
    <div class="glide__track" data-glide-el="track">
      <ul class="glide__slides">
        <li class="glide__slide"><img src="./img/20-superfoods-640.webp" alt="20 superfoods"></li>
        <li class="glide__slide"><img src="./img/3-domowe-naturalne-przeziebienie-640.webp" alt="Przeziębienie"></li>
        <li class="glide__slide"><img src="./img/ashwaganda-telomers-640.webp" alt="Ashwaganda"></li>
        <!-- Dodaj więcej zdjęć tutaj -->
      </ul>
    </div>
    <div class="glide__arrows" data-glide-el="controls">
      <button class="glide__arrow glide__arrow--left" data-glide-dir="<">Previous</button>
      <button class="glide__arrow glide__arrow--right" data-glide-dir=">">Next</button>
    </div>
    <div class="glide__bullets" data-glide-el="controls[nav]">
      <button class="glide__bullet" data-glide-dir="=0"></button>
      <button class="glide__bullet" data-glide-dir="=1"></button>
      <!-- Dodaj więcej przycisków w zależności od liczby slajdów -->
    </div>
  </div>
</body>
</html>

## W tym miejscu każdy li to pojedynczy slajd. Dodałem kilka zdjęć i dostosowałem ich alt, by były bardziej opisowe

- Krok 2: Konfiguracja JavaScript

- Podpięcie Glide.js jest proste

- Na końcu pliku index.html dodałem skrypt inicjujący slider:

<script src="./glide.js"></script>
<script>
  new Glide('.glide', {
    type: 'carousel',
    startAt: 0,
    perView: 4,
    breakpoints: {
      1200: { perView: 3 },
      800: { perView: 2 },
      480: { perView: 1 }
    }
  }).mount();
</script>

## W tej konfiguracji slider jest ustawiony jako karuzela (czyli po przewinięciu ostatniego zdjęcia wraca do pierwszego)

Ustawiłem również startAt na 0, co oznacza, że slider zaczyna od pierwszego zdjęcia. Najważniejsza część to breakpoints – dzięki nim slider dostosowuje się do szerokości ekranu:

- 1200px i więcej – wyświetlane są 4 slajdy.

- 800px do 1200px – wyświetlane są 3 slajdy.

- 480px do 800px – wyświetlane są 2 slajdy.

- poniżej 480px – wyświetlany jest 1 slajd.

## Krok 3: Responsywność i ustawienie CSS @media

Glide.js samo w sobie obsługuje breakpoints, ale dodałem też własne style CSS dla img, by zdjęcia zachowywały odpowiednie proporcje i były responsywne:

Skopiuj kod
.glide__slide img {
  width: 100%;
  height: auto;
}

## Dzięki temu zdjęcia dopasowują się do rozmiaru kontenera, niezależnie od szerokości ekranu

## Co Nauczyłem się Pracując z Glide.js?

- Prostota – Glide.js jest bardzo prosty w obsłudze, ale jednocześnie oferuje dużo możliwości konfiguracyjnych.

- Responsywność – dzięki breakpoints i CSS łatwo stworzyć slider, który świetnie wygląda zarówno na komputerze, jak i na telefonie. Łatwość rozbudowy – Glide.js pozwala na dodawanie różnych komponentów (np. przyciski nawigacyjne, wskaźniki), co sprawia, że jest wszechstronny.

## Podsumowanie

Stworzenie slidera za pomocą Glide.js to świetne doświadczenie dla każdego, kto dopiero uczy się frontendu i chce osiągnąć profesjonalne rezultaty przy minimalnym wysiłku. Cieszę się, że mogłem zrozumieć, jak działa ta biblioteka, i mam nadzieję, że ten przewodnik pomoże Wam stworzyć własny, responsywny slider.

Dajcie znać, jeśli macie pytania lub potrzebujecie pomocy – chętnie pomogę! Kliknijcie na [Facebook OpenGateweb](https://opengateweb.com/posts/autmn24/50-glide/)
