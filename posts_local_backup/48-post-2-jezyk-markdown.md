---
title: "Post #2 język Markdown"
date: 2025-02-06 07:36:08
author: Scripterix
slug: 2-jezyk-mark-down
post_id: 48
categories:
  - "Coding Corner"
tags:
  - "mark-down"
  - "markdown"
original_url: "https://opengateweb.com/posts/2-jezyk-mark-down/"
---

## **Markdown language**

**Markdown** to lekki język znaczników służący do formatowania tekstu w prosty i czytelny sposób. Używa intuicyjnej składni (np. **gwiazdek** do pogrubienia, # do nagłówków), co pozwala łatwo tworzyć sformatowane dokumenty bez znajomości HTML.

### **Gdzie się stosuje?**

- Dokumentacja techniczna (np. GitHub, GitLab, Bitbucket)

- Tworzenie notatek (np. Obsidian, Joplin)

- Blogi i CMS-y (np. Jekyll, Hugo)

- Komunikatory (np. Slack, Discord)

- Readme pliki w repozytoriach

### **Zalety Markdown:**

✅ **Łatwość użycia** – czytelny nawet bez renderowania✅ **Lekkość** – zwykły plik tekstowy, działa wszędzie✅ **Uniwersalność** – konwertowalny do HTML, PDF, LaTeX✅ **Obsługa w wielu narzędziach** – edytory kodu, platformy programistyczne

Mark down to świetne rozwiązanie, jeśli chcesz pisać sformatowany tekst szybko i bez zbędnych komplikacji. 🚀

Jeśli chcesz szybko nauczyć się Mark down, stwórz plik o dowolnej nazwie na przykład **index.md** i edytuj w VSC oto kilka podstawowych elementów, które warto poznać aby zacząć używać języka MD. 

Nagłówki i Tekst

# Nagłówek 1
## Nagłówek 2
### Nagłówek 3
#### Nagłówek 4
##### Nagłówek 5
###### Nagłówek 6

*Tekst kursywą* jest kursywą

**Ten tekst** jest pogrubiony

~~Ten tekst~~ jest przekreślony

*This text* jest italic

> To jest cytat

Tak tworzymy linki w Mark down

[Link do strony](http://www.example.com)
[Adres linku ](http://www.example.com "Nazwa linku")

Listy i formatowanie 

* Element 1
* Element 2
  * Zagnieżdżony element 1
  * Zagnieżdżony element 2

1. Element 1
2. Element 2
3. Element 3

<!-- Blokowy kod -->
`<p>To jest paragraf</p>`

<!-- Span blok kodu z Css-->
`<span class="bg-crimson">To jest span z css</p>`

## headingos {#id .className attrName=attrValue class="bg-crimson"}

`Kod w jednej linii`

**Polecenia cli** lub p**rzykładu kodu funkcji JavaScript **zapisujemy za pomocą  **backtick** (po polsku: **odwrócony apostrof** lub **gravis**)

`

Pojedynczy backtick ` – używany do oznaczania kodu w linii, np. print("Hello, World!")

Potrójny backtick ``````` – używany do bloków kodu

```bash
  npm install

  npm start
```

```JavaScript
  function dodaj(num1, num2) {
    return num1 + num2;
  }

console.log(dodaj);
```

Markdown jest bardzo użytecznym narzędziem do formatowania tekstu w prosty i czytelny sposób, więc warto go poznać! 

Markdown – język znaczników przeznaczony do formatowania tekstu zaprojektowany został przez Johna Grubera i Aarona Swartza. 

Więcej informacji o tym języku znajdziesz na stronie [GitHub](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax)
