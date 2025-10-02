---
title: "Post #28 Angular Api"
date: 2025-03-18 02:47:07
author: Scripterix
slug: 28-post-angular-api
post_id: 741
categories:
  - "Coding Corner"
  - "Wyzwanie"
tags:
  - "angular"
  - "api"
  - "programming"
original_url: "https://opengateweb.com/posts/28-post-angular-api/"
---

Odświeżenie wiadomości i kodu Angular. Dowiedziałem się że właśnie jest stabilna v 18 wprowadzająca dużo zmian.

## Treść zadania do Aplikacji Angular

**Job Task** Używając modułu HttpModule w Angular 2+, napisz fragment kodu, który z poniższego API pobierze drugi element o statusie 'pending'. Ocenimy także jakość i wydajność Twojego rozwiązania. Link do API: [API To Do](https://gorest.co.in/public/v2/todos)

## Realizacja

Stworzyłem nową Aplikację Angular w wersji 14 i metodę fetch wraz z filtrem wyników. Dodatkowo stworzę rozwiązanie z Service i Subscribe,

## Kod Obecnej aplikacji

Dodany jest Bootstrap jako UI oraz Component Api wraz z routerem

// Router

import { NgModule } from '@angular/core';
import { RouterModule, Routes } from '@angular/router';
import { HomeComponent } from './components/home/home.component';
import { ApiComponent } from './components/api/api.component';

const routes: Routes = [
  { path: 'home', component: HomeComponent },
  { path: 'api', component: ApiComponent }
];

@NgModule({
  imports: [RouterModule.forRoot(routes)],
  exports: [RouterModule]
})
export class AppRoutingModule { }

// App Module

import { NgModule } from '@angular/core';
import { BrowserModule } from '@angular/platform-browser';
import { HttpClientModule } from '@angular/common/http';

import { AppRoutingModule } from './app-routing.module';
import { AppComponent } from './app.component';
import { HomeComponent } from './components/home/home.component';
import { ApiComponent } from './components/api/api.component';
import { NavComponent } from './components/nav/nav.component';

@NgModule({
  declarations: [
    AppComponent,
    HomeComponent,
    ApiComponent,
    NavComponent
  ],
  imports: [
    BrowserModule,
    AppRoutingModule,
    HttpClientModule
  ],
  providers: [],
  bootstrap: [AppComponent]
})
export class AppModule { }

// API-Components

import { HttpClient } from '@angular/common/http';
import { Component, OnInit } from '@angular/core';
import { Observable } from 'rxjs';
import { filter, map, tap } from 'rxjs/operators';

interface Task {
  id: number;
  user_id: number;
  title: string;
  due_on: string;
  status: string;
}

@Component({
  selector: 'app-api',
  templateUrl: './api.component.html',
  styleUrls: ['./api.component.css']
})
export class ApiComponent implements OnInit {

  tasks: Task[] = [];
  secondPendingTask: Task | undefined;

  constructor(private http: HttpClient) { }

  ngOnInit(): void {
    this.getSecondPendingTask()
      .subscribe(task => {
        this.secondPendingTask = task;
      }, error => {
        console.error('Error fetching task:', error);
      });
  }

  getSecondPendingTask(): Observable<Task> {
    return this.http.get<Task[]>('https://gorest.co.in/public/v2/todos')
      .pipe(
        // Filter tasks with status 'pending'
        filter(tasks => tasks.length > 1 && tasks[1].status === 'pending'),
        // Map to the second pending task (if found)
        map(tasks => tasks[1]),
        // Handle the case where no second pending task exists
        tap(task => {
          if (!task) {
            console.log('No second pending task found');
          }
        })
      );
  }
}

## Kod Html Api-component

<h1 class="display-4">API</h1>
<p class="lead">Api works!</p>

<div class="bg-light">
  <ul class="list-unstyled">
    <li *ngIf="secondPendingTask">
      (task Id: {{ secondPendingTask.id}}) **Second Pending Task:** <span>{{ secondPendingTask.title }} </span> (status:
      {{ secondPendingTask.status }})
    </li>
    <li *ngIf="!secondPendingTask">
      No second pending task found.
    </li>
  </ul>
</div>

## Krótka instrukcja krok po kroku

- Importuj moduł HttpClient z @angular/common/http w pliku api.component.ts.

- Wstrzyknij HttpClient do konstruktora komponentu.

- Stwórz metodę, która będzie wywoływać API za pomocą metody get() z HttpClient.

- Wywołaj tę metodę w cyklu życia komponentu, np. ngOnInit().

- Przechowaj odpowiedź z API w zmiennej w komponencie.

- Wyświetl dane w szablonie komponentu za pomocą dyrektywy *ngFor.
