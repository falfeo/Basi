Prova scritta per lesame di Laboratorio di Basi di Dati 30 Gennaio 2008

E data la seguente base di dati, in cui gli attributi chiave primaria di ogni tabella sono sottolineati, e i vincoli intrarelazionali possono essere dedotti in maniera ovvia dallo studente.

STUDENTI(Matricola, Nome, Cognome, DataNascita, Indirizzo, Telefono, Cod_CorsodiLaurea)

DOCENTI(Codice_Docente, Nome, Cognome)

CORSO_DI_LAUREA(Codice_CdL, Nome, Cod_Fac)

INSEGNAMENTO(Codice_Insegnamento, Nome, Cod_Docente)

ESAMI(MatrStud, Voto, Data, Lode, Cod_Ins)

FACOLTA(Codice_Fac, Nome, Indirizzo_Sede, N_Telefonico)

Si risolvano le seguenti select SQL

1. La matricola, il nome e il cognome degli studenti che hanno superato con lode lesame di Urbanistica insegnato dal Prof. Giovanni Bianchi.

2. Lelenco degli studenti del professor Marco Bruni che hanno sostenuto almeno un esame dei suoi corsi. 

3. Il nome del corso di Laurea (o i corsi di laurea) di Lettere col massimo numero di studenti iscritti.

4. Quanti esami ha sostenuto ogni studente nel 2001, indicandone anche matricola, nome, cognome e la facoltà a cui è iscritto.

5. Il nome della Facoltà col massimo numero di studenti iscritti

6. Gli studenti che hanno sostenuto sia lesame di Economia politica 1 che quello di Economia Politica 2.

7. Scrivere un trigger tale che ogni volta che viene cancellato un insegnamento, verifichi se il professore titolare di quellinsegnamento è titolare di almeno un altro insegnamento. In caso negativo inserisca matricola, nome, cognome di questo docente e il nome dellinsegnamento cancellato in una tabella definita come segue  DOCENTI_DISOCCUPATI (Matricola, Nome, Cognome, vecchio_Insegnamento).

8. Supponiamo che nel database sia presente una tabella  PROPEDEUTICITA (codice_ins, codice_prop) in cui sono indicate nella seconda colonna tutte le propedeuticità dellinsegnamento il cui codice è indicato nella prima colonna. Si crei un trigger tale che, ogni volta che si vuole inserire un esame nella tabella ESAMI, verifichi se tutte le materie propedeutiche a quellesame sono state sostenute da quello studente, e in caso contrario impedisca linserimento sollevando uneccezione. (Suggerimento: Fare uso di un cursore)

9. Scrivere una procedura per limmatricolazione di un nuovo studente, il cui numero di matricola viene assegnato automaticamente in maniera progressiva.

10.  Scrivere una funzione che, preso in input un codice di insegnamento e una data, restituisca la media dei voti conseguiti dagli studenti in quella materia a partire da quella data.
