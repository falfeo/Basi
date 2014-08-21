La Base di Dati di un’agenzia che organizza banchetti contiene le seguenti informazioni:

1. Anagrafica persone, contenente i dati delle  persone che si rivolgono all’agenzia per organizzare un banchetto e i dati delle persone invitate al banchetto.
2. Informazioni sui banchetti organizzati in occasione di particolari eventi (congressi, matrimoni,…) per conto dei clienti.
3. Gli elenchi degli invitati ai singoli banchetti.
4. Un elenco di ristoranti, tra cui ci sono anche ristoranti caratteristici che sono gli unici ad offrire particolari specialità.
5. Un elenco delle portate tra cui si distinguono le specialità.
6. Un insieme di menu con l’elenco delle portate di cui sono composti.
7. La descrizione degli ingredienti di cui una portata è composta.

RISTORANTE(NomeRist, Località, Indirizzo, Telefono, #Posti)

RISTORANTE_OFFRE_MENU(NomeRist, Località, IdMenu)

MENU(IdMenu, NomePortata)

PREZZO(IdMenu, Costo)

PORTATA(NomePortata, Prezzo, Tipo, Specialità)

INGREDIENTE(NomeIngrediente, Tipo)

INGREDIENTI_IN_PORTATA(NomePortata, NomeIngrediente,Quantità)

BANCHETTO(Codice, Occasione, Data, #Partecipanti, CodFiscCliente,NomeRistorante, Località, IdMenu)

INVITATO(CodiceBanchetto, CodFiscInvitato)

PERSONA(CodiceFiscale, Nome, Cognome, DataNascita, Indirizzo, Telefono, Professione)

Creare una vista che contenga tutti gli ingredienti e le quantità delle specialità

```sql
CREATE VIEW Ingredienti_Specialità(NomePortata, NomeIngrediente, Quantità) AS
SELECT Portata.NomePortata, Ingredienti_In_Portata.NomeIngrediente,Ingredienti_In_Portata.Quantità
FROM Ingredienti_In_Portata, Portata
WHERE Ingredienti_In_Portata.NomePortata = Portata.NomePortata
AND Portata.Specialità = "Sì"
```

Creare una vista che contenga nome e località di tutti i ristoranti caratteristici (ristoranti che offrono specialità)

```sql
CREATE VIEW RistorantiCaratteristici(NomeRist, Località) AS
SELECT DISTINCT Ristorante_Offre_Menu.NomeRist,
Ristorante_Offre_Menu.Località
FROM Ristorante_Offre_Menu, Menu, Portata
WHERE Ristorante_Offre_Menu.IdMenu = Menu.IdMenu
AND Menu.NomePortata = Portata.NomePortata
AND Portata.Specialità = "Sì"
```
Creare una vista che contenga tutti i secondi piatti che stanno in menù da 30 euro (indicare anche il menù di cui fanno parte e se sono o meno specialità)

```sql
CREATE VIEW SecondiPiatti(NomePortata, Specialità, IdMenu) AS
SELECT Portata.NomePortata, Portata.Specialità, Menu.IdMenu
FROM Portata, Prezzo, Menu
WHERE Portata.NomePortata = Menu.NomePortata
AND Menu.IdMenu = Prezzo.IdMenu
AND Portata.Tipo = “Secondo”
AND Prezzo.Costo = 30
```

Creare un trigger tale che, ogni volta che si vuole inserire nel database un banchetto con un numero di persone maggiore del numerodei posti del ristorante, sollevi un’eccezione d’errore.
