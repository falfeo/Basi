Prova scritta per l’esame di Laboratorio di Basi di dati

E’ data la seguente base di dati:

STUDENTE (Matricola, Nome, Cognome, Indirizzo, Città, CAP,Sesso)

INSEGNANTE (Matricola, Nome, Cognome, Città,Telefono, Stipendio)

CORSO (Codice, Nome, Facoltà, NumeroCrediti)

ESAME (CodiceCorso, MatricolaStudente, Voto)

INSEGNAMENTO (CodiceCorso, MatricolaProfessore, NumeroStudenti)

1. Elencare in ordine alfabetico il nome dei professori, il nome ed il codice dei corsi che essi insegnano

```sql
SELECT Insegnante.Cognome, Insegnante.Nome, Insegnamento.CodiceCorso, Corso.Nome
FROM Insegnante, Corso, Insegnamento
WHERE Insegnante.Matricola=Insegnamento.MatricolaProfessore AND
    Insegnamento.CodiceCorso=Corso.Codice
GROUP BY Insegnante.Matricola
ORDER BY Insegnante.Cognome, Insegnante.Nome
```

2. Quali studenti hanno ricevuto 30 in qualche esame?

```sql
SELECT Nome, Cognome,
FROM Studente
WHERE Matricola IN (SELECT MatricolaStudente
    FROM Esame
    WHERE Voto=30)
```

3. Quali professori guadagnano meno della media?


```sql
SELECT Nome, Cognome,
FROM Insegnante
WHERE Stipendio < (SELECT AVG(Stipendio) FROM Insegnante)
```

4. Quali studenti hanno il voto medio maggiore del voto medio più basso? Elencare nome e voto medio degli studenti

```sql
CREATE VIEW VotiMedi(Matricola,VotoMedio) AS
SELECT MatricolaStudente, AVG(Voto)
FROM Esame
GROUP BY MatricolaStudente
```

```sql
SELECT Matricola, Nome, Cognome, AVG(Voto)
FROM Studente JOIN Esame ON
Studente.Matricola=Esame.MatricolaStudente
GROUP BY Matricola
HAVING AVG(Voto) > SELECT MIN(VotoMedio) FROM VotiMedi
```

5. Quali studenti non hanno superato alcun esame?

```sql
SELECT Matricola, Nome, Cognome
FROM Studente
WHERE NOT EXISTS (SELECT *
FROM Esame
WHERE
MatricolaStudente=Studente.Matricola)
```

6. Elencare le facoltà che hanno corsi superati da più di 4 studenti

```sql
SELECT Facoltà
FROM Corso
WHERE EXISTS (SELECT COUNT ( *)
FROM Esame
WHERE
CodiceCorso=Corso.Codice
```

7. Trovare tutti le Facoltà che non prevedono il corso di ‘Informatica C’ di 5 crediti

```sql
SELECT Facoltà
FROM Corso
EXCEPT
SELECT Facoltà
FROM Corso
WHERE Nome=‘Informatica C’
AND NumeroCrediti=5
```

8. Quali studenti hanno qualche voto maggiore o uguale al voto medio più alto in assoluto? Elencare nome degli studenti e relativo voto

```sql
CREATE VIEW VotiMedi(Matricola,VotoMedio) AS
SELECT MatricolaStudente, AVG(Voto)
FROM Esame
GROUP BY MatricolaStudente
```
```sql
SELECT Matricola, Nome, Cognome, Voto
FROM Studente JOIN Esame ON
Studente.Matricola=Esame.MatricolaStudente
WHERE Voto >= SELECT MAX(VotoMedio)
FROM VotiMedi
```

9. Quanti studenti e quante studentesse hanno superato l’esame di Basi di Dati?

```sql
SELECT Sesso, Numero=COUNT(Studente.Matricola)
FROM Studente, Esame, Corso
WHERE Corso.Nome=‘Basi di Dati’ ANDCorso.Codice=Esame.CodiceCorso AND
Esame.MatricolaStudente=Studente.Matricola
GROUP BY Sesso
```

10. Scrivere un trigger che alla cancellazione di un corso, verifichi che esso non abbia alcuno studente. In caso contrario, impedisce la cancellazione del corso emettendo un messaggio di errore.
