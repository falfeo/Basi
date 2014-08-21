Prova scritta per lesame di Laboratorio di Basi di Dati 30 Gennaio 2008

E data la seguente base di dati, in cui gli attributi chiave primaria di ogni tabella sono sottolineati, e i vincoli intrarelazionali possono essere dedotti in maniera ovvia dallo studente.

STUDENTI(Matricola, Nome, Cognome, DataNascita, Indirizzo, Telefono, Cod_CorsodiLaurea)

DOCENTI(Codice_Docente, Nome, Cognome)

CORSO_DI_LAUREA(Codice_CdL, Nome, Cod_Fac)

INSEGNAMENTO(Codice_Insegnamento, Nome, Cod_Docente)

ESAMI(MatrStud, Voto, Data, Lode, Cod_Ins)

FACOLTA(Codice_Fac, Nome, Indirizzo_Sede, N_Telefonico)

Si risolvano le seguenti select SQL

1. I nomi e cognomi degli studenti che hanno sostenuto tutti gli insegnamenti tenuti dal Professor Mario Rossi.

2. Il nome della Facoltà e il corrispondente numero di studenti, quando questo numero è superiore a 1000.

3. Le coppie dei nomi degli insegnamenti tenuti da uno stesso docente.

4. Il nome dellesame superato dal più grande numero di studenti presso il corso di Laurea in Geologia.

5. L'esame per il quale si è avuta la media dei voti più alta nellanno 2005.

6. Gli insegnamenti i cui esami sono stati sostenuti da almeno uno studente della facoltà di Scienze e da almeno uno studente della facoltà di Ingegneria.

7. Scrivere una procedura che inserisca in una tabella StudentiCritici gli studenti che non sostengono esami da più di un anno.

8. Scrivere un trigger che nel momento in cui si vuole attribuire a un docente un nuovo insegnamento, questa attribuzione venga impedita, sollevando uneccezione, se il docente tiene dei corsi in un corso di laurea di una facoltà diversa.

9. Scrivere una procedura per linserimento di un nuovo insegnamento nella tabella insegnamento, il cui codice è generato in maniera sequenziale.

10. Scrivere una funzione che restituisca il numero medio per facoltà di tutti gli studenti delluniversità.
