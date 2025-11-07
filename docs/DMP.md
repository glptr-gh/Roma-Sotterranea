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

Gianluca Petrosillo -- https://orcid.org/0009-0002-2249-1894 -- ALMA MATER UNIVERSITÀ DI BOLOGNA -- STUDENTE

## Sommario esecutivo

1. Scelta dei brani dall'opera di Diego Angeli [Diego Angeli, Le Chiese di Roma, Roma, Società Editrice Dante Alighieri, 1922.](https://archive.org/details/lechiesediromagu00ange_0/page/n7/mode/2up)
2. Dai testi scelti in formato ```.txt```, estrazione manuale dei dati 
3. Creazione della prima tabella in formato  ```.csv``` contenente tutte le chiese in cui esiste una sezione ipogea, tramite [GitHub](https://github.com/)
4. Sulla base dell'ultima tabella ```.csv```, marcatura seguendo [XML TEI](https://vscode.dev/)
5. Raccolta dei dati e loro organizzazione in seconda tabella  ```.csv``` con le informazioni sulle opere d'arte presenti nei sotterranei delle chiese descritte da Diego Angeli, di nuovo attraverso [GitHub](https://github.com/)
6. Analisi dei risultati

## Introduzione

È possibile mappare i sotterranei di Roma e il loro contenuto a partire da una guida turistica delle chiese capitoline? L'obiettivo di questa ricerca è proprio questo: rintracciare e rappresentare schematicamente gli ipogei nascosti sotto basiliche, monasteri, ed altri edifici religiosi romani.
Per riuscirci, il punto di partenza sarà l'analisi e la marcatura di un testo: [Diego Angeli, Le Chiese di Roma, Roma, Società Editrice Dante Alighieri, 1922.](https://archive.org/details/lechiesediromagu00ange_0/page/n7/mode/2up) di Diego Angeli. Da esso, mediante una banale ricerca per parole, saranno individuate le chiese dotate di sotterranei, catacombe, parti interrate, permettendoci di costruire un primo file in CSV per averne una visione schematica. Dopodiché, si procederà alla trasformazione del testo selezionato (in formato .txt) in una versione dello stesso marcata in TEI, adoperando tag che permettano l'estrazione delle opere d'arte contenute all'interno delle sezioni ipogee dei luoghi di culto romani.
Infine, sarà stilata una nuova tabella CSV nella quale saranno riportate tutte le opere d'arte sovracitate, associate a tutti i dettagli che sarà stato possibile reperire dal testo di Angeli.
Da quest'ultimo file dovrebbe essere possibile, poi, svolgere ulteriori azioni, come la creazione di LOD in RDF che permettano di associare mediante URI tutte le opere al loro autore, alla loro posizione nel sottosuolo romano, al loro soggetto, al tipo di opera d'arte, ecc.
Roma_Sotterranea è il titolo del progetto d’esame per il corso di [DHDM](https://www.unibo.it/it/studiare/insegnamenti-competenze-trasversali-moocs/insegnamenti/insegnamento/2024/502386) (a.a. 2024/2025).

## Descrizione dei dati

![image](https://github.com/user-attachments/assets/b0b8f115-f4aa-44b0-927f-19f16f7aea75)

I dati sono stati raccolti a partire dalla versione formato ```.txt``` dell'opera di Diego Angeli. A partire da esso è stato possibile ricercare manualmente quali chiese sono dotate di una o più sezioni sotterranee mediante la ricerca per le parole chiave: "sotterraneo/a/i", "catacombe","ipogeo/i/a". Dalla descrizione di queste chiese, associata a ricerche sul Web mirate, poi, sono stati identificati diversi elementi: 

- Identificativo della Chiesa
- Nome della Chiesa
- Riferimento Wikidata relativo alla Chiesa
- Ubicazione della Chiesa
- Costruzione della Chiesa
- Stato attuale della Chiesa
- Contenuto dei Sotterranei
- Edificazione dei Sotterranei
- Stato dei Sotterranei
- Modalità di accesso ai Sotterranei

A partire da queste informazioni è stato quindi possibile creare un dataset tabellare iniziale in formato ```.csv``` che permettesse di isolare le chiese sulle quali concentrare il lavoro successivo. Il nuovo obiettivo è allora diventato la marcatura dei testi selezionati secondo lo standard XML-TEI, utilizzando come riferimento i dati estratti e strutturati nel file ```.csv```. Il testo è quindi stato ripreso in formato ```.txt``` e, dopo aver isolato le chiese dotate di apparati sotterranei, si è proceduto alla creazione di un nuovo file ```.xml``` nel quale il testo è stato strutturato secondo due approcci differenti: dal punto di vista srtutturale e dal punto di vista semantico. Del testo, infatti sono stati marcati:

#### Marcatura Strutturale

- **Paragrafi**, con i tag ```<div type="section">```
- **Intestazioni**, con ```<head>```
- **Capoversi**, come ```<p>```
- **Liste**, mediante i tag ```<list rend="numbered inline">```; e ```<item>```
- **Corsivi**, con ```<hi rend="italic">```
- **Grassetti**, con ```<hi rend="bold">```
- **Note a piè di pagina**, ```<note place="foot">```
- **Interruzione di pagina**, mediante ```<pb n="x"/>```

#### Marcatura Semantica

- **Opere d'arte**, come ```<ref type="work">```
- **Titoli delle opere d'arte**, con i tag ```<title>```
- **Materiale delle opere d'arte**: ```<material>```
- **Autori delle opere d'arte**, marcati come ```<author>```
- **Date**, marcate come ```<date when="x">``` o ```<date from="x" to="y">```
- **Luoghi**, come ```<place>```
- **Persone**, marcate con il tag ```<persName>```
- **Famiglie**, per cui è stato utilizzato ```<ref type="org">```
- **Avvenimenti**: ```<ref type="event">```
- **Lingue straniere (spec. Latino e Greco)**, marcate come ```<foreign xml:lang="x">```
- **Numeri**, come ```<num type="caridnal" value="x">``` oppure ```<num type="ordinal" value="y">```
- **Misure**, marcate con il tag <measure type="x" quantity="y" unit="z">```
- **Valori monetari**, marcati come misure e con il tag ```@unit``` completato con la sigla della valuta utilizzata in Wikidata
- **Concetti generici**, come ```<rs>```

Nonostante il risultato ottenuto presenti una marcata disomogeneità e una scarsa coerenza tra le entità, a causa sia dell'inadeguatezza del formato TEI per descrivere opere d'arte sia per via dello stile di scrittura di Diego Angeli, il cui tende a preferire frasi spezzate in cui le informazioni sono spesso date in maniera discontinua (fatti che compromettono inevitabilmente l'operabilità di questa marcatura da parte di un sistema informatico), da questi dati è stato comunque possibile costruire un secondo dataset tabellare in formato ```.csv```, costituito da un file per ogni chiesa dotata di almeno un'opera d'arte nel suo sotterraneo. In questi casi, non si è fatto altro che utilizzare come metadati i tag adoperati per la marcatura:

- ID_opera
- Provenienza
- Titolo
- Tipo
- Materiale
- Soggetto(QID)
- Autore_1(QID)
- Autore_2(QID)
- Autore_3(QID)
- Data
- Specifiche_Data(Da-A)
- Data_Restauro
- Autore_Restauro

Questo lavoro ha prodotto risultati interessanti, aprendo la possibilità di ampliare la ricerca in molti modi, ma non si può sicuramente dichiarare un successo. Infatti, se l'obiettivo iniziale era quello di rendere operabile da un sistema il testo di Diego Angeli, questo è avvenuto soltanto in parte. Inserendo il file in Phthon o altro software adibito alla trasformazione di dati non strutturati in dati strutturati, si noterà molto facilmente la grande difficoltà con cui essi riescono a districarsi tra le maglie di un testo talmente complesso, restituendo datset confusi o del tutto erronei. Ciononostante, una raccolta di file come quelli prodotti in questa ricerca, come si è detto, possono comunque essere utili. Nello specifico, a partire da essi è possibile:

1. Procedere alla creazione di Linked Open Data in cui tutte le opere d'arte siano collegate ad almeno un altro dato, come la la chiesa al di sotto della quale si trova, se non proprio a una quantità molto ampia di altri dati, dall'autore all'epoca in cui è stata prodotta, dal materiale che la costituisce e al tipo di forma d'arte a cui appartiene fino al soggetto che rappresenta o a cui è dedicata;
2. Migliorare la marcatura adoperando architetture di Markup diverse e più flessibili di XML-TEI, in modo da rendere il dataset davvero interoperabile;
3. Creare guide turistiche dei sotterranei di Roma più aggiornate;
4. Geolocalizzare con una buona precisione le opere d'arte descritte da Diego Angeli, associandole alle mappe dei sotterranei delle Chiese di Roma, disponibili on line, così da dare vita a carte temeatiche specifiche;
5. Completare i dataset in ```.csv``` grazie a un processo di riconciliazione delle authority tramite Open Refine.

## Documentazione e qualità dei dati

I dati sono archiviati e resi accessibili su Git Hub, il cui dataset è composto da due cartelle:

1. **data**, che include due sotto cartelle, **csv** e **xml** ;
2. **docs**, al cui interno sono presenti la **fonte** utilizzata e il  **data management plan**

Inoltre si è provveduto a preservare i dataset tabellari pubblicandoli su [Zenodo](https://zenodo.org/) e creando un DOI per ognuno di essi. 

## Licenza

Tutti i dati saranno registrati sotto sotto licenza CC0 1.0.
