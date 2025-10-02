---
title: "Post #13 CRUD"
date: 2025-02-23 15:46:41
author: Scripterix
slug: 13-post-crud-2
post_id: 514
categories:
  - "Coding Corner"
  - "Wyzwanie"
tags:
  - "crud"
  - "Express.js"
  - "teachers grade book"
original_url: "https://opengateweb.com/posts/13-post-crud-2/"
---

## **13 App Teachers Grade book**

Aplikacja CRUD Teacher's Grade book posiada już konkretny kształt i jest zorganizowana na poziomie Read i Create. Express i Node świetnie współpracują. App jest szybka jak lubię.

Skrypt pobiera dane studentów z serwera i wyświetla je w tabeli podczas ładowania strony fetch(). Nasłuchuje również na przesłanie formularza, aby dodać nowego studenta. Gdy formularz zostanie przesłany, wysyła żądanie POST do serwera z danymi nowego studenta i dodaje nowego studenta do tabeli. Nowy student pojawia się w tabeli, powiadomienia o działaniu są w postaci Alertów Bootstrap.

Aby dodać nowego studenta do tabeli natychmiast po przesłaniu formularza, używamy nasłuchiwanie zdarzeń przesłania formularza irównież tworzymy nowy wiersz tabeli dla nowego studenta aby dołączać go do tabeli.

## **Oto logika aplikacji :**

Gdy formularz zostanie przesłany, zapobiegamy domyślnemu zachowaniu przesłania formularza.

- Pobierz wartości pól wejściowych i utwórz nowy obiekt studenta.

- Wyślij żądanie POST do serwera z danymi nowego studenta.

- Jeśli żądanie POST zakończy się sukcesem, utwórz nowy wiersz tabeli dla nowego studenta i dołącz go do tabeli.

- Zaloguj odpowiedź serwera i wyczyść pola formularza.

- Jeśli wystąpi błąd, zaloguj błąd.

- Jeśli chodzi o alert, używamy go do wyświetlenia okna alertu z komunikatem o dodaniu studenta.

## Dodałem funkcjonalność fetch() Crud R

Dane są pobierane i wyświetlane w tabeli. fetch() jest w części main.js i ustalone jako endpoint **localhost:3000/api/student**

## Dodałem funcjonalność Crud C

Funcjonalność Create student została dodana. Dodane Id poza na razie istnieje poza generacją skryptem. Zostaną zastąpioone po dopisaniu **D Delete** Jeśli dodajemy nowego studenta dodaje prawidłowy uuid z Library uuid v.4.

**logbook.json**

{
  "students": [
    {
      "id": "<uuid>",
      "name": "John",
      "grade": "A",
      "age": 18
    },
    {
      "id": "<uuid>",
      "name": "Emily",
      "grade": "B",
      "age": 17
    },
    {
      "id": "<uuid>",
      "name": "Michael",
      "grade": "C",
      "age": 16
    },
    {
      "name": "Piotr",
      "grade": "A",
      "age": "55",
      "id": "1dd4d74b-ddb6-4e87-b2f8-9fc04e91ad3a"
    },
    {
      "name": "Tom",
      "grade": "B",
      "age": "8",
      "id": "c7fe0ea0-434e-410d-b919-d427949736ff"
    }
  ]
}

## Kod dla server.js i kod logiki main.js

**server.js**

express = require('express');
const { v4: uuidv4 } = require('uuid');
const fs = require('fs');
const path = require('path');

const app = express();

// Middleware to parse JSON bodies
app.use(express.json());

// Serve static files from the public directory
app.use(express.static(path.join(__dirname, 'public')));

// Read the logbook.json file and parse it as JSON
const data = JSON.parse(fs.readFileSync(path.join(__dirname, 'logbook.json'), 'utf-8'));

// API endpoint to get all students
app.get('/api/students', (req, res) => {
  res.json(data.students);
});

// API endpoint to add a new student
app.post('/api/students', (req, res) => {
  // Get the new student data from the request body
  const newStudent = req.body;

  // Add a unique id to the new student
  newStudent.id = uuidv4();

  // Add the new student to the data
  data.students.push(newStudent);

  // Write the updated data back to the logbook.json file
  fs.writeFileSync(path.join(__dirname, 'logbook.json'), JSON.stringify(data, null, 2));

  // Send the new student data back as the response
  res.json(newStudent);
});

app.listen(3000);
console.log('Listening on port 3000');

**main.js**

// Fetch the student data from the API
const form = document.querySelector('#studentForm');
const studentName = document.querySelector('#name');
const studentGrade = document.querySelector('#grade');
const studentAge = document.querySelector('#age');
const submitButton = document.querySelector('#submit');
const alertSuccess = document.querySelector('#alertSuccess');
const alertDanger = document.querySelector('#alertDanger');

fetch('/api/students')
  .then(response => response.json())
  .then(data => {
    // Get the table body to insert the student data into
    const tableBody = document.querySelector('#student-table tbody');

    // Loop over each student in the data
    for (const student of data) {
      // Create a new table row for the student
      const tr = document.createElement('tr');

      // Create table data for each piece of student data
      const nameTd = document.createElement('td');
      nameTd.textContent = student.name;
      tr.appendChild(nameTd);

      const gradeTd = document.createElement('td');
      gradeTd.textContent = student.grade;
      tr.appendChild(gradeTd);

      const ageTd = document.createElement('td');
      ageTd.textContent = student.age;
      tr.appendChild(ageTd);

      // Append the table row to the table body
      tableBody.appendChild(tr);
    }
  });

// Function to add a new student
form.addEventListener('submit', (event) => {
  // Prevent the form from being submitted normally
  event.preventDefault();

  // Get the values of the input fields
  const name = studentName.value;
  const grade = studentGrade.value;
  const age = studentAge.value;

  // Create a new student object
  const newStudent = {
    name: name,
    grade: grade,
    age: age
  };

  // Send a POST request to the API with the new student's data
  fetch('/api/students', {
    method: 'POST',
    headers: {
      'Content-Type': 'application/json',
    },
    body: JSON.stringify(newStudent),
  })
    .then(response => {
      if (!response.ok) {
        throw new Error(`HTTP error! status: ${response.status}`);
      }
      return response.json();
    })
    .then(data => {
      // Log the response from the API
      console.log('Success:', data);

      // Show the success alert
      alertSuccess.hidden = false;

      // Add the new student to the table
      const tableBody = document.querySelector('#student-table tbody');
      const tr = document.createElement('tr');

      const nameTd = document.createElement('td');
      nameTd.textContent = data.name;
      tr.appendChild(nameTd);

      const gradeTd = document.createElement('td');
      gradeTd.textContent = data.grade;
      tr.appendChild(gradeTd);

      const ageTd = document.createElement('td');
      ageTd.textContent = data.age;
      tr.appendChild(ageTd);

      tableBody.appendChild(tr);

      // Clear the form fields
      studentName.value = '';
      studentGrade.value = '';
      studentAge.value = '';
    })
    .catch((error) => {
      console.error('Error:', error);

      // Show the danger alert
      alertDanger.hidden = false;
    });
});

// Reload the page when the success alert is dismissed
alertSuccess.querySelector('.btn-close').addEventListener('click', () => {
  location.reload();
});

// Reload the page when the danger alert is dismissed
alertDanger.querySelector('.btn-close').addEventListener('click', () => {
  location.reload();
});

## Więcej objaśnień na temat API i JSON z Express jest postach poprzenich.

Dodatkowo dla ambitnych Advance Usage Express [The Medium Article](https://medium.com/@arulvalananto/5-advanced-nodejs-techniques-6ac0b7b024a8) w tym arykule znajdziesz:

**"5 Zaawansowanych Technik NodeJS z ExpressJS":**

- Dodawanie Pośredników (Middleware)

- Używanie Globalnego Obsługi Błędów

- Użycie Niższych Funkcji Try-Catch

- Oddzielenie Głównego Pliku na Dwie Części

- Oddzielenie Tras od Kontrolerów

[Post #11 API](https://opengateweb.com/posts/11-post-api/)

[Post #12 App Teachers Grade Book](https://opengateweb.com/posts/12-post-teachers/)

### **GitHub commands practice**

Od dobrej powtórki GitHub czyli Git versjononowanie i praca z repozytorium większość projektów jest przesyłana na GitHub lub tworzone są Gist do ponownego wykorzystania.

[Git Hub Repositorium](https://github.com/Scripterix/crud-express-json)

Więcej o Git i Gist w poniższym poście.

[GitHub commands](https://opengateweb.com/posts/8-post-gist/)

Od dobrej powtórki GitHub czyli Git versjononowanie i praca z repozytorium większość projektów jest przesyłana na GitHub lub tworzone są Gist do ponownego wykorzystania.

[Git Hub Repositorium](https://github.com/Scripterix/crud-express-json)
