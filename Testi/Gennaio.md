Esercizi di SQL

Dato il seguente schema relazionale scrivere le interrogazioni specificate di seguito in SQL.

Prodotti(codice, nome, prezzo, descrizione, categoria)

Categorie(id, nome, descrizione)

Negozi(id, nome, indirizzo, telefono)

Offerte(negozio, prodotto, dataInizio, datatine, descrizione)

Disponibilità(negozio, prodotto, num_pezzi)


1. Trovare, per ogni prodotto, il numero di offerte in cui è compare.
2. Trovare nome e disponibilità (num_pezzi) dei prodotti in offerta nel negozio di nome Roncadelle (sia la disponibilità che le offerte sono riferite al negozio Roncadelle).
3. Trovare, per ciascun negozio, il numero di offerte iniziate nel marzo 2007.
4. Trovare nome e numero di pezzi totale (cioè in tutti i negozi) dei prodotti della categoria "Ufficio".
5. Trovare nome, descrizione e disponibilità dei prodotti che iniziano per N nel negozio di nome Roncadelle.
6. Trovare nome e categoria dei prodotti più cari aventi un nome di quattro lettere.
7. Trovare il nome dei prodotti con disponibilità massima nei negozi di Milano (cioè nei negozi in cui la parola "Milano" compare nell'indirizzo) in ordine alfabetico.
8. Trovare il nome dei prodotti che non sono mai stati messi in offerta nei negozi di Milano (cioè nei negozi in cui la parola "Milano" compare nell'indirizzo).

## Possibili soluzioni

1)

```sql
SELECT nome, COUNT(*) AS num_offerte
FROM Prodotti INNER JOIN Offerte ON Prodotti.codice=Offerte.prodotto
GROUP BY Prodotto.codice, Prodotto.nome
```
2)

```sql
SELECT Prodotti.nome, Disponibilità.num_pezzi
FROM (Prodotti INNER JOIN Disponibilità ON Disponibilità.prodotto=Prodotti.codice)
INNER JOIN Negozi ON Disponibilità.negozio=Negozi.id
WHERE Negozi.nome=’Roncadelle’ AND Prodotti.codice IN
(SELECT Offerte.prodotto
FROM Offerte INNER JOIN Negozi ON Offerte.negozio=Negozi.id
WHERE Negozi.nome=’Roncadelle’)
```
3)

```sql
SELECT Negozi.nome, COUNT(*) AS num_offerte
FROM Negozi INNER JOIN Offerte ON Offerte.negozio=Negozi.id
WHERE Offerte.dataInizio BETWEEN ‘2007-03-01’ AND ‘2007-03-31’
GROUP BY Negozi.nome, Negozi.id
```
4)

```sql
SELECT Prodotti.nome, SUM(Disponibilità.num_pezzi) AS totale
FROM (Prodotti INNER JOIN Disponibilità ON Prodotti.codice=Disponibilità.prodotto)
INNER JOIN Categorie ON Categorie.id=Prodotti.categoria
WHERE categorie.nome=’Ufficio’
GROUP BY Prodotti.id, Prodotti.nome
```
5)

```sql
SELECT Prodotti.nome, Prodotti.descrizione, Disponibilità.num_pezzi
FROM (Prodotti INNER JOIN Disponibilità ON Prodotti.codice=Disponibilità.prodotto)
INNER JOIN Negozi ON Disponibilità.negozio=Negozi.id
WHERE Negozi.nome=’Roncadelle’ AND Prodotti.nome LIKE ‘N%’
```
6)

```sql
SELECT Prodotti.nome, Categorie.nome AS nome_categoria
FROM Prodotti INNER JOIN Categorie ON Prodotti.categoria=Categorie.id
WHERE Prodotti.nome LIKE ‘_ _ _ _’ 
AND Prodotti.prezzo  =  (SELECT MAX(prezzo) 
FROM Prodotti 
WHERE Prodotti.nome LIKE ‘_ _ _ _’)
```
7)

```sql
SELECT Prodotti.nome
FROM (Prodotti INNER JOIN Disponibilità ON Prodotti.codice=Disponibilità.prodotto) 
INNER JOIN Negozi ON Negozi.id=Disponibilità.negozio
WHERE Negozi.indirizzo LIKE ‘%Milano%’ AND 
num_pezzi  =    (SELECT MAX(num_pezzi) 
FROM Disponibilità INNER JOIN Negozi 
ON Disponibilità.negozio=Negozi.id 
WHERE Negozi.indirizzo LIKE ‘%Milano%’)
ORDER BY Prodotti.nome
```
8)

```sql
SELECT nome
FROM Prodotti
WHERE codice NOT IN (SELECT Offerte.prodotto
FROM Offerte INNER JOIN Negozi 
ON Offerte.negozio = Negozi.id
WHERE Negozio.indirizzo LIKE ‘%Milano%’)
```
