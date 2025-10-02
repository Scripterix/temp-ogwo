---
title: "Post #58 PHP Kodowanie i znaki specjalne"
date: 2025-06-16 20:35:33
author: Scripterix
slug: post-58-php-kodowanie-i-znaki-specjalne
post_id: 1166
categories:
  - "Coding Corner"
tags:
  - "php"
  - "znaki specjalne"
original_url: "https://opengateweb.com/posts/post-58-php-kodowanie-i-znaki-specjalne/"
---

## **Czym są znaki specjalne i dlaczego są problematyczne?**

Znaki specjalne w HTML to elementy takie jak <, >, &, " oraz ', które mają szczególne znaczenie w języku HTML. Problem polega na tym, że gdy chcemy wyświetlić te znaki jako zwykły tekst (a nie jako część kodu HTML), musimy je "uciec" - zamienić na odpowiednie encje HTML.

**Dlaczego to takie ważne?**

Wyobraź sobie, że użytkownik wprowadza w formularzu tekst: <script>alert('Hack!');</script>. Jeśli wyświetlisz to bezpośrednio na stronie, kod JavaScript zostanie wykonany! To klasyczna luka bezpieczeństwa XSS (Cross-Site Scripting).

**Funkcja htmlentities() - Twój przyjaciel**

Funkcja htmlentities() zamienia wszystkie znaki specjalne na bezpieczne encje HTML:

- < → &lt;

- > → &gt;

- & → &amp;

- " → &quot;

- ' → &#039;

**Praktyczny przykład:**

<?php
// Symulujemy dane od użytkownika (np. z formularza)
$user_input = '<script>alert("Niebezpieczny kod!");</script>';
$user_name = "Jan \"Kowalski\" & Spółka";

// BEZ zabezpieczenia - NIEBEZPIECZNE!
echo "Witaj: " . $user_input; // Wykona JavaScript!

// Z zabezpieczeniem - BEZPIECZNE
echo "Witaj: " . htmlentities($user_input);
// Wyświetli: &lt;script&gt;alert(&quot;Niebezpieczny kod!&quot;);&lt;/script&gt;

// Kolejny przykład
echo "Klient: " . htmlentities($user_name);
// Wyświetli: Jan &quot;Kowalski&quot; &amp; Spółka
?>

**Dodatkowe parametry funkcji:**

php*// Podstawowe użycie*
$safe_text = htmlentities($text);

*// Z określeniem kodowania (ważne dla polskich znaków)*
$safe_text = htmlentities($text, ENT_QUOTES, 'UTF-8');

*// ENT_QUOTES - koduje zarówno pojedyncze jak i podwójne cudzysłowy*
*// UTF-8 - obsługuje polskie znaki (ą, ć, ę, ł, ń, ó, ś, ź, ż)*

**Praktyczne zastosowania w codziennym kodowaniu:**

- **Komentarze użytkowników** - każdy komentarz powinien przejść przez htmlentities()

- **Formularze kontaktowe** - zabezpieczenie przed wstrzyknięciem kodu

- **Wyświetlanie nazw firm** - które mogą zawierać znaki specjalne

- **Obsługa danych XML/JSON** - które trafiają do HTML

To podstawa bezpiecznego programowania w PHP. Każdy tekst pochodzący od użytkownika powinien być "oczyszczony" przed wyświetleniem. To jak mycie rąk w medycynie - podstawowa higiena, której nie można pomijać!

## Kodowanie polskich znaków w HTML i PHP – unikaj krzaków i wspieraj SEO

W tym artykule poruszamy temat znaków specjalnych w PHP i HTML, a w szczególności skupiamy się również na **polskich literach diakrytycznych**, takich jak **ą, ć, ę, ł, ń, ó, ś, ź, ż**. To właśnie one często powodują problemy, gdy kodowanie dokumentu jest niepoprawne – co objawia się tzw. *krzakami* (czyli błędnymi symbolami zamiast znaków).

#### Obecność polskich znaków zależy głównie od:

**Kodowania znaków (charset) – absolutnie kluczowe!**Musisz zawsze umieszczać:

<meta charset="UTF-8">

w sekcji <head>. To zapewnia poprawne wyświetlanie polskich liter zarówno **lokalnie**, jak i na **serwerze** – o ile plik jest również zapisany w formacie UTF-8.

**Atrybut lang="pl"**Nie wpływa na kodowanie, ale:

- informuje przeglądarki i czytniki ekranu, że strona jest po polsku,

- wspiera SEO i automatyczne tłumaczenia.

To dobra praktyka, szczególnie dla stron kierowanych do polskich użytkowników.

**Konfiguracja serwera**Nawet jeśli Twój plik ma poprawny meta charset, serwer może narzucić inne kodowanie (np. ISO-8859-2). Dlatego warto sprawdzić nagłówki HTTP i ustawić:

Content-Type: text/html; charset=UTF-8

#### Dobre praktyki (checklista):

- ✓ Zawsze używaj <meta charset="UTF-8"> w <head>.

- ✓ Zapisuj pliki jako UTF-8 bez BOM.

- ✓ Dodaj <html lang="pl"> dla stron po polsku.

- ✓ Sprawdź nagłówki wysyłane przez serwer (szczególnie w Apache lub Nginx).

- ✓ W PHP – stosuj htmlentities() z 'UTF-8'

$safe = htmlentities($tekst, ENT_QUOTES, 'UTF-8');

🧪 Przykład HTML z poprawną konfiguracją

<!DOCTYPE html>
<html lang="pl">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document Lang i Charset ę ą ł ó Ź</title>
</head>
<body>
  <p>ę ó ł ż ź ć ń</p>
  <p>Charset odpowiada za kodowanie znaków w dokumentach internetowych, a html lang="pl" wspiera SEO, informując, że strona jest w języku polskim.</p>
</body>
</html>

Charset odpowiada za kodowanie znaków w dokumentach internetowych, a html lang="pl" wspiera SEO, informując, że strona jest w języku polskim.

Dzięki takim ustawieniom unikniesz błędów wyświetlania i zadbasz o techniczne SEO Twojej strony – **nie tylko w PHP, ale i w całym frontendzie**. Kodowanie to fundament, a polskie znaki to nie dodatek – to standard, który warto traktować serio.

W następnym przykładzie omówimy stosowanie polskich znaków dla stron połączenia z bazą i kliku innych. Obsługa polskich znaków to kluczowa kwestia przy tworzeniu stron w Polsce. Oto kompletny przewodnik:

## Konfiguracja dla polskich znaków

**1. Meta tag w HTML:**

<!DOCTYPE html>
<html lang="pl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Moja strona</title>
</head>

**2. Konfiguracja PHP dla polskich znaków:**

<?php
// Na początku pliku PHP - ustawienie kodowania
header('Content-Type: text/html; charset=UTF-8');

// Ustawienie locale dla polskich formatów dat, liczb itp.
setlocale(LC_ALL, 'pl_PL.UTF-8');

// Alternatywnie (jeśli powyższe nie działa):
setlocale(LC_ALL, 'Polish_Poland.1250');
?>

**3. Bezpieczne wyświetlanie polskich znaków:**

<?php8
// Tekst z polskimi znakami
$tekst = "Witaj Jaś! To jest test: ąćęłńóśźż & \"cudzysłowy\"";

// PRAWIDŁOWE użycie htmlentities z UTF-8
$bezpieczny_tekst = htmlentities($tekst, ENT_QUOTES, 'UTF-8');
echo $bezpieczny_tekst;

// Lub użyj htmlspecialchars (lżejsza alternatywa)
$bezpieczny_tekst2 = htmlspecialchars($tekst, ENT_QUOTES, 'UTF-8');
echo $bezpieczny_tekst2;
?>

**4.Połączenie z bazą danych (MySQL):**

<?php
// Przy połączeniu z bazą danych
$pdo = new PDO('mysql:host=localhost;dbname=mojabaza;charset=utf8mb4', 
               $username, $password);

// Lub dla starszych wersji:
mysqli_set_charset($connection, "utf8");
?>

**5. Kompletny przykład strony:**

<?php
header('Content-Type: text/html; charset=UTF-8');
setlocale(LC_ALL, 'pl_PL.UTF-8');

$nazwa_uzytkownika = "Jaś Kowalski";
$komentarz = "Świetna strona! Mam pytanie: <skrypt>alert('test')</skrypt>";
?>
<!DOCTYPE html>
<html lang="pl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Test polskich znaków</title>
</head>
<body>
    <h1>Witaj <?= htmlspecialchars($nazwa_uzytkownika, ENT_QUOTES, 'UTF-8') ?>!</h1>
    <p>Twój komentarz: <?= htmlspecialchars($komentarz, ENT_QUOTES, 'UTF-8') ?></p>
    
    <p>Data: <?= strftime('%A, %d %B %Y') ?></p>
</body>
</html>

**Kluczowe punkty:**

- **lang="pl"** - informuje przeglądarki i czytniki ekranu o języku

- **charset="UTF-8"** - obsługuje wszystkie polskie znaki

- **ENT_QUOTES, 'UTF-8'** - przy każdym htmlentities() lub htmlspecialchars()

- **setlocale(LC_ALL, 'pl_PL.UTF-8')** - polskie formaty dat, liczb, sortowanie

**Bonus - formatowanie polskich dat:**

<?php
setlocale(LC_ALL, 'pl_PL.UTF-8');

echo strftime('%A, %d %B %Y'); // Poniedziałek, 07 czerwca 2025
echo date('j F Y'); // 7 June 2025 (angielski)

// Polska data z DateTime
$data = new DateTime();
echo $data->format('j.m.Y'); // 7.06.2025
?>

To ustawienie zagwarantuje ci pełną obsługę polskich znaków w całej aplikacji. Pamiętaj, żeby wszystkie pliki zapisywać w kodowaniu UTF-8!
