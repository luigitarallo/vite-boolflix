# BoolFlix

## Overview

- This Vue.js web application for media search employs a component-based structure and leverages technologies like Axios for asynchronous data fetching, Font Awesome for visual representation, and SCSS for enhanced stylesheet management. The code comprises Vue components such as AppHeader, AppMain, MediaList, and MediaCard. The fetchMedia method dynamically retrieves movie and series data from external APIs, updating a custom store.js for state management. The application features responsive design elements, including a visually appealing card flip effect when interacting with media cards, and custom scrollbar styling for a personalized user interface.

## Key Features and Skills Improved:

- Vue.js Mastery: Demonstrated advanced proficiency in Vue.js through the implementation of a component-based structure, showcasing a deep understanding of Vue.js concepts such as data binding, event handling, and lifecycle hooks.

- Asynchronous Data Fetching: Strengthened skills in managing asynchronous operations using Axios to fetch data from external APIs. The efficient handling of asynchronous requests contributes to a seamless user experience by providing real-time updates.

- State Management Expertise: Applied custom state management techniques by utilizing a store.js file, showcasing the ability to manage and share application state effectively. This approach enhances code organization and facilitates seamless communication between components.

- Responsive Design Implementation: Showcased expertise in responsive design by incorporating CSS transitions and transforms. The responsive design practices ensure an optimal user experience across a variety of devices and screen sizes, emphasizing a commitment to user-centric design principles.

## Technologies Used:

- HTML
- CSS
- SASS pre-processor
- npm package manager
- Vite
- JavaScript
- VueJs
- Ajax requests using Axios

## Instructions

1. Open new terminal
2. Run command

```
npm i
```

3. Run command

```
npm run dev
```

4. Open the localhost

## ScreenShot

![Alt text](./public/img/boolfix-screenshot.png)

## TRACCIA

Replica della più famosa piattaforma streaming di film e serie TV

### Milestone 0

- Progettare la struttura del global state sulla linea degli esercizi svolti nei giorni precedenti.

### Milestone 1

- Creare un layout base con una searchbar (una input e un button) in cui possiamo
  scrivere completamente o parzialmente il nome di un film. Possiamo, cliccando il
  bottone, cercare sull’API tutti i film che contengono ciò che ha scritto l’utente.

- Vogliamo dopo la risposta dell’API visualizzare a schermo i seguenti valori per ogni
  film trovato:

1. Titolo
2. Titolo Originale
3. Lingua
4. Voto

### Milestone 2

- Trasformiamo la stringa statica della lingua in una vera e propria bandiera della
  nazione corrispondente, gestendo il caso in cui non abbiamo la bandiera della
  nazione ritornata dall’API

- Allarghiamo poi la ricerca anche alle serie tv. Con la stessa azione di ricerca
  dovremo prendere sia i film che corrispondono alla query, sia le serie tv, stando
  attenti ad avere alla fine dei valori simili (le serie e i film hanno campi nel JSON di
  risposta diversi, simili ma non sempre identici)

### Milestone 3

- In questa milestone come prima cosa aggiungiamo la copertina del film o della serie
  al nostro elenco. Ci viene passata dall’API solo la parte finale dell’URL, questo
  perché poi potremo generare da quella porzione di URL tante dimensioni diverse.

- Dovremo prendere quindi l’URL base delle immagini di TMDB:
  https://image.tmdb.org/t/p/ per poi aggiungere la dimensione che vogliamo generare
  (troviamo tutte le dimensioni possibili a questo link:
  https://www.themoviedb.org/talk/53c11d4ec3a3684cf4006400) per poi aggiungere la
  parte finale dell’URL passata dall’API.

- Trasformiamo poi il voto da 1 a 10 decimale in un numero intero da 1 a 5, così da
  permetterci di stampare a schermo un numero di stelle piene che vanno da 1 a 5,
  lasciando le restanti vuote (troviamo le icone in FontAwesome).
  Arrotondiamo sempre per eccesso all’unità successiva, non gestiamo icone mezze
  piene

### Milestone 4

- Trasformiamo quello che abbiamo fatto fino ad ora in una vera e propria webapp,
  creando un layout completo simil-Netflix:
  - Un header che contiene logo e search bar
  - Dopo aver ricercato qualcosa nella searchbar, i risultati appaiono sotto forma
    di “card” in cui lo sfondo è rappresentato dall’immagine di copertina (consiglio
    la poster_path con w342)
  - Andando con il mouse sopra una card (on hover), appaiono le informazioni
    aggiuntive già prese nei punti precedenti più la overview
