---
title: "Post #14 Hugo Layout Development"
date: 2025-02-26 00:06:50
author: Scripterix
slug: 14-post-hugo-layouts-2
post_id: 519
categories:
  - "Design Hub"
tags:
  - "design-layout"
  - "hugo-generator"
original_url: "https://opengateweb.com/posts/14-post-hugo-layouts-2/"
---

# #14 Modyfikacje layout i theme Hugo PaperMod

## Dodałem Archiwa i Categorie do szablonu, bez przyjaciół się obejdzie/

## Modyfikacja layout categories i archiwa

**Moje główne kategorie**

- Tech News

- Coding Corner

- Design Hub

## Oznaczam post jako Design Hub

Taksonomie to zdefiniowane przez użytkownika grupowane treści. Są one sposobem klasyfikacji i organizacji treści na podstawie logicznych relacji. Na przykład, na stronie internetowej o filmach, możesz mieć taksonomie dla Aktorów, Reżyserów, Studiów, Gatunków, Lat i Nagród.

Każda taksonomia ma **Terminy**, które są kluczami w ramach taksonomii. Na przykład, w taksonomii Aktorów, nazwa każdego aktora byłaby terminem.

Każdy termin ma Wartości, które są elementami treści przypisanymi do terminu. Na przykład, w taksonomii Aktorów, filmy, w których wystąpił każdy aktor, byłyby wartościami dla terminu tego aktora.

Hugo automatycznie tworzy taksonomie dla tagów i kategorii. Możesz to zobaczyć na przykład na stronie [Kategorie](https://file+.vscode-resource.vscode-cdn.net/categories/) można również zdefiniować niestandardowe taksonomie w pliku konfiguracyjnym swojej strony **hugo.toml**.

Możesz przypisać treść do taksonomii w metadanych treści. Na przykład, aby przypisać wpis na blogu do kategorii "Development" i serii "Go Web Dev", należy umieścić kategorie = ['Development'] oraz series = ['Go Web Dev'] w metadanych wpisu.

Możesz dodać niestandardowe metadane do terminów taksonomii, tworząc stronę dla terminu i dodając metadane w metadanych przedniej części.

Dostarczony wcześniej plik układu categories.html służy do generowania strony z listą kategorii. Ta strona wyświetla wszystkie kategorie używane na Twojej stronie, a dla każdej kategorii dostarcza link do strony wyświetlającej wszystkie wpisy w tej kategorii. Linia {{ .Data.Terms.Alphabetical }} to miejsce, gdzie Hugo iteruje po wszystkich kategoriach w porządku alfabetycznym.

## Linki do stron dodane do Stopki

Dodałem do stopki **Kategorie**

## Stworzenie Series

Dodatkowo do categori tagów dodałem series. Przejdź i zobacz dodatkową funkcjonalność Taxonometrii Hugo. [Categories](https://file+.vscode-resource.vscode-cdn.net/categories/) [Archives](https://file+.vscode-resource.vscode-cdn.net/archives/)

## Jak zrobić archives i categories w Hugo

Trzeba założyć strony w katalogu content. Trzeba pamiętać że nie są to zwykłe pages lub post i powinny być poza tymi folderami w głównym folderze **content** poniżej front-matters.

- Plik categories.md

---
title: "Categories from here"
layout: "categories"
url: "/categories/"
summary: categories
---

- Plik archives.md

---
title: "Archive"
layout: "archives"
url: "/archives/"
summary: archives
---

Oba pliki są tylko z front-matters - treść jest generowana dynamicznie dodatkowo w głównym pliku config calej applikacji **hugo.toml** należy dodać params

[taxonomies]
  tag = "tags"
  category = "categories"
  series = "series"

W zależności jeśli chcemy umieścić linki do tych stron w menu to należy dopisać do menu odpowiednie params. W moim przypadku zmodyfikowałem layout footer.html

- Plik footer.html

<span>
        Powered by
        <a href="https://gohugo.io/" rel="noopener noreferrer" target="_blank">Hugo</a> &
        <a href="https://github.com/adityatelange/hugo-PaperMod/" rel="noopener" target="_blank">PaperMod</a> |
        <a href="/pages/sitemap" rel="noopener" target="_blank">Sitemap</a> |
        <a href="/archives/" rel="noopener" target="_blank">Archives</a> |
        <a href="/categories/" rel="noopener" target="_blank">Categories</a>
    </span>

Pliki szablonów - dla archives szablon był przygotowany a dla categories.html trzeba stworzyć plik layouts_default\categories.html ( zwróć uwagę że front-matters wskazuje na szablon layout: "categories" )

- Plik szablonu categories.html ( Do sprawdzenia dodawanie / customizowanie dodatkowego css. )

{{ define "main" }}
<div class="container">
  <h1>Categories</h1>
  {{ range $key, $value := .Site.Taxonomies.categories }}
  <a href="{{ "categories/" | relLangURL }}{{ $key | urlize }}">{{ $key }}</a> ({{ len $value }})
  {{ end }}

  <h2 style="margin-top: 2rem;">Series</h2>
  {{ range $key, $value := .Site.Taxonomies.series }}
  <a href="{{ "series/" | relLangURL }}{{ $key | urlize }}">{{ $key }}</a> ({{ len $value }})
  {{ end }}

  <h2 style="margin-top: 2rem;">Tags</h2>
  {{ range $key, $value := .Site.Taxonomies.tags }}
  <a href="{{ "tags/" | relLangURL }}{{ $key | urlize }}" style="margin-left: 0.25rem; margin-right: 0.25rem;">{{ $key }}</a> ({{ len $value }})
  {{ end }}
</div>
{{ end }}

I wszystko gotowe.
