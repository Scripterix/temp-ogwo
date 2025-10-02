---
title: "Post #20 Fluter pierwsza mobile app"
date: 2025-03-04 09:28:00
author: Scripterix
slug: 20-post-flutter
post_id: 556
categories:
  - "Coding Corner"
tags:
  - "crash-course"
  - "dart"
  - "flutter"
  - "mobile-dev"
original_url: "https://opengateweb.com/posts/20-post-flutter/"
---

# Research wyboru technologi Mobile App : Flutter

Po dokonaniu sporego researchu na temat wykonania app mobilnej zdecywałem się przetestować Flutter. Jest ciekawy. Postanowiłem uczyć się Dart i używać Flutter.

## Co to jest Flutter ?

**Flutter:** Flutter jest coraz bardziej popularnym wyborem dla tworzenia aplikacji mobilnych na platformy Android i iOS. Warto się uczyć języka Dart, używanego w Flutterze, oraz korzystać z narzędzi i bibliotek oferowanych przez Fluttera. 

Flutter pozwala na tworzenie aplikacji mobilnych zarówno na platformę Android, jak i iOS, co stanowi oszczędność czasu i pieniędzy przy dużych projektach. Nie trzeba tworzyć oddzielnych kodów dla różnych platform, co znacząco ułatwia proces tworzenia aplikacji. 

Zalety Fluttera obejmują szybkość działania, wydajność, atrakcyjny interfejs użytkownika, łatwą integrację z innymi technologiami, duże wsparcie społeczności oraz możliwość natychmiastowej aktualizacji aplikacji bez konieczności ponownego publikowania w sklepach aplikacji.

### Pierwsza App Mobilna Hello Flutter

Zrobiłem swoją pierwszą app mobilną we [Flutterze](https://docs.flutter.dev/) ( zapoznaj się z docs). Jak na poniższym kodzie. Kroki instalacji są dość proste.

Dodanie plugins do VSC Dart *Dart Code i Flutter Dart Code *

*VSC pobierze sdk które trzeba zainstalować i dodać do zmiennych środowiskowych PATH ( robi to automatycznie) *

Ctr + Shift + P 'Flutter New Project"

## Kod strony z Flutter z dodaniem About i Text

import 'package:flutter/material.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  // This widget is the root of your application.
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      debugShowCheckedModeBanner: false,
      title: 'Flutter Demo',
      theme: ThemeData(
        // This is the theme of your application.
        //
        // TRY THIS: Try running your application with "flutter run". You'll see
        // the application has a purple toolbar. Then, without quitting the app,
        // try changing the seedColor in the colorScheme below to Colors.green
        // and then invoke "hot reload" (save your changes or press the "hot
        // reload" button in a Flutter-supported IDE, or press "r" if you used
        // the command line to start the app).
        //
        // Notice that the counter didn't reset back to zero; the application
        // state is not lost during the reload. To reset the state, use hot
        // restart instead.
        //
        // This works for code too, not just values: Most code changes can be
        // tested with just a hot reload.
        colorScheme: ColorScheme.fromSeed(seedColor: Colors.deepPurple),
        useMaterial3: true,
      ),
      home: const MyHomePage(title: 'Home'),
      routes: {
        '/about': (context) => const AboutPage(),
      },
    );
  }
}

class MyHomePage extends StatefulWidget {
  const MyHomePage({super.key, required this.title});

  // This widget is the home page of your application. It is stateful, meaning
  // that it has a State object (defined below) that contains fields that affect
  // how it looks.

  // This class is the configuration for the state. It holds the values (in this
  // case the title) provided by the parent (in this case the App widget) and
  // used by the build method of the State. Fields in a Widget subclass are
  // always marked "final".

  final String title;

  @override
  State<MyHomePage> createState() => _MyHomePageState();
}

class _MyHomePageState extends State<MyHomePage> {
  int _counter = 0;

  void _incrementCounter() {
    setState(() {
      // This call to setState tells the Flutter framework that something has
      // changed in this State, which causes it to rerun the build method below
      // so that the display can reflect the updated values. If we changed
      // _counter without calling setState(), then the build method would not be
      // called again, and so nothing would appear to happen.
      _counter++;
    });
  }

  @override
  Widget build(BuildContext context) {
    // This method is rerun every time setState is called, for instance as done
    // by the _incrementCounter method above.
    //
    // The Flutter framework has been optimized to make rerunning build methods
    // fast, so that you can just rebuild anything that needs updating rather
    // than having to individually change instances of widgets.
    return Scaffold(
      appBar: AppBar(        
        // TRY THIS: Try changing the color here to a specific color (to
        // Colors.amber, perhaps?) and trigger a hot reload to see the AppBar
        // change color while the other colors stay the same.
        backgroundColor: Theme.of(context).colorScheme.inversePrimary,
        // Here we take the value from the MyHomePage object that was created by
        // the App.build method, and use it to set our appbar title.
        title: Text(widget.title),
        actions: [
          IconButton(
            icon: const Icon(Icons.info),
            onPressed: () {
              Navigator.of(context).pushNamed('/about');
            },
          ),
        ],
      ),
      body: Center(
        // Center is a layout widget. It takes a single child and positions it
        // in the middle of the parent.
        child: Column(
          // Column is also a layout widget. It takes a list of children and
          // arranges them vertically. By default, it sizes itself to fit its
          // children horizontally, and tries to be as tall as its parent.
          //
          // Column has various properties to control how it sizes itself and
          // how it positions its children. Here we use mainAxisAlignment to
          // center the children vertically; the main axis here is the vertical
          // axis because Columns are vertical (the cross axis would be
          // horizontal).
          //
          // TRY THIS: Invoke "debug painting" (choose the "Toggle Debug Paint"
          // action in the IDE, or press "p" in the console), to see the
          // wireframe for each widget.
          mainAxisAlignment: MainAxisAlignment.center,
          children: <Widget>[
            const Text(
              'You have pushed the button this many times:',
            ),
            Text(
              'First Hello from Flutter', // Zmień ten tekst na "Hello Flutter"
              style: Theme.of(context).textTheme.headlineMedium,
            ),
            Text(
              '$_counter',
              style: Theme.of(context).textTheme.headlineMedium,
            ),
          ],
        ),
      ),
      floatingActionButton: FloatingActionButton(
        onPressed: _incrementCounter,
        tooltip: 'Increment',
        child: const Icon(Icons.add),
      ), // This trailing comma makes auto-formatting nicer for build methods.
    );
  }
}

class AboutPage extends StatelessWidget {
  const AboutPage({super.key});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('About'),
      ),
      body: const Center(
          child: Text(
            'This is the about page.',
            style: TextStyle(
              fontSize: 24, // ustawia rozmiar czcionki na 24
              fontWeight: FontWeight.normal, // ustawia grubość czcionki na bold
            ),
          ),
      ),
    );
  }
}

## Kod we Flutterze używający biblioteki image_picker

Aby stworzyć aplikację mobilną, w której użytkownik może zrobić zdjęcie i przesłać je lub zapisać, należy wykonać następujące kroki

- Wybierz odpowiednią bibliotekę do obsługi zdjęć, na przykład image_picker, która umożliwia korzystanie z aparatu i galerii urządzenia. 

- Dodaj odpowiednie uprawnienia do aplikacji w pliku AndroidManifest.xml (dla systemu Android) i Info.plist (dla systemu iOS), aby umożliwić dostęp do aparatu i przechowywania zdjęć. 

-  Skonfiguruj interfejs użytkownika, aby użytkownik mógł wywołać funkcję robienia zdjęć, na przykład poprzez przycisk "Zrób zdjęcie". 

- Użyj odpowiednich metod z biblioteki image_picker, na przykład ImagePicker().getImage(), aby zrobić zdjęcie. 

- Po zrobieniu zdjęcia, możesz przesłać je na serwer za pomocą metody POST lub zapisywać je na urządzeniu za pomocą metody FileSystem.writeFile(). 

- Upewnij się, że obsługujesz odpowiednie błędy i komunikujesz użytkownikowi rezultaty operacji, na przykład poprzez wyświetlenie komunikatu o sukcesie lub błędzie. 

Poniższy kod przedstawia próbkę implementacji funkcji robienia i zapisywania zdjęć we Flutterze: 

Pamiętaj, że każda aplikacja mobilna różni się od siebie i wymaga dostosowania implementacji do swoich konkretnych wymagań i interfejsu użytkownika.

Do zrobienia zdjęcia z kamery można użyć biblioteki image_picker i z tym wszystko załatwić z kilku linii kodu. Zapis zdjęcia w pamięci urządzenia może wymagać więcej linii kodu, ale i tak nie jest to coś bardzo trudnego.

import 'dart:io';
import 'package:flutter/material.dart';
import 'package:image_picker/image_picker.dart';

class MyApp extends StatefulWidget {
  MyApp({Key key}) : super(key: key);

  @override
_MyAppState createState() => _MyAppState();
}

class _MyAppState extends State<MyApp> {
  File _image;

  void _takePicture() async {
    final imagePicker = ImagePicker();
    final pickedFile = await imagePicker.getImage(source: ImageSource.camera);

    if (pickedFile != null) {
      setState(() {
        _...

### Następnie API Async Xhr Ajax metody fetch()

### Dopracowanie szczegółów app i research wyboru architektury i technologi
