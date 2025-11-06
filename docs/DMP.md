# Roma Sotterranea - Data Management Plan

| Versione | Data       |
| -------- | ---------- |
| v1.2   | 06-11-2025 |

## Indice

- [Autore](##Autore)
- [Sommario esecutivo](##Sommarioesecutivo)
- [Introduzione](##Introduzione)
- [Descrizione dei dati](##Descrizionedeidati)
- [Documentazione e qualità dei dati](##Documentazioneequalitàdeidati)
- [Licenza](##Licenza)

## Autore

- Gianluca Petrosillo -- https://orcid.org/0009-0002-2249-1894 -- ALMA MATER UNIVERSITÀ DI BOLOGNA -- STUDENTE

## Sommario esecutivo

1. Scelta dei brani dall'opera di Diego Angeli [Diego Angeli, Le Chiese di Roma, Roma, Società Editrice Dante Alighieri, 1922.](https://archive.org/details/lechiesediromagu00ange_0/page/n7/mode/2up)
2. Dai testi scelti in formato ```.txt```, estrazione manuale dei dati 
4. Creazione della prima tabella in formato  ```.csv``` contenente tutte le chiese in cui esiste una sezione ipogea, tramite [GitHub](https://github.com/)
6. Applicazione di [Open Refine](https://openrefine.org/) per riconciliare le authority di nomi delle chiese 
7. Sulla base dell'ultima tabella ```.csv```, marcatura seguendo [XML TEI](https://vscode.dev/)
8. Raccolta dei dati e loro organizzazione in seconda tabella  ```.csv``` con le informazioni sulle opere d'arte presenti nei sotterranei delle chiese descritte da Diego Angeli, di nuovo attraverso [GitHub](https://github.com/)
9. Applicazione di [Open Refine](https://openrefine.org/) per riconciliare le authority dei nomi degli autori e correggere possibili errori
10. Analisi dei risultati

## Introduzione

È possibile mappare i sotterranei di Roma e il loro contenuto a partire da una guida turistica delle chiese capitoline? L'obiettivo di questa ricerca è proprio questo: rintracciare e rappresentare schematicamente gli ipogei nascosti sotto basiliche, monasteri, ed altri edifici religiosi romani.
Per riuscirci, il punto di partenza sarà l'analisi e la marcatura di un testo: [Diego Angeli, Le Chiese di Roma, Roma, Società Editrice Dante Alighieri, 1922.](https://archive.org/details/lechiesediromagu00ange_0/page/n7/mode/2up) di Diego Angeli. Da esso, mediante una banale ricerca per parole, saranno individuate le chiese dotate di sotterranei, catacombe, parti interrate, permettendoci di costruire un primo file in CSV per averne una visione schematica. Dopodiché, si procederà alla trasformazione del testo selezionato (in formato .txt) in una versione dello stesso marcata in TEI, adoperando tag che permettano l'estrazione delle opere d'arte contenute all'interno delle sezioni ipogee dei luoghi di culto romani.
Infine, sarà stilata una nuova tabella CSV nella quale saranno riportate tutte le opere d'arte sovracitate, associate a tutti i dettagli che sarà stato possibile reperire dal testo di Angeli.
Da quest'ultimo file dovrebbe essere possibile, poi, svolgere ulteriori azioni, come la creazione di LOD in RDF che permettano di associare mediante URI tutte le opere al loro autore, alla loro posizione nel sottosuolo romano, al loro soggetto, al tipo di opera d'arte, ecc.
Roma_Sotterranea è il titolo del progetto d’esame per il corso di [DHDM](https://www.unibo.it/it/studiare/insegnamenti-competenze-trasversali-moocs/insegnamenti/insegnamento/2024/502386) (a.a. 2024/2025).

## Descrizione dei dati

![image](https://github.com/user-attachments/assets/b0b8f115-f4aa-44b0-927f-19f16f7aea75)

I dati sono stati raccolti a partire dalla versione formato ```.txt``` dell'opera di Diego Angeli. A partire da esso sono stati identificati diversi elementi: 

- nome_chiesa
- altri_nomi
- posizione
- data_costruzione
- data_riedificazione_restauro
- responsabili_elementi_architettonici_interni
- elementi_scultorei_interni
- responsabili_elementi_scultorei_interni
- elementi_pittorici_destra
- responsabili_elementi_pittorici_destra
- elementi_pittorici_sinistra
- responsabili_elementi_ pittorici_sinistra

A partire da una strutturazione preliminare dei dati in formato tabellare (Excel), si è proceduto con la conversione in formato ```.csv``` e, attraverso l'impiego di Open Refine, è stato effettuato il controllo authority relative al campo _nome_chiesa_.   
Completata la fase di pulizia e verifica, il nuovo obiettivo è la marcatura dei testi selezionati secondo lo standard XML-TEI, utilizzando come riferimento i dati estratti e strutturati nel file ```.csv```. 

Tuttavia, il risultato ottenuto presenta una marcata disomogeneità e una scarsa coerenza tra le entità descritte nel file ```.csv``` e la loro rappresentazione nella codifica XML-TEI, con particolare riferimento agli elementi di natura scultorea e pittorica. Ciò compromette l'affidabilità e l'interoperabilità del dataset all'interno di un contesto di valorizzazione e analisi digitale del patrimonio.

In ultima analisi, _Quer pasticciaccio_ ha permesso alcune riflessioni e spunti di lavoro futuro: 

1. basare la marcatura su un thesaurus consolidato e specifico come l'Art and Architecture Thesaurus curato da [Getty Research Institute](https://www.getty.edu/research/tools/vocabularies/aat/)
2. procedere con l'estrazione e la strutturazione dei dati in ```.csv```
3. completare il processo con la riconciliazione delle authority tramite Open Refine.

Solo seguendo questo percorso sistematico si potrà ottenere un dataset affidabile, coerente e interoperabile, capace di valorizzare adeguatamente il patrimonio culturale analizzato e di supportare future ricerche digitali in ambito storico-artistico.

- Quali dati (ad esempio il tipo, i formati e i volumi)  
verranno raccolti o prodotti?
- Come verranno raccolti o prodotti i nuovi dati e/o  
come verranno riutilizzati i dati esistenti?

## Documentazione e qualità dei dati

- Quali metadati e documentazione (ad esempio la metodologia  
di raccolta dei dati e il modo di organizzare i dati)  
accompagneranno i dati?
- Quali misure di controllo della qualità dei dati saranno  
utilizzate?

## Backup e archiviazione

- Come saranno archiviati e salvati i dati e i metadati  
durante la ricerca?
- Come sarà gestita la sicurezza dei dati e la protezione  
dei dati sensibili durante la ricerca?

## Requisiti legali ed etici

- Come saranno gestite altre questioni legali, come i diritti  
di proprietà intellettuale e la proprietà? Quale legislazione  
si applica?
- Quali questioni etiche e codici di condotta ci sono e come  
saranno presi in considerazione?

## Condivisione dei dati e conservazione a lungo termine

- Come e quando i dati saranno condivisi? Ci sono possibili  
restrizioni alla condivisione dei dati o motivi di embargo?
- Come saranno selezionati i dati per la conservazione e dove  
saranno conservati a lungo termine (ad esempio un repository  
di dati o un archivio)?
- Quali metodi o strumenti software sono necessari per accedere  
e utilizzare i dati?
- Come sarà garantita l'applicazione di un identificatore unico  
e persistente (come un Digital Object Identifier, o DOI) a  
ciascun set di dati?
