---
title: "Post #66 – Jak zbudować środowisko programistyczne na Windows Visual Studio Code, Git, Node.js"
date: 2025-08-07 22:16:59
author: Scripterix
slug: post-66-jak-zbudowac-srodowisko-programistyczne-na-windows-visual-studio-code-git-node-js
post_id: 1575
categories:
  - "Coding Corner"
  - "Wyzwanie"
tags:
  - "front-end"
  - "programming"
original_url: "https://opengateweb.com/posts/post-66-jak-zbudowac-srodowisko-programistyczne-na-windows-visual-studio-code-git-node-js/"
---

## Spis treści

- [Wprowadzenie](#Wprowadzenie-66)

- [I](#IDE – czyli jak wygląda warsztat programisty?)[DE – czyli jak wygląda warsztat programisty?](#IDE-–-czyli-jak-wygląda-warsztat-programisty?)

- [Czym jest Visual Studio Code i dlaczego warto go używać?](#Czym-jest-Visual-Studio-Code-i-dlaczego-warto-go-używać)

- [Instalacja Node.js na Windows](#Instalacja-Nodejs-na-Windows)

- I[nstalacja Visual Studio Code](#Instalacja-Visual-Studio-Code-(VSC))

- [Konfiguracja VS Code i najważniejsze rozszerzenia](#Konfiguracja-VSC-i-najważniejsze-rozszerzenia-i-ustawienia)

- [Instalacja Git i Git Bash](#Instalacja-Git-i-Bash-Git-Bash))

- [Tworzenie pierwszego projektu HTML Css JS](#Tworzenie-pierwszego-projektu-HTML-Css-JS)

- Pierwszy projekt w React z create-react-app

- [Inne edytory kodu na Windows](#Inne-edytory-kodu-na-Windows)

- [Synchronizacja ustawień i ustawienie VS Code z GitHub](#Synchronizacja-ustawień-i-ustawienie-VS-Code-z-GitHub)

- [Podsumowanie i co dalej](#podsumowanie-66)

## Wprowadzenie

Zanim zaczniesz programować w Java Script, React, PHP czy Pythonie, potrzebujesz stabilnego i dobrze skonfigurowanego środowiska deweloperskiego. Na systemie Windows wymaga to kilku kroków, ale efekt końcowy pozwala wygodnie pisać kod, zarządzać projektami i testować aplikacje. Ten przewodnik pokazuje, jak to zrobić krok po kroku. 

Przeprowadzimy cię w kilku krokach jak zainstalować Edytor kodu VSC i niektóre dodatki. Omówimy Node.js po co jest i co można dzięki niemu zrobić a na koniec dodamy GitBash twój konsolowy przyjaciel dla poleceń CLI.

🛠️ **Uwaga:** Środowisko IDE jest uniwersalne i może służyć nie tylko do pracy z Reactem. Świetnie sprawdzi się również przy projektach w Angularze, Vue.js, Node.js, Next.js, a nawet w PHP czy Pythonie. My w tym artykule koncentrujemy się na konfiguracji pod Reacta, ale to tylko przykład – te same narzędzia wykorzystasz w większości popularnych stacków frontendowych i backendowych.

## **IDE – czyli jak wygląda warsztat programisty**?

Twój edytor kodu, taki jak **Visual Studio Code**, może być czymś więcej niż tylko miejscem do pisania funkcji czy wstawiania średników. To centrum dowodzenia całym projektem – elastyczne, rozszerzalne, gotowe do rozbudowy o zestaw narzędzi wspierających Cię na każdej linii kodu.

Z czasem – po kilku lub kilkunastu projektach – dojdziesz do własnego układu folderów i stylu pracy. Ale już teraz warto zaplanować przechowywanie i znać „ekosystem”, który najczęściej towarzyszy IDE. Oto kilka podstawowych gałęzi:

#### 1. **Git i GitHub**

- **Git** to system wersjonowania – pozwala cofać zmiany, tworzyć osobne gałęzie (branches), pracować zespołowo i mieć historię każdego wiersza kodu.

- **GitHub** to portal (nie wtyczka!) do przechowywania i zarządzania repozytoriami online. Przydaje się przy backupie i pracy w zespole.

#### 2. **Git Bash** *(osobny program)*

Zastępuje domyślny terminal systemowy (np. PowerShell w Windowsie). Umożliwia pracę w stylu Linuxa, z pełnym wsparciem komend bash, co bardzo ułatwia korzystanie z Gita i automatyzację.

#### 3. **Live Server** *(wtyczka do VSC)*

Uruchamia Twoją aplikację w przeglądarce i automatycznie odświeża ją przy każdej zmianie w kodzie. Doskonały do nauki HTML, CSS i JS – efekt widzisz natychmiast.

#### 4. **Prettier i ESLint** *(wtyczki do VSC)*

Prettier formatuje kod zgodnie z ustalonym stylem. ESLint sprawdza, czy kod nie zawiera błędów lub złych praktyk. Razem utrzymują porządek i jakość w Twoim projekcie.

#### 5. **Debugger** *(moduł VSC + konfiguracja)*

Zatrzymuje kod w dowolnym miejscu, pokazuje wartości zmiennych, ułatwia śledzenie błędów. Przydaje się szczególnie, gdy aplikacja robi „dziwne rzeczy”.

#### 6. **Docker i Dev Containers** *(zewnętrzne programy + integracje z VSC)*

Pozwalają uruchamiać całe środowisko programistyczne w osobnym kontenerze – jakbyś miał osobny komputer do projektu, bez mieszania go z lokalnym systemem.

#### 7. **Copilot i inne narzędzia AI** *(pluginy do VSC)*

Podpowiadają kod, automatyzują powtarzalne operacje, tłumaczą błędy. Sztuczna inteligencja staje się Twoim asystentem, a czasem nawet współautorem kodu.

Brzmi przytłaczająco? Może i tak. Łatwo się poczuć **overwhelmed**, zwłaszcza na początku, kiedy wszystko wydaje się nowe i nieznane. Ale spokojnie – większość z tych narzędzi ma prosty interfejs, wersję desktopową lub instaluje się jako plugin do VSC jednym kliknięciem.

Nie musisz znać wszystkiego od razu. Jeśli czujesz lekki chaos – weź oddech. **IDE to tylko Twoja zbrojownia.** A zbrojownię odkrywa się krok po kroku.

Zanim zaczniesz programować w JavaScript, React, PHP czy Pythonie, potrzebujesz stabilnego i dobrze skonfigurowanego środowiska deweloperskiego. Na systemie Windows wymaga to kilku kroków, ale efekt końcowy pozwala wygodnie pisać kod, zarządzać projektami i testować aplikacje.

Ten przewodnik pokaże Ci krok po kroku:

- jak zainstalować edytor kodu Visual Studio Code,

- po co jest Node.js i do czego się przydaje,

- jak działa Git i terminal Bash w pracy frontendowca,

- oraz jak zbudować swoje pierwsze projekty i środowisko gotowe do pracy z Reactem, JavaScript, CSS i HTML.

🛠️ Uwaga: Środowisko IDE opisane w tym artykule możesz wykorzystać również do pracy z Angular, Vue, Next.js, PHP, Python, a nawet C++. React jest tutaj tylko przykładem – to uniwersalna baza dla każdego programisty webowego.

## Czym jest Visual Studio Code i dlaczego warto go używać

Visual Studio Code (zamiennie nazywany VSC) to jeden z najlżejszych i najbardziej rozszerzalnych edytorów kodu. Obsługuje wiele języków, ma wsparcie dla Git, debugger, zintegrowany terminal, a dzięki tysiącom dostępnych rozszerzeń możesz go dostosować do niemal każdego stacku technologicznego – od frontendu po backend.

Rozwijany i utrzymywany przez firmę Microsoft, VSC zyskał ogromną popularność wśród programistów na całym świecie dzięki swojej szybkości, niezawodności i łatwości konfiguracji. To idealny wybór do pracy z JavaScript, Node.js, React, Pythonem i wieloma innymi technologiami.

W dalszej części pokażemy, jak go pobrać, skonfigurować i połączyć z Git i GitHub.

## Instalacja Node.js na Windows

### Co to jest Node.js?

Node.js to środowisko uruchomieniowe JavaScript, które pozwala wykonywać kod JS poza przeglądarką. Dzięki niemu możemy używać npm – menedżera pakietów, który jest niezbędny do instalowania bibliotek takich jak React, Vue czy Express. 

Node.js integruje się z Visual Studio Code, ponieważ pozwala uruchamiać skrypty JavaScript bez potrzeby używania przeglądarki. Dzięki temu VSC staje się nie tylko edytorem, ale również środowiskiem uruchomieniowym – możesz pisać, testować i debugować kod JS bez wychodzenia z edytora. Dodatkowo, Node instaluje npm, czyli menedżer pakietów, który pozwala dodawać biblioteki do projektu jednym poleceniem w terminalu VSC.

### Jak zainstalować?

- Wejdź na https://nodejs.org

- Pobierz wersję oznaczoną jako **LTS (Long Term Support)**

- Uruchom instalator i przejdź przez kolejne kroki (zaznacz opcję dodania Node do zmiennych środowiskowych PATH)

- Po instalacji otwórz terminal i wpisz node -v npm -v 

- Jeśli pojawią się wersje – wszystko działa poprawnie.

![node JS download](https://opengateweb.com/wp-content/uploads/2025/08/node-1324x745.png)

## Instalacja Visual Studio Code (VSC)

### Dlaczego warto?

Visual Studio Code to jeden z najlżejszych i najbardziej rozszerzalnych edytorów kodu. Obsługuje wiele języków, ma wsparcie dla Git, debugger, terminal, a dzięki rozszerzeniom możesz go dostosować do każdego stacku technologicznego.

### Instalacja:

- Pobierz ze strony: https://code.visualstudio.com

- Zainstaluj jak zwykły program Windows

W opcjach instalatora warto zaznaczyć:

- "Add to PATH"

- "Register Code as an editor for supported file types"

- Visual Studio Code będzie gotowy do pracy z kodem JavaScript, HTML, CSS, a po rozszerzeniu również z React, TypeScript i wieloma innymi.

![](https://opengateweb.com/wp-content/uploads/2025/08/vsc-1324x745.png)

## Konfiguracja VSC i najważniejsze rozszerzenia i ustawienia

### Rozszerzenia (extensions) sprawiają, że VS Code staje się profesjonalnym środowiskiem. Oto must-have. Dodatkowo zrób sobie formatOnSave: true

- **Prettier** – automatyczne formatowanie kodu

- **ESLint** – wykrywanie błędów w kodzie JavaScript

- **React Snippets** – skróty do najczęściej używanych komponentów React

- **GitLens** – historia commitów i zaawansowane opcje Git

- **Live Server** – dodatek do podglądu strony projektu w przeglądarce, automatycznie odświeżający zawartość po zapisaniu pliku. Niezastąpiony przy pracy z HTML, CSS i JS.

- **JavaScript (ES6) code snippets** – gotowe skróty do często używanych składni JavaScript ES6.

- **HTML CSS Support** – rozszerzenie dodające podpowiedzi CSS wewnątrz plików HTML.

- **ES7+ React/Redux/React-Native snippets** – świetne rozszerzenie do tworzenia komponentów React i hooków jeszcze szybciej.

### **Jak dodać rozszerzenie do VS Code?**

Po lewej stronie znajdziesz ikonę kostki (Extensions). Kliknij ją, wpisz nazwę rozszerzenia, które chcesz zainstalować (np. Prettier, Live Server), a następnie kliknij przycisk „Install”. Gotowe – rozszerzenie jest aktywne.

W ustawieniach VS Code możesz dodatkowo dodać:

- W settings.json dodaj:

{
  "editor.formatOnSave": true,
  "editor.tabSize": 2,
  "files.autoSave": "onFocusChange"
}

![](https://opengateweb.com/wp-content/uploads/2025/08/extension-vsc-1324x745.png)

## Instalacja Git i Bash Git Bash

Po co?

Git to system kontroli wersji, a Bash daje wygodniejszy terminal niż domyślny CMD. Dzięki Git Bash możesz korzystać z poleceń unixopodobnych (ls, touch, etc.)

### Instalacja:

- Pobierz ze strony: [https://git-scm.com/](https://git-scm.com/)

- Podczas instalacji wybierz opcję "Use Git from the command line and also from 3rd-party software"

- Po instalacji wpisz:

git --version

![](https://opengateweb.com/wp-content/uploads/2025/08/cli-git-git-bash-1324x745.png)

## Tworzenie pierwszego projektu HTML Css JS

Zanim sięgniesz po Reacta, warto zacząć od prostego projektu frontendowego w HTML, CSS i JavaScript. To dobry sposób na naukę podstaw web developmentu i pracy w edytorze.

- Na pulpicie utwórz nowy folder, np. mojastrona

- Kliknij prawym przyciskiem myszy i wybierz „Otwórz w Visual Studio Code” (niebieska ikona)

Dodaj trzy pliki:

- index.html

- style.css

- script.js

- W index.html wpisz skrót:

! + Tab

To tzw. Emmet – system skrótów, który automatycznie tworzy strukturę dokumentu HTML. Z pewnością się zaprzyjaźnicie.

5.Połącz pliki:

<link rel="stylesheet" href="style.css">
<script src="script.js"></script>

6. Uruchom stronę klikając **prawym przyciskiem** na index.html i wybierając **Open with Live Server**.

7. Wprowadź zmianę w HTML lub CSS – przeglądarka odświeży się automatycznie.

## Pierwszy projekt w React z create-react-app

- W terminalu wpisz:

npx create-react-app moja-apka
cd moja-apka
npm start

- Otwórz folder w VS Code

- Uruchom lokalny serwer developerski

To jeden z najprostszych sposobów, aby uruchomić Reacta bez konfiguracji.

## Inne edytory kodu na Windows

Mimo że Visual Studio Code cieszy się największą popularnością wśród programistów, istnieje wiele innych wartościowych opcji, które również mogą być godne uwagi. 

Jednym z alternatywnych narzędzi jest Sublime Text, który słynie z szybkości i prostoty obsługi. Kolejną opcją wartą uwagi jest IntelliJ IDEA, szczególnie polecana dla programistów pracujących w języku Java. Dzięki różnorodności dostępnych narzędzi, programiści mogą znaleźć edytor kodu, który najlepiej odpowiada ich indywidualnym potrzebom i preferencjom. Warto eksperymentować z różnymi programami, aby znaleźć ten, który zapewni najbardziej efektywną pracę i komfort podczas codziennego programowania.

- **PHPStorm** (dla PHP)

- **Notepad++** (lekki edytor)

- **Sublime Text** (szybki i minimalistyczny)

- **Visual Studio** (dla C#, .NET)

## Synchronizacja ustawień i ustawienie VS Code z GitHub

Visual Studio Code pozwala połączyć się z Twoim kontem GitHub i synchronizować ustawienia edytora między komputerami. Dzięki temu nie musisz konfigurować środowiska od nowa na każdym urządzeniu.

### Jak to działa?

- Otwórz Command Palette (Ctrl+Shift+P)

- Wpisz Sign in with GitHub i wybierz polecenie

- Zaloguj się przez przeglądarkę do GitHub

- Po zalogowaniu wrócisz do edytora – Twoje konto jest połączone

- Ponownie otwórz Command Palette i wpisz Turn on Settings Sync

- Wybierz, co chcesz synchronizować: rozszerzenia, ustawienia, skróty, motywy

- Dane zapisywane są w GitHub Gist (prywatnie, automatycznie)

### **Co daje synchronizacja?**

- Twoje środowisko pracy wygląda identycznie na każdym komputerze

- Nie musisz zapamiętywać listy rozszerzeń ani kopiować plików konfiguracyjnych

- Zmiany wprowadzone na jednym urządzeniu są dostępne na drugim

Dodatkowo: po połączeniu z GitHub możesz korzystać z rozszerzeń takich jak GitLens, Copilot i wiele innych, które wymagają autoryzacji przez GitHub.

## Podsumowanie i co dalej

Masz już skonfigurowane środowisko z Visual Studio Code, Node.js i Git. Wiesz, jak stworzyć prosty projekt HTML/CSS/JS, jak działa terminal Git Bash i jak rozbudować VS Code o niezbędne rozszerzenia.

Co dalej?

- Opanuj podstawy terminala

- Naucz się pracy z Git i commitami

- Poznaj Docker i DevContainers do izolowania środowisk

- Eksperymentuj i buduj projekty

To dopiero początek – Twoje środowisko deweloperskie na Windows jest gotowe, a każdy nowy projekt będzie już tylko prostszy.

**Obrazy ilustrujące opisy**:

- Widok instalatora Visual Studio Code

- Terminal Git Bash z git --version

- Widok folderu projektu React w VS Code

- Panel rozszerzeń VS Code z Prettier i ESLint

- Synchronizacja ustawień z GitHub

- Widok prostej strony HTML uruchomionej przez Live Server
