---
title: "Post #9 Calculator Math Func OOP"
date: 2025-02-15 06:31:24
author: Scripterix
slug: 9-post-calc
post_id: 281
categories:
  - "Coding Corner"
tags:
  - "functions"
  - "oop"
  - "procedruralne"
original_url: "https://opengateweb.com/posts/9-post-calc/"
---

**Prosty Calculator - funkcjonalne i obiektowe podejście**

W tym przykładzie nieśmiertelnego kalkulatora zrobiłem podejście typowo Funkcjonalne i Obiektowe. W pliku JavaScript main-function.js znajdują się logi konsoli a także przykłady Person w wersji **constructor** oraz **class**.

[GitHub Calculator Repo](https://github.com/Scripterix/calculator-funck-oop)  

let input1 = document.getElementById('input1');
let input2 = document.getElementById('input2');
let input3 = document.getElementById('input3');

let input4 = document.getElementById('input4');
let input5 = document.getElementById('input5');
let input6 = document.getElementById('input6');

console.log(input4);
console.log(input5);
console.log(input6);

// Function

input1.addEventListener('mouseout', sum);
input2.addEventListener('mouseout', sum);

function sum() {
  let result = parseInt(input1.value || 0) + parseInt(input2.value || 0);
  input3.value = result
  console.log(input3.value);
}

input4.addEventListener('mouseout', sub);
input5.addEventListener('mouseout', sub);

function sub() {
  let result = parseInt(input4.value || 0) -
    parseInt(input5.value || 0);
  input6.value = result
  console.log(input6.value)
}

// OOP version 

class Calculator {
  calculate(operand1, operator, operand2) {
    switch (operator) {
      case '+':
        return operand1 + operand2;
      case '-':
        return operand1 - operand2;
      default:
        return NaN; // Invalid operator
    }
  }
}

const calculator = new Calculator();

document.getElementById('calculate').addEventListener('click', function () {
  const operand1 = parseFloat(document.getElementById('operand1').value) || 0;
  const operator = document.getElementById('operator').value.trim();
  const operand2 = parseFloat(document.getElementById('operand2').value) || 0;

  const result = calculator.calculate(operand1, operator, operand2);
  if (!isNaN(result)) {
    document.getElementById('result').value = result;
  } else {
    alert('Invalid operator! Please enter "+" or "-".');
  }
});

class Calculator2 {
  constructor() {
    this.result = 0;
  }

  add(a, b) {
    this.result = a + b;
  }
}

// Extra OOP example Person

function Person(name, age) {
  this.name = name;
  this.age = age;
}

let person1 = new Person("John", 30);

console.log(person1);

class Person2 {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }
}

let person2 = new Person("Alice", 25);

console.log(person2);

let sumOfAges = person1.age + person2.age;

console.log('Suma wiekou osób: ', sumOfAges);

Kalkulator jest do rozwinięcia i poprawy Ui. Poniżej omówienie kodu i podejścia.

### **Analiza kodu – Podejście Funkcyjne vs. OOP**

Twój kod przedstawia dwa podejścia do realizacji obliczeń: **funkcyjne (proceduralne)** oraz **obiektowe (OOP)**. Omówię je krok po kroku.

## **Podejście Funkcyjne**

Kod obsługuje proste operacje dodawania i odejmowania, wykorzystując **manipulację DOM** oraz **zdarzenia**.

### **1. Pobranie elementów HTML**

let input1 = document.getElementById('input1');let input2 = document.getElementById('input2');let input3 = document.getElementById('input3');let input4 = document.getElementById('input4');let input5 = document.getElementById('input5');let input6 = document.getElementById('input6');

Kod pobiera **referencje** do pól formularza (input) na stronie.

### **2. Logowanie wartości pól input**

console.log(input4);console.log(input5);console.log(input6);

Wypisuje w konsoli referencje do trzech pól input, ale same wartości nie są jeszcze dostępne.

### **3. Obsługa zdarzeń "mouseout"**

input1.addEventListener('mouseout', sum);input2.addEventListener('mouseout', sum);

- Gdy użytkownik **opuści** pole input1 lub input2, wywołana zostanie funkcja sum().

input4.addEventListener('mouseout', sub);input5.addEventListener('mouseout', sub);

- Gdy użytkownik **opuści** pole input4 lub input5, wywołana zostanie funkcja sub().

### **4. Funkcja sum() – Dodawanie liczb**

function sum() {  let result = parseInt(input1.value || 0) + parseInt(input2.value || 0);  input3.value = result;  console.log(input3.value);}

- Pobiera wartości z input1 i input2, konwertuje je na liczby (parseInt).

- Jeżeli pole jest puste, przyjmuje 0.

- Oblicza sumę i wpisuje wynik do input3.

### **5. Funkcja sub() – Odejmowanie liczb**

function sub() {  let result = parseInt(input4.value || 0) - parseInt(input5.value || 0);  input6.value = result;  console.log(input6.value);}

- Pobiera wartości z input4 i input5, konwertuje je na liczby.

- Wykonuje odejmowanie.

- Wstawia wynik do input6.

## **Podejście Obiektowe (OOP)**

Podejście obiektowe wykorzystuje **klasy**, które umożliwiają lepszą organizację kodu i jego ponowne użycie.

### **1. Klasa Calculator**

class Calculator {  calculate(operand1, operator, operand2) {    switch (operator) {      case '+':        return operand1 + operand2;      case '-':        return operand1 - operand2;      default:        return NaN; // Invalid operator    }  }}

- Klasa zawiera **metodę calculate()**, która obsługuje różne operatory.

- W zależności od przekazanego operatora (+ lub -), zwraca odpowiedni wynik.

### **2. Tworzenie instancji klasy i obsługa kliknięcia**

const calculator = new Calculator();

- Tworzymy obiekt klasy Calculator.

document.getElementById('calculate').addEventListener('click', function () {  const operand1 = parseFloat(document.getElementById('operand1').value) || 0;  const operator = document.getElementById('operator').value.trim();  const operand2 = parseFloat(document.getElementById('operand2').value) || 0;  const result = calculator.calculate(operand1, operator, operand2);  if (!isNaN(result)) {    document.getElementById('result').value = result;  } else {    alert('Invalid operator! Please enter "+" or "-".');  }});

Po kliknięciu przycisku calculate:

- Pobiera wartości operand1, operator, operand2.

- Wywołuje metodę calculate() obiektu calculator.

- Wstawia wynik do pola result lub pokazuje alert o błędzie.

### **3. Klasa Calculator2**

class Calculator2 {  constructor() {    this.result = 0;  }  add(a, b) {    this.result = a + b;  }}

- Calculator2 zawiera właściwość result i metodę add(), ale jej instancja nie jest używana w kodzie.

### **4. Tworzenie obiektów Person**

#### **Funkcja konstrukcyjna (stare podejście)**

function Person(name, age) {  this.name = name;  this.age = age;}let person1 = new Person("John", 30);console.log(person1);

- Tworzy obiekt person1 z właściwościami name i age.

#### **Klasa Person2 (nowoczesne podejście)**

class Person2 {  constructor(name, age) {    this.name = name;    this.age = age;  }}let person2 = new Person("Alice", 25);console.log(person2);

- Tworzy obiekt person2 używając nowoczesnej składni ES6 (class).

### **5. Obliczanie sumy wieku**

let sumOfAges = person1.age + person2.age;console.log('Suma wiekou osób: ', sumOfAges);

- Dodaje age obiektów person1 i person2 i wyświetla wynik.

## **Podsumowanie – Różnice między podejściem Funkcyjnym a OOP**

CechaPodejście FunkcyjnePodejście OOP**Organizacja kodu**Funkcje niezależneKlasy i obiekty**Przechowywanie stanu**Brak (wszystko lokalnie w funkcjach)Obiekty przechowują stan (this.result)**Reużywalność**Funkcje działają niezależnieMożna tworzyć wiele instancji klasy**Czytelność**Prosty kod, ale trudny do rozbudowyBardziej rozbudowany, ale łatwiejszy w utrzymaniu

**Kiedy używać którego podejścia?**

- Jeśli kod jest **prosty** i nie wymaga wielu operacji → **podejście funkcjonalne**.

- Jeśli kod ma być **rozszerzalny i wielokrotnego użytku** → **podejście OOP**.
