STUDENTI(Matricola, Nome, Cognome, DataNascita, Indirizzo, Telefono, Cod_CorsodiLaurea)

DOCENTI(Codice_Docente, Nome, Cognome)

CORSO_DI_LAUREA(Codice_CdL, Nome, Cod_Fac)

INSEGNAMENTO(Codice_Insegnamento, Nome, Cod_Docente)

ESAMI(MatrStud, Voto, Data, Lode, Cod_Ins)

FACOLTA(Codice_Fac, Nome, Indirizzo_Sede, N_Telefonico)

Scrivere le query SQL per trovare:

1. Gli insegnamenti tenuti dal docente Gianni Somma che insegna Teoria della Probabilità e non dal docente Gianni Somma che insegna Diritto Romano.
2. L'elenco dei docenti e il numero degli esami superati nei rispettivi corsi, in ordine decrescente (di numero di corsi). 
3. La facoltà presso la quale nel 2002 è stato sostenuto il massimo numero di esami.
4. Gli insegnamenti tenuti dal docente Gianni Somma che insegna Teoria della Probabilità e non dal docente Gianni Somma che insegna Diritto Romano.

```sql
select I.Nome
from INSEGNAMENTO I join DOCENTI on Cod_Docente=Codice_Docente
where Codice_Docente = any (select Codice_Docente
from INSEGNAMENTO join DOCENTI on Cod_Docente=Codice_Docente
where INSEGNAMENTO.Nome=Teoria delle Probabilità 
and DOCENTI.Nome=Gianni 
and DOCENTI.Cognome=Somma)
```

5. L'elenco dei docenti e il numero degli esami superati nei rispettivi corsi, in ordine decrescente (di numero di esami). 

```sql
select D.Nome, D.Cognome, I.Nome, count(*) as N_Esami
from INSEGNAMENTO I join DOCENTI on Cod_Docente=Codice_Docente
join ESAMI E on Cod_Ins=Codice_Insegnamento
group by D.Nome, D.Cognome, I.Nome
order by N_Esami desc
```


6. La facoltà presso la quale nel 2002 è stato sostenuto il massimo numero di esami.

```sql
select FACOLTA.Nome, count(*) as N_Esami
from ESAMI, STUDENTI, FACOLTA, CORSO_DI_LAUREA
where MatrStud=Matricola 
and     
Cod_CorsodiLaurea=Codice_CdL 
and     
Cod_Fac=Codice_Fac
group by FACOLTA.Nome
having N_Esami >= all (select count(*)
from    
ESAMI, STUDENTI, 
FACOLTA, CORSO_DI_LAUREA
where MatrStud=Matricola  
and 
Cod_CorsodiLaurea=C.Codice_CdL 
and 
Cod_Fac=Codice_Fac
group by FACOLTA.Nome)
```

7. Il docente col quale è stato sostenuto il maggior numero di esami.
8. Il nome delle diverse facoltà ed il numero di iscritti a ciascuna di esse, in ordine decrescente. 
9. La media dei voti ottenuti negli esami sostenuti dagli iscritti a Scienze Politiche.
10. Lesame di Ingegneria Informatica sostenuto dal massimo numero di studenti nel 2001.
11. Quanti esami ha sostenuto ogni studente nel 2002. 
12. L'elenco dei corsi di laurea e, per ciascuno, il numero di docenti che insegnano i relativi corsi.
13. Lo studente di Ingegneria che ha sostenuto il massimo numero di esami.
14. L'elenco delle diverse Facolta' e il numero di corsi di laurea che esse offrono, in ordine decrescente di numero di corsi. 
15. L'elenco alfabetico degli iscritti alla Facolta' di Scienze che hanno sostenuto almeno 3 esami e la media dei voti che hanno ottenuto in tali esami.
16. Il corso di Laurea di Lettere col massimo numero di studenti iscritti
17. Quanti esami ha sostenuto ogni studente nel 2001 e la facolta' a cui e' iscritto 
18. L'elenco degli studenti del Prof. Pallini che hanno sostenuto almeno un esame relativo ai suoi corsi e la media dei voti che hanno ottenuto in tali esami.
19. La facolta' col massimo numero di studenti iscritti
20. Quanti esami con voto maggiore di 25 ha sostenuto ogni studente e il corso di laurea a cui e' iscritto 
21. L'elenco degli insegnamenti e dei docenti del corso di laurea in Ingegneria Informatica, e il numero di studenti che hanno sostenuto l'esame per ciascun corso. 
22. Il nome e il cognome del docente della facoltà di Ingegneria titolare del maggior numero di insegnamenti.        
23. Quanti insegnamenti prevede il corso di laurea in Ingegneria delle Telecomunicazioni.

