Considerare la seguente base di dati:

Fornitori (CodiceFornitore, Nome, Indirizzo, Città)

Prodotti (CodiceProdotto, Nome, Marca, Modello)

Catalogo (CodiceFornitore, CodiceProdotto, Costo)

Dopo aver costruito le tabelle corrispondenti mediante opportuni comandi DDL e avere imposto gli opportuni vincoli intrarelazionali e interrelazionali, formulare in SQL una interrogazione per ciascuno dei seguenti punti:

1. Costruire l’elenco dei prodotti venduti, visualizzando Codice e Costo del prodotto e Nome del fornitore presso cui è venduto, e ordinarlo in ordine crescente rispetto al codice e al costo del prodotto (prima rispetto al codice poi al costo).

2. Trovare il costo del prodotto più caro venduto a Milano.

3. Trovare il costo medio dei prodotti forniti in ciascuna città (visualizzare costo e città)

4. Per ogni città, trovare il numero delle offerte, ovvero il numero dei beni venduti in ogni città.

5. Trovare il codice del prodotto più costoso tra quelli distribuiti dai fornitori presenti a Roma.

6. Trovare presso quali fornitori conviene comprare i singoli prodotti (chi vende a meno un determinato prodotto?); mostrare: Nome del fornitore, Codice e Costo del prodotto.

7. Trovare i codici di tutti i prodotti che sono forniti da almeno due fornitori.

8. Creare una vista contenente i nomi e il costo medio di tutti i prodotti.

9. Creare una nuova tabella audit_prezzi che serve a registrare ogni modifica dei prezzi dei prodotti. La sua struttura sarà la seguente:

AUDIT_PREZZI (CodFornitore, CodProdotto, Aumento,Data)

Creare un trigger che ad ogni aumento del prezzo di un prodotto da parte di un fornitore, se questo aumento è superiore al 15%, impedisca l’inserimento sollevando un’eccezione, altrimenti inserisca il codice del fornitore, il codice del prodotto, l’aumento del prezzo, e la data in cui la modifica viene effettuata.
