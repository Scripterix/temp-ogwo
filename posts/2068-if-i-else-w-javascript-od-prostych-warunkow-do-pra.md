---
title: "If i Else w JavaScript – od prostych warunków do praktycznych aplikacji"
date: 2025-09-21 18:39:36
author: Scripterix
slug: if-i-else-w-javascript-od-prostych-warunkow-do-praktycznych-aplikacji
post_id: 2068
categories:
  - "Coding Corner"
  - "Wyzwanie"
tags:
  - "javascript"
  - "js dom"
  - "programming"
original_url: "https://opengateweb.com/posts/if-i-else-w-javascript-od-prostych-warunkow-do-praktycznych-aplikacji/"
---

## **If i Else w JavaScript Post #74** **dowiedz się o instrukcjach warunkowych. **

## Spis treści

- [Dlaczego instrukcje warunkowe są potrzebne](#Dlaczego-instrukcje-warunkowe-są-potrzebne)

- [Pierwszy krok – najprostszy if w konsoli](#Pierwszy-krok-najprostszy-if-w-konsoli)

- [Jak działają typy i dlaczego to ważne](#Jak-działają-typy-i-dlaczego-to-ważne)

- [Od konsoli do UI – podpinanie warunku do interfejsu](#Od-konsoli-do-UI-podpinanie-warunku-do-interfejsu)

- [Przykład 1 – walidator liczby (index.html)](#Przykład-1-walidator-liczby)

- [Przykład 2 – kalkulator kosztu przejazdu (fuel.html)](#Przykład-2-kalkulator-kosztu-przejazdu)

- [Przykład 3 – kontrola prędkości (speed.html)](#Przykład-3-kontrola-prędkości)

- [Najczęstsze błędy i dobre praktyki](#najcz%C4%99stsze-b%C5%82%C4%99dy-i-dobre-praktyki)

- [Q&A – szybkie odpowiedzi](#qa--szybkie-odpowiedzi)

- [Jak uruchomić przykłady](#jak-uruchomić-przykłady-if)

- [Podsumowanie](#Podsumowanie-If)

## Dlaczego instrukcje warunkowe są potrzebne

Każdy program potrzebuje podejmować decyzje. Jeśli użytkownik poda liczbę, sprawdź, czy jest większa od 100. Jeśli prędkość przekracza 120 km/h, ostrzeż o ryzyku, podano prawidłowe hasło i login **access = granted**. Instrukcja if to sposób na powiedzenie komputerowi: „zrób coś tylko wtedy, gdy warunek jest spełniony”.

***A co, jeśli warunek nie jest spełniony?***Wtedy wchodzi else – alternatywna ścieżka.

## Pierwszy krok – najprostszy if w konsoli

Pierwszy przykład można uruchomić w konsoli przeglądarki (F12 → Console). Utwórz dowolny plik html lub js w VSC i zapoznaj się ze składnią.

const isLoggedIn = true;

if (isLoggedIn) {
  console.log("Witaj ponownie!");
} else {
  console.log("Zaloguj się!");
}

***Dlaczego to działa tak prosto?***Bo isLoggedIn to zmienna logiczna (true albo false). if sprawdza jej wartość i wybiera odpowiednią gałąź.

## Jak działają typy i dlaczego to ważne

Często dane z formularza przychodzą jako tekst. Nawet liczba „120” wpisana w polu <input> to string.  Funkcja wbudowana Number(...) próbuje przekonwertować wartość wejściową na **typ number** (liczbę w JS). Jest kilka innych sposobów ale skupienie na **IF**

const raw = "120";
const n = Number(raw); // konwersja na liczbę

***A co, jeśli ktoś wpisze literki?***Wtedy Number("abc") zwróci NaN. Dlatego potrzebna jest walidacja. Choć zazwyczaj ustawia się **input** na typ **number**. Zobaczysz to w późniejszym przykładzie.

if (Number.isNaN(n)) {
  console.log("To nie jest liczba.");
}

## Od konsoli do UI – podpinanie warunku do interfejsu

Warunki są najbardziej praktyczne, gdy podpinamy je do elementów strony: pól formularza, przycisków, komunikatów.  Ustawienie type="number" powoduje że formularz przyjmuje liczby i ma skalę do powiększania/zmniejszania wartości myszą.

<input id="value" type="number" placeholder="Podaj liczbę">
<button id="run">Sprawdź</button>
<p id="out"></p>

<script>
  const input = document.getElementById("value");
  const out   = document.getElementById("out");
  document.getElementById("run").addEventListener("click", () => {
    const n = Number(input.value);
    if (Number.isNaN(n)) {
      out.textContent = "To nie jest liczba.";
    } else if (n > 100) {
      out.textContent = "Większa niż 100.";
    } else {
      out.textContent = "Mniejsza lub równa 100.";
    }
  });
</script>

***A czy muszę zawsze używać przycisku?***Nie. Możesz reagować na naciśnięcie Enter lub nawet na każdą zmianę pola, ale przycisk jest najprostszy na start.

## Przykład 1 – walidator liczby (walidator.html)

Plik **walidator.html** sprawdza, czy podana wartość to liczba, czy jest parzysta, i porównuje ją do 100.

Kluczowa funkcja:

function analyzeNumber(raw) {
  if (raw === '' || raw === null || raw === undefined) {
    return { cls: 'err', lines: ['Wpisz jakąś wartość.'] };
  }
  const n = Number(raw);
  if (Number.isNaN(n)) {
    return { cls: 'err', lines: ['To nie jest poprawna liczba.'] };
  }

  const parity = (Number.isInteger(n) && n % 2 === 0) ? 'parzysta'
                : (Number.isInteger(n) ? 'nieparzysta' : 'niecałkowita');
  const gt100  = n > 100 ? 'większa niż 100' : (n === 100 ? 'równa 100' : 'nie większa niż 100');

  return {
    cls: n > 100 ? 'ok' : 'warn',
    lines: [
      `Wprowadzono: ${raw}`,
      Number.isInteger(n) ? `Parzystość: ${parity}` : `Typ: ${parity}`,
      `Porównanie do 100: ${gt100}`
    ]
  };
}

***Dlaczego najpierw sprawdzamy pustą wartość, a potem liczbę?***Bo inaczej Number('') zwróci 0, co wprowadziłoby w błąd. Walidacja musi być krok po kroku.

## Przykład 2 – kalkulator kosztu przejazdu (fuel.html)

Plik **fuel.html** liczy koszt przejazdu z uwzględnieniem dystansu, spalania i ceny paliwa.

function analyzeTrip(d, c, p) {
  if (!d || !c || !p) {
    return { cls: 'err', lines: ['Wpisz wszystkie dane'] };
  }
  const liters = (d * c) / 100;
  const cost = liters * p;

  let msg, cls;
  if (cost < 50) {
    msg = 'Tani przejazd';
    cls = 'ok';
  } else if (cost < 150) {
    msg = 'Średni koszt';
    cls = 'warn';
  } else {
    msg = 'Drogo';
    cls = 'err';
  }

  return {
    cls,
    lines: [
      `Dystans: ${d} km`,
      `Zużycie paliwa: ${liters.toFixed(1)} l`,
      `Koszt: ${cost.toFixed(2)} zł`,
      msg
    ]
  };
}

***A co, jeśli chcę też policzyć czas przejazdu?***Dodaj pole na prędkość średnią i oblicz czas jako dystans / prędkość. Wtedy możesz dodać kolejny warunek i ostrzeżenie.

## Przykład 3 – kontrola prędkości (speed.html)

Plik **speed.html** pokazuje pełną ścieżkę warunków: dokładne wartości (===) i zakresy (>, <, >=, <=).

Fragment:

if (speed === 50) {
  message = "Idealnie 50 km/h – wzorowo w mieście.";
  cls = "ok";
} else if (speed > 50 && speed < 90) {
  message = "Od 51 do 89 km/h – poza miastem.";
  cls = "warn";
} else if (speed >= 90 && speed < 140) {
  message = "Od 90 do 139 km/h – droga ekspresowa.";
  cls = "warn";
} else if (speed >= 140 && speed <= 200) {
  message = "Od 140 do 200 km/h – autostrada, bardzo ryzykownie.";
  cls = "err";
} else if (speed > 240 && speed <= 300) {
  message = "Od 240 do 300 km/h – ekstremalna prędkość.";
  cls = "err";
} else {
  message = `${speed} km/h – poza naszymi regułami.`;
  cls = "warn";
}

***Dlaczego sprawdzamy dokładne wartości przed zakresami?***Bo inaczej warunek zakresu złapałby je wcześniej i blok dokładny nigdy by się nie wykonał.

## Najczęstsze błędy i dobre praktyki

- Zaczynaj od walidacji wejścia.

- Stosuj === i !==, aby unikać pułapek związanych z typami.

- Układaj warunki w logicznej kolejności – od szczegółowych do ogólnych albo odwrotnie, ale spójnie.

- Rozdzielaj logikę (analiza) od prezentacji (renderowanie w UI).

- Nie komplikuj na starcie – wystarczy kilka operatorów porównania.

## Q&A – szybkie odpowiedzi

**Czy if to jedyna możliwość?**Nie. Istnieje też switch i operator warunkowy ? :, ale if jest najprostszy na początek.

**Czy muszę znać wszystkie operatory?**Nie. Wystarczą >, <, >=, <=, ===, !== i czasem &&, ||.

**Co się stanie, jeśli źle ustawię kolejność warunków?**Niektóre bloki nigdy się nie wykonają. Dlatego ważne jest myślenie krokami i testowanie różnych danych.

**Dlaczego używamy === zamiast ==?**=== porównuje wartość i typ, == tylko wartość i może powodować niespodzianki.

**Czy można używać if bez else?**Tak. Jeśli interesuje nas tylko reakcja na spełniony warunek, wystarczy sam if. else jest opcjonalne i stosuje się je, gdy potrzebujemy alternatywnej ścieżki.

**Czy if działa tylko z liczbami?**Nie. if działa z każdą wartością, którą JavaScript potrafi sprowadzić do true/false. To mogą być liczby, stringi, obiekty, a nawet same booleany. Warto jednak wiedzieć, że np. pusty string "", liczba 0 czy null traktowane są jako fałsz.

**Jaka jest różnica między == a === w warunkach?**== porównuje tylko wartości i automatycznie konwertuje typy (np. "5" == 5 da true). === jest bardziej rygorystyczny – sprawdza zarówno wartość, jak i typ. Dlatego w praktyce bezpieczniej używać ===.

**Czy można zagnieżdżać if-y?**Tak. Możesz w jednym if umieścić kolejny, ale gdy logika robi się zbyt skomplikowana, lepiej użyć else if lub osobnej funkcji, aby kod pozostał czytelny.

**Kiedy lepiej użyć switch zamiast wielu if-ów?**switch sprawdza wiele możliwych wartości jednej zmiennej i pozwala uniknąć długiego łańcucha else if. Jest czytelny, gdy porównujemy jeden element do kilku konkretnych opcji, np. dni tygodnia.

## Jak uruchomić przykłady z If?

- Zapisz pliki if-else.html, **walidator.html**, fuel.html, speed.html w jednym folderze. Możesz też zrobić git clone repozytorium z GitHub [https://github.com/Scripterix/if-else-javascript](https://github.com/Scripterix/if-else-javascript)

- Otwórz w przeglądarce.

- Możesz też robić dowolne eksperymenty z przykładami.

## Podsumowanie

Instrukcje warunkowe to fundament programowania. Od prostego if w konsoli, przez walidację danych w formularzu, aż po rozbudowane przykłady jak kalkulator paliwa czy kontrola prędkości – wszystkie opierają się na jednej zasadzie: *sprawdź warunek i podejmij decyzję*.
