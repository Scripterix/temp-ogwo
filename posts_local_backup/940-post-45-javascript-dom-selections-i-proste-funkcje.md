---
title: "Post #45 JavaScript DOM selections i proste funkcje"
date: 2025-04-05 05:59:03
author: Scripterix
slug: 45-js-dom
post_id: 940
categories:
  - "Coding Corner"
  - "Wyzwanie"
tags:
  - "dom"
  - "javascript"
  - "js dom"
  - "selectors"
original_url: "https://opengateweb.com/posts/45-js-dom/"
---

## Spis treści JS DOM Selections

- Wprowadzenie do Document Object Model

- Selekcja elementów

- [Q&A JS DOM ](#10.-Najczęstsze-pytania-i-problemy-z-DOM-–-Q&A)

## 1. Wprowadzenie – jak działa DOM w JavaScript i dlaczego to takie ważne?

Ten wpis to **praktyczny tutorial JavaScript DOM**, w którym zobaczysz, jak krok po kroku korzystać z selektorów i manipulować elementami na stronie. Jeśli zastanawiasz się, **jak działa DOM w JavaScript** i co możesz z nim zrobić, jesteś w dobrym miejscu.

DOM – czyli **Document Object Model** – to struktura, w której przeglądarka „widzi” naszą stronę. To właśnie dzięki niej możemy przy pomocy kodu:

- dynamicznie zmieniać treści (np. licznik w koszyku),

- budować **animacje w JS** i efekty wizualne,

- ukrywać, pokazywać i dodawać elementy na żywo (np. rozwijane menu),

- reagować na kliknięcia użytkownika,

- modyfikować style i klasy CSS bez przeładowania strony.

Ten **JavaScript DOM tutorial** pokaże Ci m.in.:

- jak zaznaczać elementy przy użyciu querySelector, getElementById, getElementsByClassName i innych selektorów DOM,

- jak tworzyć dynamiczne elementy (createElement, appendChild),

- jak budować **interaktywne funkcje w JavaScript**,

- jak podpiąć proste efekty i animacje JS do kliknięć i akcji użytkownika.

To nie jest tylko teoria – pokażę Ci **działające przykłady kodu JS**, które możesz od razu przetestować w swojej przeglądarce.

Przykład jak działa DOM i co możesz robić dzięki selektorom. Jak myśleć o DOM?  Prosty przykład, który całkowicie rozjaśnia temat

**Wyobraź sobie, że masz prosty HTML**

Strona zawiera elementy ( tagi )  html head body i w body tagi np H1 Jestem Tytułem i pod nim P jestem paragrafem i rozwijam w tym akapicie tytuł do DOM ( Data Object Model ) pozwoli zrobić taką akcję uchwyć za h1 i nadaj mu po najechaniu kolor z czarnego na niebieski

<body>
  <h1>Jestem tytułem</h1>
  <p>Jestem paragrafem i rozwijam w tym akapicie tytuł</p>
</body>

**DOM (Document Object Model)** pozwala nam „złapać” te elementy za pomocą JavaScriptu i coś z nimi zrobić.

Na przykład: chcesz, żeby tytuł h1 zmieniał kolor, gdy ktoś na niego najedzie kursorem.

Dzięki DOM możemy napisać prostą funkcję w JavaScript:

const header = document.querySelector("h1");

header.addEventListener("mouseover", () => {
  header.style.color = "blue";
});

header.addEventListener("mouseout", () => {
  header.style.color = "black";
});

I co się dzieje? Strona żyje! Kiedy użytkownik najedzie myszką na nagłówek, kolor zmienia się z czarnego na niebieski. DOM daje Ci **pełną kontrolę nad tym, jak strona reaguje na użytkownika**.

Tego właśnie dotyczy **manipulacja DOM JS** – łapanie elementów, zmienianie ich wyglądu, zawartości lub reakcji na kliknięcia. To fundament interaktywnych stron, gier, animacji JS i dynamicznych interfejsów.

## 2. Selekcja elementów

JavaScript oferuje kilka sposobów na wybieranie elementów z DOM:

### 2.1. getElementById (Selekcja po ID)

// Wybieranie elementu po jego ID
const element = document.getElementById('myElement');
console.log(element);

### 2.2. getElementsByClassName (Selekcja po klasie)

// Wybieranie wszystkich elementów z daną klasą (zwraca kolekcję)
const elements = document.getElementsByClassName('myClass');
console.log(elements);

### 2.3. getElementsByTagName (Selekcja po tagu)

// Wybieranie wszystkich elementów o danym tagu (np. wszystkie <p>)
const paragraphs = document.getElementsByTagName('p');
console.log(paragraphs);

### 2.4. querySelector (Pierwszy element pasujący do selektora CSS)

// Wybieranie pierwszego elementu, który pasuje do selektora CSS
const firstParagraph = document.querySelector('p');
console.log(firstParagraph);

2.5 Można używać bardziej złożonych selektorów

const elementById = document.querySelector('#myElement');
const elementByClass = document.querySelector('.myClass');
console.log(elementById, elementByClass);

### 2.6 querySelectorAll (Wszystkie elementy pasujące do selektora CSS)

// Wybieranie wszystkich elementów pasujących do selektora CSS
const allParagraphs = document.querySelectorAll('p');
console.log(allParagraphs);

// Selekcja bardziej złożona
const allDivsInContainer = document.querySelectorAll('#container div');
console.log(allDivsInContainer);

## 3. Manipulacja DOM w JavaScript – Tworzenie Dynamicznych Stron

![ JavaScript coding ](https://opengateweb.com/wp-content/uploads/2025/04/ChatGPT-Image-2-kwi-2025-01_55_56-1118x745.png)

JavaScript to język, który daje życie stronom internetowym! Dzięki niemu możemy nie tylko wyświetlać statyczne treści, ale także dynamicznie je zmieniać, reagować na interakcje użytkownika i budować nowoczesne aplikacje webowe.

Aby to osiągnąć, musimy zrozumieć **DOM (Document Object Model)** – czyli sposób, w jaki przeglądarka widzi strukturę HTML strony. DOM zamienia kod HTML w **drzewo obiektów**, dzięki czemu JavaScript może je modyfikować, usuwać lub dodawać nowe elementy w czasie rzeczywistym.

**Przykłady zastosowania manipulacji DOM w JavaScript:**Aktualizacja treści w czasie rzeczywistym (np. liczba lajków na przycisku)Tworzenie efektów wizualnych i animacjiObsługa dynamicznych formularzy i interakcji użytkownika Tworzenie gier i aplikacji webowych

Teraz zobaczmy, jak możemy manipulować DOM w JavaScript i jakie ciekawe rzeczy możemy zrobić! 

## **Lepsza praktyka – zamiast stylów w JavaScript, użyj klasy CSS**

We wprowadzeniu i pierwszym  przykładzie manipulowaliśmy style.color bezpośrednio w kodzie JS.  Jest to poprawne, ale **lepszym rozwiązaniem** jest przypisywanie klas CSS – oddzielamy wtedy logikę (JS) od wyglądu (CSS), co czyni kod bardziej przejrzystym i łatwiejszym w utrzymaniu.

1. Definiujemy klasę CSS w <style> lub osobnym pliku .css

.highlighted {
  color: blue;
}

2. JavaScript – dodajemy/ usuwamy klasę przy najechaniu myszką

const header = document.querySelector("h1");

header.addEventListener("mouseover", () => {
  header.classList.add("highlighted");
});

header.addEventListener("mouseout", () => {
  header.classList.remove("highlighted");
});

Ten sam efekt  zastosowania **JS DOM**– ale czyściej. Dlaczego to rozwiązanie jest lepsze?

- Możesz szybko zmienić styl w CSS bez ruszania JS

- Unikasz mieszania logiki z wyglądem

- Łatwiej ponownie użyć klas w innych miejscach

Takie podejście to podstawa profesjonalnego front-endu, nawet w prostych projektach. Przy okazji poznajesz dość często używaną konstrukcje **.addEventListener**

## 4. **Co to jest DOM i jak JavaScript go wykorzystuje?**

Wyobraź sobie, że HTML to szkielety budynku, a CSS to jego kolor i styl. JavaScript to robot, który może zmieniać wygląd budynku, dodawać okna, drzwi, a nawet przesuwać ściany.

Każdy element na stronie – nagłówek, paragraf, obrazek czy przycisk – jest w DOM reprezentowany jako **obiekt**, który możemy modyfikować przy pomocy JavaScriptu.

DOM wygląda jak drzewo, gdzie głównym elementem jest <html>, a jego gałęziami są <head> i <body>. Każdy kolejny element, jak <p>, <h1>, <div>, to kolejne węzły drzewa.

🎯 **Przykład wizualizacji drzewa DOM**:

php-templateKopiujEdytuj<html>
 ├── <head>
 │   ├── <title> Moja Strona </title>
 ├── <body>
 │   ├── <h1> Nagłówek </h1>
 │   ├── <p> Jakiś tekst </p>
 │   ├── <button> Kliknij mnie </button>

Dzięki JavaScript możemy manipulować tym drzewem – dodawać nowe elementy, zmieniać treści, a nawet usuwać elementy JS DOM! 

## 5. **Zmiana treści i atrybutów elementów**

Najprostsza manipulacja DOM to zmiana tekstu lub atrybutów elementów.

**Przykład – zmiana nagłówka i linku:**

document.getElementById("myTitle").textContent = "Nowy, dynamiczny nagłówek!";
document.getElementById("myLink").href = "https://developer.mozilla.org";
document.getElementById("myImage").src = "new-image.jpg";

**HTML do testowania:**

<h2 id="myTitle">Stary tytuł</h2>
<a id="myLink" href="#">Kliknij tutaj</a>
<img id="myImage" src="old-image.jpg" alt="Obrazek">

JavaScript sprawia, że strona zmienia się **bez potrzeby przeładowania!**

## 6. **Tworzenie nowych elementów w DOM**

Chcesz dodać nowy paragraf lub przycisk w locie? JavaScript to umożliwia!

**Przykład – dynamiczne dodawanie elementu:**

let newParagraph = document.createElement("p");
newParagraph.textContent = "To jest dynamicznie dodany paragraf!";
document.body.appendChild(newParagraph);

Dzięki temu możemy budować dynamiczne listy, generować karty produktów czy dodawać nowe wiadomości w czacie użytkownika.

## 7. **Zmiana stylów i klas CSS**

Możemy nie tylko zmieniać treści, ale też **wygląd elementów** poprzez style CSS.

**Przykład – zmiana koloru i rozmiaru tekstu:**

let newParagraph = document.createElement("p");
newParagraph.textContent = "To jest dynamicznie dodany paragraf!";
document.body.appendChild(newParagraph);

**Lepszy sposób – dodawanie klas CSS:**

document.getElementById("box").classList.add("highlight");

**CSS:**

cssKopiujEdytuj.highlight {
    background-color: yellow;
    border: 2px solid red;
}

Zamiast manipulować stylami w JavaScript, lepiej dodawać/usunąć klasy – to bardziej wydajne i czytelne!

## 8. **Obsługa zdarzeń użytkownika – interaktywne przyciski!**

JavaScript pozwala reagować na działania użytkownika, np. kliknięcia myszką, najechanie kursorem czy naciśnięcie klawisza.

**Przykład – reakcja na kliknięcie przycisku:**

document.getElementById("myButton").addEventListener("click", function() {
    alert("Kliknięto przycisk!");
});

**HTML do testowania:**

<button id="myButton">Kliknij mnie!</button>

Możemy dzięki temu tworzyć menu, interaktywne formularze czy nawet gry w JavaScript!

## 9. **Usuwanie elementów z DOM**

Czasem chcemy ukryć lub całkowicie usunąć element ze strony.

**Przykład – usunięcie elementu:**

document.getElementById("myParagraph").remove();

 **HTML do testowania:**

<p id="myParagraph">To zostanie usunięte!</p>

Można to wykorzystać np. do usuwania zadań na liście „to-do” lub zamykania okienek pop-up.

## 10. Najczęstsze pytania i problemy z DOM – Q&A

### **Czym właściwie jest DOM** - **js dom.**

DOM (Document Object Model) to reprezentacja strony internetowej w pamięci przeglądarki. Dzięki niej JavaScript może w czasie rzeczywistym:

- zmieniać teksty i obrazy,

- reagować na kliknięcia użytkownika,

- dodawać lub usuwać elementy,

- kontrolować strukturę całej strony.

Wyobraź sobie, że HTML to konstrukcja z klocków LEGO – DOM to mapa tych klocków, którą może modyfikować Twój kod.

### **Jak zacząć naukę DOM w JavaScript** -** *javascript DOM tutorial***

Najlepiej zacząć od prostych ćwiczeń – uchwycenia elementów za pomocą getElementById czy querySelector, a następnie zmiany ich treści lub stylu. DOM to struktura, która pozwala programiście „zobaczyć” elementy HTML jako obiekty. Dobry tutorial powinien pokazywać, jak:

- selekcjonować elementy (różnymi metodami),

- reagować na zdarzenia (np. kliknięcia),

- modyfikować strukturę strony w czasie rzeczywistym (dodawać, usuwać, zmieniać treść i atrybuty).

Praktyczne przykłady znajdziesz w Post #45 – JS DOM Selections i proste funkcje, gdzie pokazujemy manipulację nagłówkiem, tworzenie nowych paragrafów i przypisywanie klas.

### Co to znaczy manipulować DOM w JavaScript - **manipulacja DOM JS**

Manipulacja DOM to każda akcja wykonywana w JavaScript, która zmienia stronę bez jej przeładowania. Może to być:

- dynamiczne dodanie listy produktów po kliknięciu przycisku,

- zmiana treści nagłówka po wpisaniu czegoś w formularz,

- przypisanie nowej klasy CSS do zaznaczonego elementu.

To właśnie ta technika sprawia, że strony są „żywe”. W Post #45 pokazujemy manipulację z użyciem metod createElement, appendChild, textContent i classList. Dla tych, którzy chcą pójść dalej, polecamy [Post #46 – Anime.js i animacje DOM](https://opengateweb.com/posts/46-anime), gdzie te same elementy DOM służą jako podstawa do efektów wizualnych.

### Jak działa DOM w JavaScript – czyli co widzi przeglądarka - **jak działa DOM w JavaScript**

Kiedy przeglądarka ładuje dokument HTML, tworzy z niego wewnętrzne drzewo obiektów – DOM. JavaScript może to drzewo czytać, modyfikować i rozszerzać. Każdy element HTML – h1, p, div – staje się osobnym obiektem, który można „złapać” i zmienić jego właściwości.

To jak cyfrowy model budynku – JavaScript to inżynier, który przestawia drzwi, dodaje okna i zmienia kolor ścian bez potrzeby budowania wszystkiego od nowa. Jeśli chcesz zobaczyć taki przykład w praktyce, zobacz fragment z h1, który zmienia kolor po najechaniu – dokładnie to opisaliśmy w Post #45.

### Jakie są różnice między getElementById a querySelector?

MetodaTyp selektoraZwracagetElementByIdtylko idjeden elementquerySelectordowolny selektorpierwszy pasujący elementquerySelectorAlldowolny selektorkolekcję wszystkich

W praktyce querySelector jest bardziej uniwersalny – możesz go używać z klasami, tagami, a nawet złożonymi selektorami CSS (#header .logo p).

### Dlaczego mój kod getElementById zwraca null?

Najczęstsze przyczyny:

- Element o tym ID nie istnieje w HTML w momencie wykonywania skryptu.

- Skrypt jest umieszczony **przed** elementem w strukturze DOM – warto używać DOMContentLoaded.

- Literówka w ID – JavaScript jest czuły na wielkość liter.

Przykład poprawnej struktury:

## **Podsumowanie – Co dzięki temu zyskujemy?**

 Tworzymy **dynamiczne i interaktywne** strony internetowe Reagujemy na **akcje użytkownika**Zmieniamy treść i wygląd strony **bez przeładowania**Tworzymy **nowoczesne aplikacje webowe**

JavaScript i manipulacja DOM to **klucz do nowoczesnego front-endu**! 

Jeśli chcesz budować **interaktywne strony i aplikacje**, to musisz opanować manipulację DOM – a teraz masz solidne podstawy, by to robić! 

### Chcesz iść dalej? Zobacz, jak to robią biblioteki JavaScript

To, co właśnie poznałeś – selekcje i manipulacje DOM w czystym JavaScript – to podstawa. Ale warto wiedzieć, że wokół tego mechanizmu powstały całe **biblioteki animacyjne**, które robią jeszcze więcej, szybciej i efektowniej.

📌 W artykule [**Post #46 – Biblioteki do animacji z elementami w JavaScript – Anime.js** ](https://opengateweb.com/posts/46-anime/)pokazujemy, **jak łączyć DOM z efektami wizualnymi**: płynne przejścia, sekwencje animacji, reakcje na kliknięcia i wiele więcej.
