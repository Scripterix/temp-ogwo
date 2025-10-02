---
title: "Post #47 Projekty wykonane"
date: 2025-04-07 00:14:57
author: Scripterix
slug: 47-telo-react
post_id: 944
categories:
  - "Ogólne"
  - "Wyzwanie"
tags:
  - "front-end"
  - "portfolio"
  - "react"
original_url: "https://opengateweb.com/posts/47-telo-react/"
---

Projekty wykonane - Telomers & React portfolio

Ostatnio zrealizowałem dwa projekty, które rozbudowały zarówno moje portfolio, jak i stronę Telomers.pl.

### 1. Trzy strony dla Telomers.pl

Dla serwisu **Telomers.pl** dodałem trzy nowe strony:

- **Poranne rozbudzanie**: Strona skupiająca się na zdrowych porannych rytuałach. [Poranne rytuały](https://telomers.pl/proces-rozbudzania)

- **Witaminy i Minerały na wiosnę**: Informacje na temat optymalnego doboru witamin i minerałów w sezonie wiosennym.[Witaminy Minerały Suplementy](https://telomers.pl/witaminy-i-mineraly-budulec-twojego-zdrowia)

- **3 domowe sposoby na przeziębienie**: Naturalne sposoby na walkę z przeziębieniem. [3 domowe spososby na przeziębienie](https://telomers.pl/3-domowe-sposoby-na-przeziebienie) Całość została wdrożona w krótkim czasie, a nowe treści są już dostępne dla użytkowników serwisu.

### 2. Aplikacja React Hooks

Stworzyłem również aplikację w **React**, która demonstruje wykorzystanie hooków takich jak useState, useEffect oraz useContext. Projekt polega na dynamicznej zmianie koloru tła oraz liczniku, który można zwiększać przyciskiem. W aplikacji zaimplementowane są funkcje:

- Obsługa zmiany wartości inputu z wykorzystaniem useState.

- Dynamiczna zmiana tła na podstawie wprowadzonego koloru w formacie HEX.

- Wykorzystanie kontekstu (useContext) do aktualizacji tła.

- Wyświetla licznik (Increment)

- Pozwala wpisać kolor w HEX i zmienia tło

- Używa Context API do przekazywania koloru do komponentów potomnych

Zobacz applikację [React](https://react-hooks.opengateweb.com/) i jej proste funkcje.

Poniżej fragment kodu aplikacji:

import React, { useState, useEffect, createContext, useContext } from 'react';

const BackgroundColorContext = createContext();

function App() {
  const [count, setCount] = useState(0);
  const [inputValue, setInputValue] = useState('#0e0e0e');
  const [bgColor, setBgColor] = useState('#0e0e0e');

  useEffect(() => {
    const isHex = /^#[0-9A-F]{6}$/i.test(inputValue) || /^#[0-9A-F]{3}$/i.test(inputValue);
    if (isHex) setBgColor(inputValue);
  }, [inputValue]);

  return (
    <BackgroundColorContext.Provider value={{ bgColor, setBgColor }}>
      <div style={{ backgroundColor: bgColor, padding: '20px', minHeight: '100vh' }}>
        <p>Count: {count}</p>
        <button onClick={() => setCount(count + 1)}>Increment</button>
        <input
          type="text"
          value={inputValue}
          onChange={(e) => setInputValue(e.target.value)}
          placeholder="Enter HEX color"
        />
        <BackgroundColorInput />
      </div>
    </BackgroundColorContext.Provider>
  );
}

function BackgroundColorInput() {
  const { setBgColor } = useContext(BackgroundColorContext);

  return (
    <input
      type="text"
      placeholder="Change background color"
      onChange={(e) => setBgColor(e.target.value)}
    />
  );
}

export default App;

Jeśli chcesz się dowiedzieć więcej jak stworzyć Applikację opartą na React może zobaczyć naszą sekcję Nauka Programowania React. React hooks nie jest najlpeszym przykładem do nauki i zrozumienia jak kodować React ale jeśli chcesz zobaczyć kod odwiedź [GH Repo](https://github.com/Scripterix).

## Całość zajęła 6 godzin i można zobaczyć efekty na telomers.pl i [porfolio](https://opengateweb.com/portfolio/)
