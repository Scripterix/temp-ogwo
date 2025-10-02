---
title: "Jak zacząć naukę Pythona w Windows i Visual Studio Code Post #70"
date: 2025-08-28 05:29:38
author: Scripterix
slug: jak-zaczac-nauke-pythona-w-windows-i-visual-studio-code-post-70
post_id: 2003
categories:
  - "Coding Corner"
  - "Wyzwanie"
tags:
  - "python"
original_url: "https://opengateweb.com/posts/jak-zaczac-nauke-pythona-w-windows-i-visual-studio-code-post-70/"
---

## Jak zacząć naukę Pythona w Windows i Visual Studio Code

W poniższej treści dowiesz się jak skonfigurować w kilku prostych krokach środowisko do pracy w Python.

## Spis treści

- Instalacja Pythona w systemie Windows

- Konfiguracja i sprawdzenie instalacji

- Instalacja edytora Visual Studio Code

- Niezbędne rozszerzenia w VS Code

- Pierwszy projekt i uruchamianie kodu

- Tworzenie wirtualnego środowiska

- Kolejne kroki nauki

## Instalacja Pythona w systemie Windows

Pierwszym krokiem jest pobranie języka Python z oficjalnej strony [python.org/downloads](https://python.org/downloads?utm_source=chatgpt.com). Wybierz najnowszą stabilną wersję przeznaczoną dla systemu Windows (np. Python 3.12.x).

Podczas instalacji koniecznie zaznacz opcję **Add Python to PATH**, dzięki czemu interpreter będzie dostępny z poziomu terminala. Następnie wybierz instalację domyślną (Install Now).

Po zakończeniu instalacji sprawdź, czy wszystko działa poprawnie. Otwórz **CMD** lub **PowerShell** i wpisz:

python --version

Jeśli instalacja przebiegła pomyślnie, zobaczysz komunikat w rodzaju:Python 3.12.2

## Instalacja Visual Studio Code

Visual Studio Code to popularny edytor kodu, który świetnie współpracuje z Pythonem. Pobierz go z oficjalnej strony [code.visualstudio.com](https://code.visualstudio.com?utm_source=chatgpt.com) i zainstaluj z domyślnymi ustawieniami.

Warto podczas instalacji zaznaczyć opcję integracji z terminalem oraz dodanie polecenia **Open with Code** w menu kontekstowym systemu Windows. Dzięki temu łatwiej otworzysz projekty i pliki bezpośrednio w edytorze. 

Jeśli chcesz dowiedzieć się łatwo [jak zainstalować VSC](https://opengateweb.com/posts/post-66-jak-zbudowac-srodowisko-programistyczne-na-windows-visual-studio-code-git-node-js/) - zobacz nasz poradnik

## Niezbędne rozszerzenia w VS Code

Po uruchomieniu edytora przejdź do zakładki **Extensions** (skrót klawiszowy Ctrl + Shift + X). Wyszukaj i zainstaluj następujące rozszerzenia:

- **Python (Microsoft)** – oficjalne wsparcie dla Pythona, zawierające debugger i narzędzia do pracy z kodem.

- **Pylance** – rozszerzenie zapewniające szybkie i precyzyjne podpowiedzi składni oraz typów.

- **Code Runner** – opcjonalne narzędzie pozwalające szybko uruchamiać fragmenty kodu bez konieczności konfiguracji projektu.

## Pierwszy projekt i uruchamianie kodu

- Utwórz folder na swoje projekty, np. C:\PythonProjects\HelloWorld.

- W Visual Studio Code otwórz ten folder przez menu **File → Open Folder**.

- Dodaj nowy plik o nazwie main.py.

Wpisz w nim prosty kod:

print("Hello, Python!")

Plik możesz uruchomić na dwa sposoby:

- klikając przycisk **Run Python File** w prawym górnym rogu edytora,

- lub wpisując w terminalu VSC:

python main.py

## Podsumowanie

Po wykonaniu tych kroków masz już w pełni działające środowisko programistyczne. Możesz od razu pisać własne skrypty i rozwijać je w kierunku automatyzacji, tworzenia aplikacji webowych (Flask, Django), analizy danych (Pandas, NumPy) czy sztucznej inteligencji (PyTorch, TensorFlow). Co dalej ? Możesz skorzystać z wielu gotowych kursów lub [sprawdź jak jak się uczę Python](https://opengateweb.com/posts/10-post-python/).
