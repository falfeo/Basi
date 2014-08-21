Prova scritta per l’esame di Laboratorio di Basi di dati 2 Marzo 2009

SCHEMA RELAZIONALE:

MUSEI (NomeM, Città)

ARTISTI (NomeA, Nazionalità)

OPERE (Codice, Titolo, NomeM*, NomeA*)

PERSONAGGI (Personaggio, Codice*)

1. Il nome dei musei di Londra che non conservano opere di Tiziano
2. Il nome dei musei di Londra che conservano solo opere di Tiziano
3. I musei che conservano almeno 20 opere di artisti italiani
4. Il museo che ha la più grande collezione di opere italiane
5. Una vista contenente gli artisti che hanno raffigurato San Francesco in almeno una delle loro opere
6. Scrivere un trigger che per ogni nuova opera acquisita, prima che venga inserita nella tabella opere, verifichi se l’artista è presente nella tabella artisti, e in caso contrario inserisce nella tabella artisti una riga contenente il nome dell’artista e, momentaneamente, indica una nazionalità sconosciuta.
