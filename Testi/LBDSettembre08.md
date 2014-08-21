SCHEMA RELAZIONALE:

ATTORI (CodAttore, Nome, AnnoNascita, Nazionalità);

RECITA (CodAttore*, CodFilm*)

FILM (CodFilm, Titolo, AnnoProduzione, Nazionalità, Regista, Genere)

PROIEZIONI (CodProiezione, CodFilm*, CodSala*, Incasso, DataProiezione)

SALE (CodSala, Posti, Nome, Città)

Scrivere le interrogazioni SQL che restituiscono le seguenti informazioni

1. Per ogni regista, l’incasso totale di tutte le proiezioni dei suoi film.
2. Per ogni film di S.Spielberg, il titolo del film, il numero totale di proiezioni a Pisa e l’incasso.
3. Per ogni sala di Pisa, che nel mese di gennaio 2005 ha incassato più di 20000 €, il nome della sala e l’incasso totale (sempre del mese di gennaio 2005)
4. I titoli dei film che non sono mai stati proiettati a Pisa
5. I titoli dei film che sono stati proiettati solo a Pisa
6. Il nome degli attori italiani che non hanno mai recitato in film di Fellini.
7. Gli attori che prima del 1960 hanno recitato solo nei film di Fellini.
8. Per ogni regista e ogni attore, il numero di film del regista con l’attore.
9. Il numero di film recitato da ogni attore italiano in film di Fellini, indicando anche il suo nome, anno di nascita e nazionalità.
10. Scrivere il codice sql per un trigger che, all’inserimento di una proiezione, se l’incasso è inferiore ai 200 euro, inserisca il codice del film, il codice della sala e l’incasso in una tabella di audit

FLOP(codiceFilm, sala, incasso)

