STUDENTE(Matricola, Nome, Cognome, Indirizzo, Città, CAP,M/F)

INSEGNANTE(Matricola, Nome, Cognome, Città,Telefono, Stipendio)

CORSO(Codice, Nome, Facoltà, NumeroCrediti)

ESAME(CodiceCorso, MatricolaStudente, Voto)

INSEGNAMENTO(CodiceCorso, MatricolaProfessore, NumeroStudenti, Anno)

1. Elencare in ordine alfabetico gli insegnanti con il relativo stipendio convertito in lire (supponendo sia in euro, 1 euro=1936,27 lire), e il cui stipendio è superiore a 2000 euro.
2. Trovare la somma degli stipendi dei professori che guadagnano più di 2000 euro
3. Trovare la matricola degli studenti che hanno preso un 30 e un 30 e lode
4. Elencare il voto medio e il numero di esami sostenuti da ogni studente con voto medio superiore a 25
5. Elencare in ordine alfabetico il nome dei professori, e la somma dei crediti dei corsi che essi insegnano.
6. Indicare quali studenti hanno superato tutti gli esami di primo anno.
7. Determinare quali studenti hanno almeno un  voto maggiore o uguale alla media dei voti più alta in assoluto. Elencare nome degli studenti e relativo voto. Per fare ciò creare una vista che contiene, per ogni studente, la media dei suoi voti.
8. Ogni professore deve insegnare almeno 12 crediti. Creare un trigger che verifica che, ogni volta che un insegnante viene sostituito in un insegnamento, l’insegnante che è stato sostituito continui ad insegnare  almeno 12 crediti.
9. Creare un trigger tale che, ogni volta che ad un insegnante viene attribuito un nuovo corso, verifica se supera i 12 crediti, e nel qual caso aumenti il suo stipendio di 100 euro per ogni credito oltre i 12 istituzionali.
10. Supponiamo che esista un sistema di propedeuticità per cui uno studente non può sostenere nessun esame di un anno se non ha sostenuto gli esami dell’anno precedente. Supponiamo che si tratti di un corso di laurea triennale. Creare un trigger che verifica le propedeuticità, ossia impedisce di registrare un esame se non sono stati sostenuti tutti gli esami propedeutici.
