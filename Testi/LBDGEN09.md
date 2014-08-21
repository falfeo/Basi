Prova scritta dell’esame di Laboratorio di Basi di Dati 15 Gennaio 2009

ATTORI (CodAttore, Nome, AnnoNascita, Nazionalità);

RECITA (CodAttore*, CodFilm*)

FILM (CodFilm, Titolo, AnnoProduzione, Nazionalità, Regista, Genere)

PROIEZIONI (CodProiezione, CodFilm*, CodSala*, Incasso, DataProiezione)

SALE (CodSala, Posti, Nome, Città)

1. Determinare il numero dei film interpretati da Brad Pitt e Angelina Jolie.
2. Per ogni sala di Palermo, che nel mese di gennaio 2005 ha incassato più di 20000 €, il nome della sala e l’incasso totale (sempre del mese di gennaio 2005
3. Per ogni film di fantascienza che non è mai stato proiettato prima del 1/1/01, il titolo e l’incasso totale di tutte le sue proiezioni
4. Elencare tutte le coppie di attori che hanno lavorato almeno una volta insieme nello stesso film
5. Scrivere una procedura che cancella dal database tutti i film della tabella FILM il cui anno di produzione è successivo ad un anno, dato come parametro.
6. Scrivere un trigger che alla cancellazione di un film dalla tabella FILM, lo inserisca in una nuova tabella “VECCHI FILM” con gli stessi attributi
