Prova Scritta dell’Esame di Laboratorio di Basi di Dati 21 Aprile 2009



AUTO (Targa, Marca, Cilindrata, Potenza, CodF*, CodAss*)

PROPRIETARI (CodF, Nome, Residenza)

ASSICURAZIONI (CodAss, Nome, Sede)

SINISTRO (CodS, Località, Data)

AUTOCOINVOLTE (CodS*, Targa*, ImportoDelDanno)


Scrivere le interrogazioni SQL che restituiscono le seguenti informazioni:

1. Per ciascuna Assicurazione, il nome, la sede ed il numero di auto assicurate
2. Le coppie di auto coinvolte negli stessi sinistri.
3. Per ciascuna auto coinvolta in più di un sinistro, la targa dell’auto, il nome dell’ Assicurazione ed il totale dei danni riportati.
4. CodF e Nome di coloro che possiedono più di un’auto
5. La targa delle auto che non sono state coinvolte in sinistri dopo il 20/01/01
6. Il codice dei sinistri in cui non sono state coinvolte auto con cilindrata inferiore a 2000 cc
7. Supponiamo che esista una tabella NumeroIncidenti(Targa, Numero) che contenga per ogni macchina il numero di incidenti in cui è stata coinvolta, se ha mai fatto degli incidenti. Scrivere un trigger tale che, ogni volta che si inserisce una riga nella tabella AUTOCOINVOLTE, aggiorni la tabella 
