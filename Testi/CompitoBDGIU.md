Dato il seguente schema relazionale:

Regista(Nome, DataNascita, Nazionalita)

Film(Titolo, NomeRegista, Anno)

Proiezione(Nomecinema, Nomefilm, Citta`)

scrivere in SQL le interrogazioni seguenti:

Selezionare le Nazionalità dei registi che hanno diretto dei film nel 1992 ma non hanno diretto film nel 1993.

Individuare i nomi dei registi che hanno girato nel 1993 più film di quanti ne avevano girati nel 1992.

Individuare le date di nascita dei registi che hanno diretto film che sono stati proiettati sia a Torino che a Milano.

Dato il seguente schema relazionale:

AUTORE(Nome, Cognome, Data-N, Nazionalita)

AUTORELIBRO(Nome, Cognome, Segnatura)

LIBRO(Segnatura, Scaffale, Argomento, Lingua)

Scrivere in SQL l'interrogazione seguente:

Selezionare il cognome degli autori tedeschi di libri in italiano con Argomento "filosofia" o "logica".

Selezionare la data di nascita degli autori italiani di libri in inglese di Argomento "informatica", che non sono autori di libri di Argomento "matematica".

Selezionare gli autori (selezionati in base al loro Nome e Cognome) che hanno più di 10 libri diversi contenuti nel terzo scaffale della biblioteca.

Dato il seguente schema relazionale che descrive il calendario di una manifestazione sportiva a squadre nazionali:

STADIO(NUMERO,Citta,Capienza)

INCONTRO(NUM-STADIO,Squadra1,Squadra2,DATA,ORA)

NAZIONALE(PAESE,Continente,Categoria)

Esprimere in SQL le seguenti interrogazioni:

Estrarre i numeri degli stadi in cui non gioca nessuna nazionale europea.

Estrarre la capienza complessiva degli stadi in cui si giocano le partite che hanno come prima squadra una nazione sudamericana (nota: ai fini della valutazione della capienza complessiva, si sommino le capienze associate a ciascuna gara, anche se più gare si svolgono nello stesso stadio).

Estrarre la città in cui si trova lo stadio in cui la squadra italiana gioca più partite.
