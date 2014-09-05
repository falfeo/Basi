Prova scritta dell’esame di Basi di Dati
4 Febbraio 2011

## Carta di credito

Si consideri una BD per gli acquisti con carta di credito che contiene le seguenti informazioni sui clienti (titolari di carte di credito), estratti conto, dettagli degli acquisti, prodotti acquistati, luoghi degli acquisti e promozioni.

Dei clienti interessano il codice fiscale, che li identifica, il nome, il reddito, il sesso, l’anno di nascita, l’indirizzo, il numero e l’anno di scadenza della carta.

I clienti ricevono mensilmente un estratto conto del quale interessano il numero, che lo identifica, la data, il totale delle spese addebitato e, per ogni acquisto, la data, l’importo, il luogo (città, provincia e regione), la descrizione e la categoria del prodotto (supermercato, ristorante, auto, viaggi, varie).

Con l'estratto conto vengono segnalate al cliente diverse promozioni di acquisti delle quali interessano il codice, che le identifica, la descrizione, il costo, le date di inizio e fine della promozione. 

## Algebra Relazionale e SQL

Si consideri il seguente schema, che descrive la realtà di una banca, organizzata su più filiali ed agenzie, con i suoi dipendenti ed i suoi clienti (in GRASSETTO le chiavi primarie):

CLIENTI(CodiceFiscale,Cognome,Nome,DataNascita,LuogoNascita,Indirizzo) alias CL

DIPENDENTI(CodiceFiscale,DataAssunz.,CodiceFiliale,Numero,AnzianitàLivello) alias DI

LIVELLI(Numero,StipendioIniziale,ScattoAnnuale) alias LI

FILIALI(CodiceFiliale,Città,Direttore) alias FI

AGENZIE(CodiceFiliale,NumeroAgenzia,Indirizzo,Reggente)

CONTICORRENTI(CodiceFiliale,NumeroAgenzia,NumeroConto,Titolare,Saldo) alias CO

In Dipendenti, Numero è un riferimento esterno alla chiave della relazione LIVELLI
In Dipendenti, CodiceFiliale è un riferimento esterno alla chiave della relazione FILIALI
In Filiali, Direttore è un riferimento esterno alla chiave della relazione DIPENDENTI
In Agenzie, Reggente è un riferimento esterno alla chiave della relazione DIPENDENTI alias AG
In Conticorrenti, Titolare è un riferimento esterno alla chiave della relazione CLIENTI

Si scrivano espressioni di algebra relazionale ed in SQL che traducano le seguenti interrogazioni:

1. elencare il nome ed il cognome dei clienti il cui saldo è negativo in almeno un conto corrente
2. elencare i dipendenti che sono clienti della banca e che hanno il conto in una filiale che non è quella in cui lavorano.
3. Elencare le filiali nelle quali i dipendenti hanno tutti (incluso il direttore) un'anzianità nel rispettivo livello inferiore a tre anni.
4. Elencare per ogni filiale il dipendente con anzianità massima, purché non sia né direttore della filiale, né reggente di un'agenzia.

Scrivere in SQL la seguente interrogazione

e) I Clienti che hanno il massimo numero di conti correnti.
