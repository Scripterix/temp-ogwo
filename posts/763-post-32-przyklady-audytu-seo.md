---
title: "Post #32 Przykłady Audytu SEO"
date: 2025-03-21 13:24:18
author: Scripterix
slug: 32-examples-seo-audit
post_id: 763
categories:
  - "SEO SEM"
  - "Wyzwanie"
tags:
  - "seo-audit"
  - "tools"
original_url: "https://opengateweb.com/posts/32-examples-seo-audit/"
---

# **Przykłady Audytu SEO,  Audyt ruchu(traffic) na stronie** oraz omówienie podstawowych parametrów.

## Data publikacji to 3 Lipca 2024 zatem mówimy o GA4

- Dane z Google Analitics

- Liczba użytkowników sesji

- Wyświetlenia strony

- Współczynnik odrzuceń

- Średni czas spędzony na stronie

- Żródła ruchu

- Konwersje

**Audyt wyników strony w odróżnieniu od audytu technicznego**

## Do przeprowadzenia dokładnej analizy SEO potrzebujemy różnych danych 

- Można się pogubić początkowo ale zawsze warto myśleć że strony to tylko **LINK** TEXT i IMG

- Dlatego podkreślami dużymi literami link bo on ma duże znaczenie dla SEO

- Można także koncentrować się na mniejszej liczbie współczynników jeśli wiemy w jakiej fazie jesteśmy

## Dane z Google Analytics

**Liczba użytkowników sesji, wyświetleń stron, współczynnik odrzuceń, średni czas spędzony na stronie, źródła ruchu, konwersje**

Dane te pozwolą nam zrozumieć, jak użytkownicy wchodzą na stronę, co robią na niej i jak długo z niej korzystają.

**Dane z Google Search Console**

Pozycje strony w wynikach wyszukiwania, widoczność w wyszukiwarce, kliknięcia, współczynnik kliknięć (CTR), błędy indeksowania. Dane te pokażą nam, jak dobrze strona jest widoczna w wyszukiwarce Google i jakie są potencjalne problemy z indeksowaniem.

**Badania słów kluczowych**

Określenie fraz kluczowych, na które strona chce się pozycjonować. Należy sprawdzić objętość wyszukiwania, konkurencyjność i trafność fraz kluczowych.

**Analiza konkurencji**

Zidentyfikowanie głównych konkurentów i analiza ich stron internetowych pod kątem SEO. Należy sprawdzić, jakie frazy kluczowe pozycjonują konkurenci, jakie treści publikują i jakie mają linki zewnętrzne.

**Analiza techniczna strony** Sprawdzenie strony pod kątem błędów technicznych, takich jak wolne ładowanie strony, brak responsywności, błędy 404.

Należy również sprawdzić strukturę strony, adresy URL i metadane.

# Rozpoczynamy analize i sprawdzamy [Telomers.pl](https://telomers.pl/)

## Liczba użytkowników sesji na stronie telomers.pl

## Czym jest "Liczba użytkowników sesji"?

Liczba użytkowników to wskaźnik w Google Analytics, który informuje o liczbie wszystkich użytkowników, którzy odwiedzili Twoją stronę internetową w danym okresie czasu (np. dzień, miesiąc). Następnie mamy parametr Nowi Użytkownikownicy i Sesje. Każdy użytkownik jest unikalny ale nie do końca co jest dla mnie zabawne. Kiedyś w poprzednich wersja UU był liczony tylko raz, niezależnie od tego, ile razy odwiedził stronę w tym okresie. Dodatkowo w obecnym GA4 nie podaje dokładnej ilości unikalnych użytkowników, wytłumaczenie pomocy Google:

**Użytkownik po wejściu np na stronę główną HOME zazwyczaj klika dalej w podstronę np ABOUT a kiedy wróci do HOME jego unikalne odwiedziny będą liczone jako 2**

Aby zrozumieć, dlaczego odwiedziny strony głównej, a następnie strony o nas i powrót na stronę główną są liczone jako 2 unikalne odwiedziny, musimy wziąć pod uwagę sposób, w jaki Google Analytics śledzi sesje użytkowników.

W Google Analytics sesja jest definiowana jako grupa interakcji, które użytkownik podejmuje w określonym przedziale czasowym na Twojej stronie internetowej. Domyślnie sesja kończy się po 30 minutach braku aktywności lub o północy.

Kiedy użytkownik odwiedza stronę główną, a następnie przechodzi do strony o nas, jest to uważane za jedną sesję. Jednak gdy użytkownik wraca na stronę główną, jest to liczone jako nowa sesja, ponieważ wystąpiła przerwa w aktywności trwająca ponad 30 minut.

Dlatego w tym scenariuszu wizyta na stronie głównej, a następnie na stronie o nas i powrót na stronę główną jest liczone jako 2 unikalne odwiedziny.

Warto zauważyć, że to zachowanie jest specyficzne dla sposobu, w jaki Google Analytics śledzi sesje i może się różnić w zależności od używanego narzędzia analitycznego.

## Tabela z Pomocy Google jakie dane użytkowników możesz filtrować w GA4

- ALL Users lub Użytkownicy łącznie

- Nowi Użytkownicy

- Aktywni Użytkownicy (w raportach także jako „Użytkownicy”)

- Powracający Użytkownicy

Tabela poniżej zawiera definicje poszczególnych danych o użytkownikach:

DaneCo to jest ?Metoda i atrybut danychUżytkownicy łącznie wybranym zakresie dat.Liczba unikalnych użytkowników, którzy wywołali użytkowników, którzy wywołali użytkowników, którzy wywołali dowolne zdarzenie w wybranym zakresie datDane generowane automatyczneNowi użytkownicyLiczba nowych unikalnych użytkowników powiązanych z zarejestrowanym zdarzeniem first_open lub first_visit w zakresie dat.Dane generowane automatycznieAktywni użytkownicy (w raportach także jako „Użytkownicy”)*Liczba unikalnych użytkowników, którzy weszli w użytkowników, którzy weszli w interakcję z Twoja witryną w wybranym zakresie dat.Dane generowane automatyczne

Aktywny użytkownik to każdy użytkownik, który ma rozpoczętą sesję z zaangażowaniem, czyli taką, podczas której Analytics rejestruje zdarzenia

Rejestracja zdarzeń:

- w witrynie zdarzenie first_visit lub parametr engagement_time_msec,

- w aplikacji na Androida zdarzenie first_open lub parametr engagement_time_msec,

- w aplikacji na iOS zdarzenie first_open lub user_engagement.

Dodatkowe informacje: W Google Analytics możesz przeglądać raporty dotyczące liczby użytkowników sesji dla różnych przedziałów czasowych, stron, źródeł ruchu i innych parametrów. Możesz również ustawić cele i śledzić liczbę użytkowników sesji, którzy osiągnęli te cele.

Jeśli chcesz dowiedzieć się więcej napisz lub samodzielnie poszperaj w Google Pomoc oto [Linki-Omówieninie-Uzytkowników](https://support.google.com/analytics/answer/12253918)
