---
title: "Jak używać React Hooks w 2025 – przykłady i najlepsze praktyki Post #69."
date: 2025-08-24 21:53:36
author: Scripterix
slug: react-hooks-w-2025
post_id: 1799
categories:
  - "Coding Corner"
  - "Wyzwanie"
tags:
  - "react"
original_url: "https://opengateweb.com/posts/react-hooks-w-2025/"
---

## React Hooks krok po kroku – przykłady useEffect, useState i własnych hooków. Naucz się praktycznie stosować React w projektach.

Przewodnik po React Hooks: useState, useEffect i useContext

## Wprowadzenie

React **Hooks** to funkcje, które pozwalają „zahaczyć się” w mechanizmy Reacta takie jak stan komponentów czy cykl życia bez potrzeby pisania klas. Oficjalna dokumentacja opisuje hooki jako *„nowy dodatek w React 16.8, który umożliwia korzystanie ze stanu i innych funkcji Reacta bez pisania klasy*. Są one wstecznie kompatybilne i sprawiają, że logikę komponentów można wydzielać do niewielkich, wielokrotnego użytku funkcji.

Jednym z głównych hooków jest **useState**, który zwraca parę: aktualną wartość stanu oraz funkcję służącą do jej aktualizacji. Hook **useEffect** pozwala wykonywać efekty uboczne (np. manipulacje DOM‑u, zapytania sieciowe) po każdym renderowaniu komponentu. Zapoznaj się z dockumentacją [legacy.reactjs.org](https://legacy.reactjs.org/docs/hooks-overview.html#:~:text=The%20Effect%20Hook%2C%20,in%20Using%20the%20Effect%20Hook). Hook **useContext** daje natomiast możliwość odczytywania wartości kontekstu i subskrybowania się na jego zmiany bez przekazywania propsów przez kolejne warstwy drzewa komponentów [react.dev](https://react.dev/reference/react/useContext#:~:text=useContext).

Jeśli chcesz zobaczyć jak aplikacja wykonuje Hooks - odwiedź stronę portfolio i aplikację [https://react-hooks.opengateweb.com/](https://react-hooks.opengateweb.com/) aplikacja jest zbudowana tak aby odwzorowywała poniższy tutorial React. 

## Spis treści

- [useState – prosty licznik](#sgdsladjsdjasd-hooks)

- [useEffect – zmiana koloru na podstawie danych wejściowych](#adfgahfgdsfalasgd-useEffect)

- [useContext – udostępnianie koloru w całym drzewie komponentów](#gdddoooagsajla-useContext)

## useState prosty licznik

Przykład na stronie demonstracyjnej wyświetla napis **“Count: 0”** i przycisk **“Increment”**

react-hooks.opengateweb.com. Kliknięcie przycisku zwiększa wartość licznika. Kod poniżej pokazuje, jak zrealizować takie zachowanie z użyciem hooka useState

import React, { useState } from 'react';

function Counter() {
  // deklarujemy zmienną stanu i funkcję ją aktualizującą
  const [count, setCount] = useState(0);

  // funkcja obsługująca kliknięcie
  const handleIncrement = () => {
    setCount((prevCount) => prevCount + 1);
  };

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={handleIncrement}>Increment</button>
    </div>
  );
}

**Omówienie**

- useState przyjmuje wartość początkową (0) i zwraca tablicę [wartość, setWartość]

- Wywołanie setCount powoduje ponowne wyrenderowanie komponentu z aktualną wartością stanu.

- Funkcja aktualizująca może przyjmować funkcję zwrotną otrzymującą poprzednią wartość stanu, co jest bezpieczne w przypadku wielu szybkich aktualizacji.

Taki prosty licznik jest typowym wprowadzeniem do hooka useState. Można używać wielu zmiennych stanu w jednym komponencie, deklarując useState kilkukrotnie[legacy.reactjs.org](https://legacy.reactjs.org/docs/hooks-overview.html#:~:text=).

![react-hooks krok po kroku](https://opengateweb.com/wp-content/uploads/2025/07/image-4.jpg)

## useEffect – zmiana koloru na podstawie danych wejściowych

Drugi przykład prezentowany na stronie pozwala użytkownikowi wpisać kod koloru w formacie szesnastkowym. Po wpisaniu wartości w pole tekstowe (z podpowiedzią **“Input hex color…”**) pod spodem pojawia się napis **“Wprowadzone dane:”** z bieżącą wartością pola![](https://sdmntprpolandcentral.oaiusercontent.com/files/00000000-6048-620a-9dec-5888b9d471a6/raw?se=2025-08-23T22%3A52%3A36Z&sp=r&sv=2024-08-04&sr=b&scid=01c3d9a3-de78-582f-adde-cb4a7330bb1a&skoid=76024c37-11e2-4c92-aa07-7e519fbe2d0f&sktid=a48cca56-e6da-484e-a814-9c849652bcb3&skt=2025-08-23T08%3A21%3A47Z&ske=2025-08-24T08%3A21%3A47Z&sks=b&skv=2024-08-04&sig=djXm2WBfD8Lr5/1hqlwI8x4L6FpGaqP6vSYtTu8EXyM%3D)react-hooks.opengateweb.com. Możemy napisać komponent, który wykorzystuje useEffect, aby reagować na zmianę tekstu i aktualizować kolor tła:

import React, { useState, useEffect } from 'react';

function ColorInput() {
  // stan przechowujący aktualny tekst i kolor tła
  const [inputValue, setInputValue] = useState('');
  const [color, setColor] = useState('');

  useEffect(() => {
    // wyrażenie regularne sprawdzające format #RGB lub #RRGGBB
    const hexRegex = /^#[0-9A-Fa-f]{3}$|^#[0-9A-Fa-f]{6}$/;
    if (hexRegex.test(inputValue)) {
      setColor(inputValue);
    }
  }, [inputValue]); // efekt uruchomi się po każdej zmianie inputValue

  return (
    <div style={{ backgroundColor: color, padding: '1rem' }}>
      <input
        type="text"
        placeholder="Input hex color..."
        value={inputValue}
        onChange={(e) => setInputValue(e.target.value)}
      />
      <p>Wprowadzone dane: {inputValue}</p>
    </div>
  );
}

**Omówienie**

- useEffect służy do wykonywania **efektów ubocznych** – operacji, które wykraczają poza czysty rendering (np. zmiany w DOM‑ie, zapytania do API). Dokumentacja tłumaczy, że efekt hook **„dodaje możliwość wykonywania efektów ubocznych z funkcyjnego komponentu”**[ Dokumenty ](https://legacy.reactjs.org/docs/hooks-overview.html#:~:text=The%20Effect%20Hook%2C%20,in%20Using%20the%20Effect%20Hook)[legacy.reactjs.org](https://legacy.reactjs.org/docs/hooks-overview.html#:~:text=The%20Effect%20Hook%2C%20,in%20Using%20the%20Effect%20Hook).

- W powyższym kodzie efekt uruchamia się za każdym razem, gdy zmieni się inputValue (zdefiniowane w tablicy zależności). Gdy użytkownik wpisze poprawny kod koloru, aktualizujemy stan color, co powoduje zmianę tła.

- Pole tekstowe kontrolowane jest przez React – jego wartość jest związana ze stanem inputValue, a każda zmiana wyzwala funkcję setInputValue.

Dzięki useEffect można w prosty sposób reagować na zmiany stanu i wykonywać akcje, które w klasowych komponentach wymagałyby użycia componentDidMount/ c7omponentDidUpdate/ componentWillUnmount.

## useContext – udostępnianie koloru w całym drzewie komponentów

Ostatni przykład demonstruje wykorzystanie hooka useContext. Na stronie widzimy pole z podpowiedzią **“Input color formatted #ddd or #dddddd…”** oraz listę przykładowych kolorów: **#000000 – black, #78b257 – green, #ea0e3a – red, #0000ff – blue, #ffffff – white**. Celem jest umożliwienie ustawienia koloru tła w jednym miejscu i udostępnienie go wszystkim komponentom potomnym.

import React, { useState, useContext, createContext } from 'react';

// tworzymy kontekst ze wstępną wartością domyślną
const ThemeContext = createContext('#ffffff');

function ThemeProvider({ children }) {
  const [color, setColor] = useState('#ffffff');
  return (
    <ThemeContext.Provider value={{ color, setColor }}>
      {children}
    </ThemeContext.Provider>
  );
}

function ColorInput() {
  // pobieramy funkcję setColor z kontekstu
  const { setColor } = useContext(ThemeContext);

  const handleChange = (e) => {
    const value = e.target.value;
    // dopuszczamy format #RGB lub #RRGGBB
    const hexRegex = /^#[0-9A-Fa-f]{3}$|^#[0-9A-Fa-f]{6}$/;
    if (hexRegex.test(value)) {
      setColor(value);
    }
  };

  return (
    <input
      type="text"
      placeholder="Input color formatted #ddd or #dddddd..."
      onChange={handleChange}
    />
  );
}

function ColorBox() {
  // pobieramy aktualny kolor z kontekstu
  const { color } = useContext(ThemeContext);
  return (
    <div style={{ backgroundColor: color, padding: '1rem' }}>
      Aktualny kolor kontekstu: {color}
    </div>
  );
}

export default function App() {
  return (
    <ThemeProvider>
      <ColorInput />
      <p>Przykładowe kolory tła:</p>
      <ul>
        <li>#000000 – black</li>
        <li>#78b257 – green</li>
        <li>#ea0e3a – red</li>
        <li>#0000ff – blue</li>
        <li>#ffffff – white</li>
      </ul>
      <ColorBox />
    </ThemeProvider>
  );
}

**Omówienie**

- Hook useContext pozwala **„czytać i subskrybować kontekst z poziomu komponentu”** Omówienie w docs zjadziesz tutaj - [react.dev](https://react.dev/reference/react/useContext#:~:text=useContext). Wywołujemy go na najwyższym poziomie funkcji komponentu, przekazując obiekt kontekstu utworzony wcześniej za pomocą createContext.

- W powyższym przykładzie ThemeProvider udostępnia parę color/setColor wszystkim komponentom potomnym. Funkcja ColorInput odczytuje setColor z kontekstu i pozwala użytkownikowi ustawić kolor podając wartość w odpowiednim formacie.

- Komponent ColorBox korzysta z tej samej wartości kontekstu, aby ustawić kolor tła. Dzięki temu zmiana w jednym miejscu propaguje się automatycznie do wszystkich elementów korzystających z tej wartości.

- Hook useContext zawsze zwraca **wartość przekazaną do najbliższego providera** w drzewie komponentów React. Jeżeli provider nie istnieje, zwracana jest wartość domyślna podana przy tworzeniu kontekstu.

## Podsumowanie

Hooki w React są potężnym narzędziem, które ułatwia organizację logiki w komponentach funkcyjnych. W tym przewodniku poznaliśmy trzy podstawowe hooki:

- **useState** – pozwala dodać lokalny stan do komponentu funkcjonalnego. Przykładowy licznik z przyciskiem „Increment” ilustruje jego działaniereact-hooks.opengateweb.com.

- **useEffect** – umożliwia wykonywanie efektów ubocznych po renderowaniu. W przykładzie zmienia tło na podstawie wpisanego kodu kolorureact-hooks.opengateweb.com.

- **useContext** – pozwala przekazywać dane do wielu komponentów bez przekazywania propsów w głąb drzewa. Dzięki niemu komponenty mogą odczytywać i aktualizować wspólny stan tematyczny. Zobacz docs [react.dev](https://react.dev/reference/react/useContext#:~:text=useContext).

Zaprezentowany kod można wykorzystać jako bazę do tworzenia bardziej rozbudowanych aplikacji React, w których potrzebne jest zarządzanie stanem, reagowanie na zmiany czy udostępnianie danych pomiędzy komponentami.
