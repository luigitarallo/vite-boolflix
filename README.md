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

## SVOLGIMENTO

### Milestone 0

- Installo tutto il necessario per il corretto funzionamento di vue e vite
- Organizzo l'applicazione:

  - Creo dei componenti secondari per l'header ed il main (_AppMain_,_AppHeader_)
  - Li importo e registro nell'App principale
  - Creo un componente _MovieList_ che si interfaccerà solo con _AppMain_ che conterrà la lista dei film e serie TV
    - Lo importo e registro nell'App genitore
    - _MovieList_ avrà a sua volta un altro componente per creare la card _MediaCard_
      - Lo esporto e registro nel genitore
    - Creo uno store utile per salvare i dati richiesti tramite API in modo da renderli disponibili anche per altri componenti
      - Importo lo store nell'App principale _App_

### Milestone 1

- Creo una searchbar nell'_AppHeader_
  - la collego con una direttiva v-model perché mi servirà sapere cosa viene scritto nell'input
- Per inviare il parametro ricercato al genitore (_App_), avrò bisogno di un emit che verrà inviato al click del button o alla pressione del tasto Enter nell'input
- L'_emit_ arriva al genitore che scatena un metodo
  - Tramite _axios_ viene inviata una ricerca sul database contenente il parametro inserito nell'input
  - Costruisco il link per la ricerca utilizzando la _chiave api_ personale e la _parola_ da ricercare
  - salvo i valori ricevuti con chiavi personalizzate nello _store_ creato precedentemente
- Nell'app che deve contenere le card, importo lo store con i dati e **PER OGNI** risultato ricevuto stampo una card
- Invio i dati dello store tramite _props_ all'app figlia che si occuperà di creare solamente la card e visualizzare i dati ricevuti

### Milestone 2

- Creo un database con le bandiere più comuni per le lingue
- Dichiaro un oggetto con al suo interno una chiave che sarà la lingua del film e come valore un percorso al database con la bandiera corrispondete
- Quando interrogo il link per ricevere le informazioni del film, salvo i dati ricevuti in un oggetto, dichiaro una variabile _flag_ che si sostituirà al valore della lingua originale in caso di corrispondenza, **SE** non vi è corrispondenza, inserisco un' immagine di default

- Quando invoco il metodo per ricercare i film, creo un'altra chiamata per ricercare le serie
- salvo i dati in un secondo array di oggetti nello storage
- Nell'app _MediaList_ registro un secondo componente _MediaCard_ e **PER OGNI** oggetto nell'array stamperà una card, i dati da stampare li invio tramite la stessa props ma con dati _serie_ differenti

### Milestone 3

- Per poter stampare la compertina del film o serie tv, aggiungo una nuova chiave all'oggetto che mappo quando faccio la richiesta axios. Questa chiave conterrà il link parziale dell'immagine
- Quando ritorno l'array con le chiavi cambiate, cambio anche quella dell'immagine, aggiungo l'url rimanente dato dalla documentazione e per visualizzare correttamente il file alla dimensione impostata aggiungo anche un valore width all'url

- Installo i pacchetti di font-awesame nel file js principale dopo aver installato i pacchetti necessari
- Importo l'icona della stella che mi serve
- Per inserirle nella card
  - **PER OGNI** voto(numero ottenuto tramite api) aggiungo un'icona stella, così ottengo il voto
- Per inserire nella card le stelle vuote
  - **PER OGNI** voto(numero ottenuto tramite api) sottraggo a 5 ed ottengo le stelle vuote
  - Stilizzo le stelle rendendo colorate quelle corrispondenti al vuoto e nere quelle vuote
