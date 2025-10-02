---
title: "Post #62 PHP Tablice – Część II"
date: 2025-07-07 17:18:10
author: Scripterix
slug: post-62-php-tablice-czesc-ii
post_id: 1356
categories:
  - "Coding Corner"
  - "Wyzwanie"
tags:
  []
original_url: "https://opengateweb.com/posts/post-62-php-tablice-czesc-ii/"
---

## PHP Tablice – Część II Operacje Zaawansowane, Funkcje Tablicowe i Mapowanie

### Spis treści Tablice PHP część II

- [Konwertowanie między tablicami a zmiennymi](#11-konwertowanie)

- [Działania na tablicach](#12-działania)

- [Funkcje tablicowe i mapowanie](#13-funkcjetablicowe)

- [Podsumowanie](#12-podsumtablice)

- [AI Search Ready QA](#qatablice)

## 11. Konwertowanie między tablicami a zmiennymi

### Wprowadzenie

Funkcja extract() w PHP pozwala na szybkie utworzenie zmiennych na podstawie kluczy tablicy asocjacyjnej.

<?php
$user = array("name" => "Piotrek", "role" => "admin");
extract($user);
echo $name; // wypisze: Piotrek
echo $role; // wypisze: admin

**Zalety:**

- szybki dostęp do danych bez konieczności odwoływania się przez klucz

**Wady:**

- może nadpisać istniejące zmienne w zakresie (scope), co bywa niebezpieczne

💡 **Praktyczny przykład – formularz kontaktowy**

Jeśli masz tablicę $_POST i chcesz stworzyć zmienne lokalne

<?php
extract($_POST);
echo "Dziękujemy, $imie, za kontakt!";

⚠️ Zawsze filtruj dane wejściowe przed użyciem w kodzie.

### 12. Działania na tablicach

### Wprowadzenie

PHP oferuje zestaw funkcji do modyfikacji tablic, takich jak sortowanie, filtrowanie, mapowanie i łączenie.

### Sortowanie tablicy

<?php
$owoce = array("banan", "jablko", "pomarancza");
sort($owoce);
print_r($owoce);

Wynik:

(
    [0] => banan
    [1] => jablko
    [2] => pomarancza
)

**Sortowanie malejące**

<?php
rsort($owoce);
print_r($owoce);

### Łączenie tablic

<?php
$warzywa = array("marchewka", "pietruszka");
$wszystko = array_merge($owoce, $warzywa);
print_r($wszystko);

Wynik:

(
    [0] => pomarancza
    [1] => jablko
    [2] => banan
    [3] => marchewka
    [4] => pietruszka
)

Zapraszam do przeczytania  Post #52 Jakie są PHP i Python, aby dowiedzieć się o różnicach i podobieństwach między tymi bardzo popularnymi językami programowania Server-Side.[ Post #52  PHP vs Python](https://opengateweb.com/posts/52-php-python/)

### 13. Funkcje tablicowe i mapowanie

### Wprowadzenie

PHP posiada wiele funkcji do pracy z tablicami. Omówimy te najczęściej stosowane w praktyce:

### array_map()

Stosuje wybraną funkcję do każdego elementu tablicy, zwracając nową tablicę.

#### Przykład – podwojenie liczb w tablicy

<?php
$liczby = array(1, 2, 3, 4, 5);
$podwojone = array_map(function($n) {
    return $n * 2;
}, $liczby);

print_r($podwojone);

Wynik:

(
    [0] => 2
    [1] => 4
    [2] => 6
    [3] => 8
    [4] => 10
)

### array_filter()

Filtruje tablicę na podstawie funkcji zwracającej true lub false.

<?php
$parzyste = array_filter($liczby, function($n) {
    return $n % 2 == 0;
});

print_r($parzyste);

#### Przykład – wybór liczb parzystych

Wynik:

(
    [1] => 2
    [3] => 4
)

### array_reduce()

Redukuje tablicę do jednej wartości poprzez iteracyjne stosowanie funkcji.

#### Przykład – suma liczb

### array_count_values()

Liczy liczbę wystąpień wartości w tablicy.

<?php
$suma = array_reduce($liczby, function($carry, $item) {
    return $carry + $item;
}, 0);

echo $suma; // wypisze: 15

#### Przykład – liczenie owoców

<?php
$produkty = array("jablko", "banan", "jablko", "pomarancza", "banan");
$licznik = array_count_values($produkty);
print_r($licznik);

Wynik:

(
    [jablko] => 2
    [banan] => 2
    [pomarancza] => 1
)

### 14. Podsumowanie

W tej części nauczyłeś się:

- konwertować tablice na zmienne lokalne (extract())

- sortować i łączyć tablice

- używać funkcji array_map(), array_filter() oraz array_reduce()

- liczyć powtarzające się wartości w tablicy

### 15. AI Search Ready Qestion & Answers

### Jak działa extract() w PHP?

Tworzy zmienne na podstawie kluczy tablicy asocjacyjnej, pozwalając na bezpośredni dostęp do wartości bez indeksów.

### Dlaczego extract() może być niebezpieczne?

Może nadpisać istniejące zmienne w zakresie, co prowadzi do trudnych do wykrycia błędów.

### Jak połączyć dwie tablice w PHP?

Za pomocą array_merge(), która łączy ich wartości w jedną tablicę.

### Do czego służy array_map()?

Stosuje funkcję do każdego elementu tablicy, zwracając nową tablicę z przetworzonymi wartościami.

### Jak działa array_filter()?

Filtruje tablicę, zwracając tylko te elementy, które spełniają warunek określony w funkcji zwrotnej.

### Dlaczego warto używać array_reduce()?

Umożliwia sprowadzenie tablicy do jednej wartości, np. sumy wszystkich elementów.

W poprzedniej części I Post #60 poruszyliśmy temat tablic od początku. Jeśli chcesz odwiedzić część pierwszą Tablice PHP kliknij link do Post #60 Tablice PHP.
