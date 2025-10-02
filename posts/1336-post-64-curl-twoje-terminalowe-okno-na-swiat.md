---
title: "Post #64 Curl – Twoje Terminalowe Okno na Świat"
date: 2025-07-18 21:21:56
author: Scripterix
slug: post-64-curl-twoje-terminalowe-okno-na-swiat
post_id: 1336
categories:
  - "Coding Corner"
  - "Wyzwanie"
tags:
  - "curl"
  - "endpoint"
original_url: "https://opengateweb.com/posts/post-64-curl-twoje-terminalowe-okno-na-swiat/"
---

## **Jak testować API, pobierać pliki i debugować żądania HTTP jak zawodowiec**.

Poniższy artykuł jest w formule tutorial** Curl** i zawiera zbiór komend i opis jak pracować z Curl.

## Spis treści

- [Wprowadzenie – czym właściwie jest curl?](#Wprowadzenie-–-czym-właściwie-jest-curl)

- [Instalacja i konfiguracja](#Instalacja-i-konfiguracja-curl)

- [Najważniejsze komendy w praktyce](#Najważniejsze-komendy-w-praktyce-curl)

- [Curl i API – jak testować endpointy i pracować z JSON-em](#Curl-i-API-–-jak-testować-endpointy)

- [Autoryzacja, nagłówki i metody HTTP](#Autoryzacja,-nagłówki-i-metody-HTTP)

- [Debugowanie i śledzenie przekierowań](#Debugowanie-i-śledzenie-przekierowań)

- [Automatyzacja w skryptach](#Automatyzacja-w-skryptach)

- [Porównanie curl i wget – kiedy używać którego?](#Porównanie-curl-i-wget-–-kiedy-używać-którego?)

- [FAQ - Często zadawane pytania](#-FAQ---Często-zadawane-pytania)

- [Komendy curl – PDF do pobrania](#Komendy-curl-–-PDF-do-pobrania-(Markdown-tekst-do-eksportu))

- [Podsumowanie co się nauczyliśmy o Curl](#Podsumowanie-co-się-nauczyliśmy-o-Curl)

Kod źródłowy do wpisu oraz komendy zostały umieszczone i są dostępne jako **[Gist] Scripetrix dla [Post #64 Curl – Twoje Terminalowe Okno na Świat](https://gist.github.com/Scripterix/5dcbc8e77570e42f2bb635e10eb3a607)**

## 1. Wprowadzenie – czym właściwie jest curl?

Wyobraź sobie, że możesz porozmawiać z dowolnym serwerem bezpośrednio z terminala – bez przeglądarki, bez graficznych bajerów. Tylko Ty, adres URL i odpowiedź serwera.Tym właśnie jest curl.

To jedno z najczęściej używanych narzędzi w świecie programistów, testerów i DevOps. Pomaga wysyłać żądania HTTP, testować API, pobierać pliki i analizować odpowiedzi.

![coding-opengateweb](https://opengateweb.com/wp-content/uploads/2025/07/image-2-559x745.jpg)

## 2. Instalacja i konfiguracja

Curl jest dostępny na większości systemów:

- **Linux** – często zainstalowany domyślnie (sprawdź: curl --version)

- **macOS** – również w standardzie

- **Windows** – dostępny jako curl.exe w PowerShell lub przez instalator

- **Visual Studio Code / Git Bash** – jeśli używasz Windows i masz zainstalowany Git, curl jest dostępny w terminalu (MINGW64), który uruchamiasz np. przez VSC

Jeśli chcesz, możesz też zainstalować aktualną wersję z oficjalnego repozytorium: [https://curl.se](https://curl.se)

## 3. Najważniejsze komendy w praktyce

curl https://example.com

Pobiera HTML strony.

curl -I https://example.com

Wyświetla tylko nagłówki odpowiedzi (HEAD).

curl -v https://example.com

Tryb verbose – pokazuje cały proces żądania.

curl -o plik.png https://example.com/logo.png

Zapisuje odpowiedź do pliku.

curl -L https://bit.ly/xyz

Śledzi przekierowania (301/302).

## 4. Curl i API – jak testować endpointy i pracować z JSON-em

Curl to niezastąpione narzędzie do testowania REST API:

curl -X GET https://api.example.com/users

Wysyłanie danych JSON:

curl -X POST -H "Content-Type: application/json" \     -d '{"name":"Piotr"}' https://api.example.com/users

Odbieranie odpowiedzi? Surowe dane JSON można sformatować narzędziem jq:

curl https://api.example.com/data | jq .

## 5. Autoryzacja, nagłówki i metody HTTP

### Basic Auth

curl -u user:pass https://api.example.com

### Token JWT

curl -H "Authorization: Bearer TwójToken" https://api.example.com

### Niestandardowe nagłówki

curl -H "X-Custom: wartość" https://example.com

## 6. Debugowanie i śledzenie przekierowań

- -v pokazuje cały przebieg żądania

- -i dołącza nagłówki HTTP

- --location automatycznie podąża za przekierowaniami

Dzięki temu możesz analizować łańcuchy redirectów, statusy HTTP, i błędy po stronie serwera.

## 7. Automatyzacja w skryptach

Curl świetnie nadaje się do cronów, testów integracyjnych, CI/CD.Przykład użycia w bashu:

if curl -s --fail https://strona.pl/health; then  echo "Strona działa poprawnie"else  echo "Uwaga – problem z endpointem!"fi

Najważniejsze komendy Curl znajdziesz w naszym darmowym CheatSheet. Kliknij w link, aby pobrać [listę poleceń Curl](https://opengateweb.com/wp-content/uploads/2025/07/Curl-–-Najwazniejsze-Komendy.pdf) lub skorzystaj z przycisku poniżej. Nie musisz nawet się rejestrować do newslettera – to proste i szybkie!

[Pobierz polecenie Curl](https://opengateweb.com/wp-content/uploads/2025/07/Curl-–-Najwazniejsze-Komendy.pdf)

## 8. Porównanie curl i wget – kiedy używać którego?

CechacurlwgetWspiera API✅ (POST, PUT itd.)❌ tylko GET i pobieraniePobieranie plików✅✅Śledzenie redirectów✅ -L✅ domyślnieObsługa protokołówHTTP, FTP, SMTPHTTP, FTPSkryptyDoskonały do testowania APIŚwietny do masowego pobierania

## 9. FAQ - Często zadawane pytania

**Jak pobrać plik PDF za pomocą curl?**

curl -o plik.pdf https://adres.pl/plik.pdf

📌 curl nawiązuje połączenie HTTP z podanym adresem i pobiera surową zawartość odpowiedzi – czyli dane binarne pliku PDF. Dzięki opcji -o (output) treść ta zostaje zapisana bezpośrednio do wskazanego pliku lokalnego, a nie wyświetlona w terminalu.

**Czy curl działa z proxy?**

curl -x http://proxy.example.com:8080 https://example.com

📌 Flaga -x ustawia zewnętrzny serwer proxy, przez który curl kieruje całe połączenie. To przydatne w firmowych sieciach, testach lokalizacji lub omijaniu ograniczeń regionalnych.

**Czy curl obsługuje cookies?**

curl -c cookies.txt https://example.com

📌 Flaga -c zapisuje wszystkie ciasteczka otrzymane od serwera (np. Set-Cookie) do pliku cookies.txt. Curl działa tu jak przeglądarka – przechowuje informacje o sesji, autoryzacji, itp.

curl -b cookies.txt https://example.com

📌 Flaga -b pozwala odczytać i przesłać zapisane wcześniej ciasteczka jako nagłówki HTTP w kolejnych żądaniach. Dzięki temu możesz zachować sesję lub zalogowanie między wywołaniami curl.

**Jak wyświetlić nagłówki odpowiedzi HTTP?**

curl -i https://example.com

📌 Flaga -i sprawia, że curl dołącza do odpowiedzi nie tylko ciało (HTML, JSON, itd.), ale też nagłówki HTTP – takie jak Content-Type, Server, Date, Cache-Control, itp.

**Jak podejrzeć cały proces komunikacji z serwerem?**

curl -v https://example.com

📌 -v (verbose) to tryb diagnostyczny. Pokazuje wszystko: rozwiązywanie DNS, połączenie z portem, wysłane żądanie HTTP i pełną odpowiedź, włącznie z kodem statusu i nagłówkami. Niezbędne przy debugowaniu API i błędów 403, 404, 500.

**Jak pobrać plik bez pokazywania postępu (cicho)?**

curl -s -o plik.txt https://example.com/data.txt

📌 Flaga -s (silent) wyłącza pasek postępu i komunikaty – przydatne w skryptach, cronach i logach CI/CD.

[![cURL Cheat Sheet – darmowy PDF z najważniejszymi komendami terminalowymi, API i JSON](https://opengateweb.com/wp-content/uploads/2025/07/post-64-curl-twoje-terminalowe-okno-na-swiat-497x745.png)](https://opengateweb.com/wp-content/uploads/2025/07/Curl-–-Najwazniejsze-Komendy.pdf)

## 10. Komendy curl – [**PDF do pobrania**](https://opengateweb.com/wp-content/uploads/2025/07/Curl-–-Najwazniejsze-Komendy.pdf)

Curl – Najważniejsze Komendy## Podstawowe- `curl https://example.com` – pobranie HTML- `curl -I https://example.com` – tylko nagłówki- `curl -v https://example.com` – verbose mode- `curl -L https://bit.ly/link` – śledzenie redirectów## API i JSON- `curl -X GET https://api.example.com/users`- `curl -X POST -H "Content-Type: application/json" -d '{"name":"Anna"}' https://api.example.com`- `curl -H "Authorization: Bearer TOKEN" https://api.example.com`## Pobieranie plików- `curl -o obrazek.png https://example.com/img.png`- `curl -O https://example.com/dokument.pdf`## Debugowanie- `curl -i https://example.com` – nagłówki- `curl -v https://example.com` – cały log- `curl --trace-ascii log.txt https://example.com`## Autoryzacja- `curl -u user:pass https://api.example.com`- `curl -H "Authorization: Bearer TOKEN" https://api.example.com`## Inne- `curl --help` – pomoc- `man curl` – pełna dokumentacja

## 11. Podsumowanie co się nauczyliśmy o Curl

11. Podsumowanie – czego się nauczyliśmy?

W tym poradniku poznaliśmy najważniejsze aspekty pracy z curl, w tym:

- jak instalować i uruchamiać curl na różnych systemach (nawet z Git Bash w VSC),

- jak wykonywać podstawowe żądania GET i POST,

- jak testować API i przesyłać dane w formacie JSON,

- jak ustawiać nagłówki, tokeny, autoryzację,

- jak śledzić przekierowania i analizować odpowiedzi HTTP,

- oraz jak zautomatyzować powtarzalne zapytania w skryptach.

Dowiedziałeś się również, jak curl wypada w porównaniu do wget, oraz jak diagnozować problemy sieciowe przy pomocy trybu verbose, trace-ascii i opcji -i, -s, -L.

📌 **Chcesz pogłębić wiedzę o testowaniu API?** Zajrzyj do naszych pokrewnych artykułów:

-  [Post #22 wprowadzenie do API](https://opengateweb.com/posts/22-post-api/)

-  [Post #11 API Advanced Programming Interface](https://opengateweb.com/posts/11-post-api/)

Zachęcamy do dodania curl do swojego codziennego workflow – niezależnie od tego, czy jesteś programistą, testerem, DevOpsem czy po prostu chcesz zrozumieć, co naprawdę dzieje się między Twoją aplikacją a serwerem.

**📝 Zespół OpenGateWeb**

Artykuł przygotowany w ramach wyzwania **10k godzin programowania** i kategorii Coding Corner.
