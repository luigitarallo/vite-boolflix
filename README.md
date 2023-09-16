# BoolFlix

## TRACCIA

Replica della più famosa piattaforma streaming di film e serie TV!

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
