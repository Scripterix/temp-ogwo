---
title: "Post #16 Docker konteneryzacja"
date: 2025-02-28 07:39:55
author: Scripterix
slug: 16-post-docker
post_id: 534
categories:
  - "Coding Corner"
tags:
  - "container"
  - "docker"
  - "tools"
original_url: "https://opengateweb.com/posts/16-post-docker/"
---

# Docker narzędzie do konteneryzacji ?

## Czym jest Docker ?

**Docker** jest jak magiczna skrzynka, która pomaga Ci zapanować nad aplikacjami i ich środowiskami. Teraz, wyobraź sobie, że Docker to taka magiczna walizka 🧳, w której możesz trzymać wszystko, czego potrzebujesz do swoich aplikacji: kod, zależności, ustawienia środowiska, wszystko!

Teraz, ta magiczna walizka ma specjalne pojemniki, nazywane kontenerami 📦. W tych kontenerach trzymasz poszczególne elementy Twojej aplikacji. Ciekawe jest to, że każdy kontener jest jak mały świat dla Twojej aplikacji, mający wszystko, czego potrzebuje do pracy, bez wpływu na resztę środowiska. To oznacza, że możesz mieć kontener dla swojej aplikacji internetowej, inny dla bazy danych, a nawet kolejny dla usługi cachowania – każdy z nich działa niezależnie!

No dobrze, a teraz, jak to wszystko używać? Docker Desktop jest Twoim magicznym miejscem, gdzie zarządzasz wszystkimi tymi kontenerami. Po zainstalowaniu wystarczy, że uruchomisz Docker Desktop, i będziesz mógł tworzyć, uruchamiać, zatrzymywać i usuwać kontenery za pomocą kilku kliknięć myszką lub poleceń w terminalu. To takie proste, jak wrzucenie rzeczy do magicznej walizki i powiedzenie jej, aby działała!

I to wszystko! Teraz, gdy znasz trochę teori o konteneryzacji i używaniu Docker Desktop, możesz zacząć swoją przygodę z zarządzaniem aplikacjami jak prawdziwy magik! ✨

## Co jest najważniejsze do stworzenie kontenera ?

Kontener wie, co jest potrzebne z pliku package.json dzięki Dockerfile'owi. Dockerfile to taki magiczny przepis 📜, który mówi Dockerowi, jak zbudować kontener dla Twojej aplikacji. W Dockerfile'u określasz wszystko, czego Docker potrzebuje, aby zbudować środowisko dla Twojej aplikacji, włączając w to zależności zdefiniowane w pliku package.json.

W typowym środowisku Node.js, na przykład, gdy budujesz kontener, kopiujesz plik package.json do kontenera i uruchamiasz komendę npm install. To spowoduje, że Docker pobierze i zainstaluje wszystkie zależności wymienione w pliku package.json, umożliwiając Twojej aplikacji działać w izolowanym i spójnym środowisku.

Dzięki temu, gdy Twój kontener zostanie uruchomiony, będzie miał wszystkie zależności, których Twoja aplikacja potrzebuje, aby działać poprawnie, dzięki czemu możesz być pewny, że działa ona tak, jak powinna, niezależnie od otoczenia, w którym jest uruchomiona.

## Oto prosty przepis w formie Dockerfile'a

Załóżmy że chcemy uruchomić na hostingu App opartą działającą w Node.js i Express a nie mamy zainstalowanych zależności na naszym serwerze. Docelowo nie wiemy jakie środowiska będą w przyszłości. Uruchamiamy Dockefile, który wykonuje polecenie npm install:

# Użyj oficjalny obraz Node.js jako bazowy
FROM node:alpine

# Utwórz katalog aplikacji w kontenerze
WORKDIR /app

# Skopiuj pliki package.json i package-lock.json do katalogu /app w kontenerze
COPY package*.json ./

# Zainstaluj zależności przy użyciu npm install
RUN npm install

# Skopiuj resztę plików aplikacji do katalogu /app w kontenerze
COPY . .

# Domyślnie uruchom aplikację po uruchomieniu kontenera
CMD ["npm", "start"]

## Popularny obraz Docker Alpine

Docker "alpine"! Obraz ten jest jednym z najpopularniejszych obrazów bazowych używanych do tworzenia kontenerów Docker. Oferuje on minimalistyczną dystrybucję Linuxa opartą na musl libc i BusyBox, zajmującą zaledwie 5 MB miejsca. To sprawia, że jest świetnym wyborem do budowy lekkich i wydajnych kontenerów.

Oto kilka kluczowych informacji na temat **Docker Alpine**:

Rozmiar: Tylko 5 MB, co czyni go jednym z najlżejszych dostępnych obrazów. Repozytorium pakietów: Posiada dostęp do kompletnego repozytorium pakietów, co ułatwia instalację potrzebnych narzędzi i aplikacji. Obsługiwane architektury: Dostępny dla wielu różnych architektur, w tym amd64, arm, i386, ppc64le, s390x, itp. Użycie: Można go używać podobnie do innych obrazów bazowych. Przykładowo, można dodać dodatkowe narzędzia za pomocą apk add --no-cache lub wykonać inne konfiguracje w Dockerfile'u. Poniżej znajduje się prosty przykład użycia obrazu "alpine" w pliku Dockerfile:

FROM alpine:3.14

# Instalacja klienta MySQL
RUN apk add --no-cache mysql-client

# Definicja punktu wejścia (ENTRYPOINT)
ENTRYPOINT ["mysql"]

## Czym jest Docker kontener ?

Kontener to izolowane środowisko dla Twojego kodu. Oznacza to, że kontener nie ma wiedzy o Twoim systemie operacyjnym ani Twoich plikach. Działa w środowisku dostarczonym przez Docker Desktop. Kontenery posiadają wszystko, czego potrzebuje Twój kod do działania, łącznie z bazowym systemem operacyjnym. Możesz używać Docker Desktop do zarządzania i eksplorowania swoich kontenerów.

### Zasoby

[Docker Docs Guid](https://docs.docker.com/guides/)
