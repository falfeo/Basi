Prova scritta dell’esame di Laboratorio di Basi di Dati 15 Giugno 2009

ROMANZI(CodiceR, Titolo, NomeAut*, Anno)

PERSONAGGI(NomeP, CodiceR*, sesso, ruolo)

AUTORI(NomeAut, AnnoN, AnnoM:optional, Nazione)

FILM(CodiceF, Titolo, Regista, Produttore, Anno, CodiceR*)

Scrivere le interrogazioni SQL che restituiscono le seguenti informazioni:

1. I personaggi principali (ruolo =”P”) dei romanzi di autori viventi.
2. I nomi dei personaggi che compaiono in più di un romanzo, ed il numero dei romanzi nei quali compaiono
3. I romanzi di autori italiani dai quali è stato tratto più di un film
4. Il titolo dei romanzi dai quali non è stato tratto nessun film
5. Il titolo dei romanzi i cui personaggi principali sono tutti femminili.
6. Scrivere una vista contenente tutti i nomi di tutti gli autori presenti nel database, dai cui romanzi è stato girato un film sotto la regia di Fellini.
7. Scrivere un trigger tale che, ogni volta che viene cancellato un titolo dalla tabella ROMANZI, viene cancellato il film tratto da esso dalla tabella FILM
