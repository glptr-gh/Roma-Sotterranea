# Progetto d'esame DHDMCH 2024/2025

## Indice

- [Autore e Link](#Autore-e-Link)
- [Introduzione](#Introduzione)
- [L' idea](#L'-idea)
- [Il Progetto](#Il-Progetto)
- [I Risultati](#I-Risultati)
- [Problemi e Future Works](#Problemi-e-Future-Works)
- [La Grande Assente](#La-Grande-Assente)
- [Conclusione](#Conclusione)

## Autore e Link

Gianluca Petrosillo -- ORCID: [0009-0002-2249-1894](https://orcid.org/0009-0002-2249-1894) -- [Repository GitHub](https://github.com/glptr-gh/Roma-Sotterranea/tree/main)

## Introduzione

È possibile mappare i sotterranei di Roma e il loro contenuto a partire da una guida turistica delle chiese capitoline? L'obiettivo di questa ricerca è proprio questo: rintracciare e rappresentare schematicamente gli ipogei nascosti sotto basiliche, monasteri, ed altri edifici religiosi romani.
Per riuscirci, il punto di partenza è stata l'analisi e la marcatura di un testo: [Diego Angeli, Le Chiese di Roma, Roma, Società Editrice Dante Alighieri, 1922.](https://archive.org/details/lechiesediromagu00ange_0/page/n7/mode/2up) di Diego Angeli. Da esso, mediante una banale ricerca per parole, sono state individuate le chiese dotate di sotterranei, catacombe, parti interrate, permettendo di costruire un primo file in CSV per averne una visione schematica. Dopodiché, si è proceduto alla trasformazione del testo selezionato (in formato .txt) in una versione dello stesso marcata in TEI, adoperando tag che permettessero l'estrazione delle opere d'arte contenute all'interno delle sezioni ipogee dei luoghi di culto romani.
Infine, è stata stilata una nuova tabella CSV nella quale saranno riportate tutte le opere d'arte sovracitate, associate a tutti i dettagli che è stato possibile reperire dal testo di Angeli.
Da quest'ultimo file dovrebbe essere possibile, poi, svolgere ulteriori azioni, come la creazione di LOD in RDF che permettano di associare mediante URI tutte le opere al loro autore, alla loro posizione nel sottosuolo romano, al loro soggetto, al tipo di opera d'arte, ecc.
Roma_Sotterranea è il titolo del progetto d’esame per il corso di [DHDMCH](https://www.unibo.it/it/studiare/insegnamenti-competenze-trasversali-moocs/insegnamenti/insegnamento/2024/502386) (a.a. 2024/2025).

## L'idea

![image](https://github.com/user-attachments/assets/b0b8f115-f4aa-44b0-927f-19f16f7aea75)

I dati sono stati raccolti a partire dalla versione formato ```.txt``` dell'opera di Diego Angeli. A partire da esso è stato possibile ricercare manualmente quali chiese sono dotate di una o più sezioni sotterranee mediante la ricerca per le parole chiave: "sotterraneo/a/i", "catacombe","ipogeo/i/a". Il risultato è il file [Chiese_Sotterranee.csv](https://github.com/glptr-gh/Roma-Sotterranea/blob/main/data/CSV/Chiese_Sotterranee.csv), dal quale è possibile vedere come dalla descrizione di queste chiese, associata a ricerche sul Web mirate, sono stati identificati diversi elementi: 

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

## Il progetto

A partire da queste informazioni è stato quindi possibile creare un dataset tabellare iniziale in formato ```.csv``` che permettesse di isolare le chiese sulle quali concentrare il lavoro successivo. Il nuovo obiettivo è allora diventato la marcatura dei testi selezionati secondo lo standard XML-TEI, utilizzando come riferimento i dati estratti e strutturati nel file ```.csv```. Il testo è quindi stato ripreso in formato ```.txt``` e, dopo aver isolato le chiese dotate di apparati sotterranei, si è proceduto alla creazione di un nuovo file ```.xml``` nel quale il testo è stato strutturato secondo due approcci differenti: dal punto di vista srtutturale e dal punto di vista semantico. Del testo, infatti, sono stati marcati:

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
- **Misure**, marcate con il tag ```<measure type="x" quantity="y" unit="z">```
- **Valori monetari**, marcati come misure e con il tag ```@unit``` completato con la sigla della valuta utilizzata in Wikidata
- **Concetti generici**, come ```<rs>```

## I Risultati

  ```<div type="section">```
            ```<head><ref type="place" target="https://www.wikidata.org/wiki/Q385910">S.CLEMENTE</ref>.</head>```
            ```<p>BASILICA SOTTERRANEA. — Questa basilica primitiva fu costruita sopra un edificio dell'<ref type="org" target="https://www.wikidata.org/wiki/Q2277">impero</ref> che a sua volta era stato eretto sopra costruzioni dell'<date from="0509" to="27">epoca repubblicana</date>. In queste costruzioni fu rinvenuta una <rs><hi rend="italic">cella</hi></rs> col <ref type="work"><title>simulacro di Mitra</title></ref>, il che fa supporre - sapendosi essere stata quella l'abitazione di <persName target="https://www.wikidata.org/wiki/Q42887">San Clemente</persName> - che```
            ```<pb n="101"/>```
            ```le case del martire fossero confiscate durante una <rs type="event">persecuzione</rs> e cedute ai <rs type="person">sacerdoti di <ref type="character" target="https://www.wikidata.org/wiki/Q6497135">Mitra</ref></rs> il cui <rs type="org">culto</rs> era molto esteso negli ultimi <measure type="time" quantity="100" unit="year">secoli</measure> dell'<ref type="org" target="https://www.wikidata.org/wiki/Q2277">Impero</ref>. La chiesa è formata da <num type="cardinal" value="1">un</num> vestibolo e da <num type="cardinal" value="1">un</num> tempio a <num type="cardinal" value="3">tre</num> navi le cui absidi erano assai maggiori delle attuali. Le pareti sono dipinte da <ref type="work"><title>affreschi</title> di <date from="400" to="1099">epoche diverse, che variano dal V all’XI secolo</date></ref>.</p>```

Com'è possibile notare dal file [Chiese_di_Roma_Angeli_Sotterranei.xml](https://github.com/glptr-gh/Roma-Sotterranea/blob/main/data/XML/Chiese_di_Roma_Angeli_Sotterranei.xml), il risultato ottenuto presenta una marcata disomogeneità e una scarsa coerenza tra le entità, a causa sia dell'inadeguatezza del formato TEI per descrivere opere d'arte sia per via dello stile di scrittura di Diego Angeli, il cui tende a preferire frasi spezzate in cui le informazioni sono spesso date in maniera discontinua (fatti che compromettono inevitabilmente l'operabilità di questa marcatura da parte di un sistema informatico). Nonostante ciò, da questi dati è stato comunque possibile costruire manualmente un secondo dataset tabellare in formato ```.csv```, costituito da un file per ogni chiesa dotata di almeno un'opera d'arte nel suo sotterraneo: sono tutti visibili nella cartella [CSV](https://github.com/glptr-gh/Roma-Sotterranea/tree/main/data/CSV). In questi casi, non si è fatto altro che utilizzare come metadati i tag adoperati per la marcatura:

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

## Problemi e Future Works

Questo lavoro ha prodotto risultati interessanti, aprendo la possibilità di ampliare la ricerca in molti modi, ma non si può sicuramente dichiarare un successo. Infatti, se l'obiettivo iniziale era quello di rendere operabile da un sistema il testo di Diego Angeli, questo è avvenuto soltanto in parte. Inserendo il file in Phthon o altro software adibito alla trasformazione di dati non strutturati in dati strutturati, si noterà molto facilmente la grande difficoltà con cui essi riescono a districarsi tra le maglie di un testo talmente complesso, restituendo datset confusi o del tutto erronei. Ciononostante, una raccolta di file come quelli prodotti in questa ricerca, come si è detto, possono comunque essere utili. Nello specifico, a partire da essi è possibile:

1. Procedere alla creazione di Linked Open Data in cui tutte le opere d'arte siano collegate ad almeno un altro dato, come la la chiesa al di sotto della quale si trova, se non proprio a una quantità molto ampia di altri dati, dall'autore all'epoca in cui è stata prodotta, dal materiale che la costituisce e al tipo di forma d'arte a cui appartiene fino al soggetto che rappresenta o a cui è dedicata;
2. Migliorare la marcatura adoperando architetture di Markup diverse e più flessibili di XML-TEI, in modo da rendere il dataset davvero interoperabile;
3. Creare guide turistiche dei sotterranei di Roma più aggiornate;
4. Geolocalizzare con una buona precisione le opere d'arte descritte da Diego Angeli, associandole alle mappe dei sotterranei delle Chiese di Roma, disponibili on line, così da dare vita a carte temeatiche specifiche;
5. Completare i dataset in ```.csv``` grazie a un processo di riconciliazione delle authority tramite Open Refine.

## La Grande Assente

Purtroppo, per mancanza di tempo e problematiche del dataset in se stesso, non è stato possibile effettuare una pulizia organica dei dati. Se per qwuanto riguarda il dataset tabellare, a impedirlo è stata soprattutto la mancanza di tempo, il problema principale riscontrato nel tentativo di svolgere una pulizia del file XML, infatti, sta nel fatto che Open Refine non riesce a leggere il file, non accettando la mancanza di un tag di chiusura dei capoversi (```</p>```); problematica che non può essere risolto a meno di penalizzare la fedeltà alla struttura del testo, la quale è stata uno dei primi _must_ del progetto di marcatura.

## Conclusione

In conclusione, si può dire che questo progetto si caratterizza principalmente come un fallimento, ma un fallimento dal quale è stato possibile ricavare qualcosa di buono e che, soprattutto, insegna molto sul modo giusto (o forse su tutti i modi sbagliati) con cui andrebbe gestito un progetto di Data Management. Conoscere meglio XML e TEI ha permesso di comprenderne meglio le potenzialità e i limiti, e utilizzare GitHub ha aperto un mondo che difficilmente sarà possibile ignorare in futuro. Open Refine, seppure poco utilizzato, si è dimostrato un ottimo strumento il quale, se ustao correttamente, può velocizzare molto il lavoro su un progetto, e Zenodo ha aperto uno spiraglio nel vasto mondo dei ricercatori e della ricerca. Con queste consapevolezze, sarà molto più facile in futuro fare le scelte corrette, e soprattutto capire quando un'idea rischia di essere troppo dispendiosa dal punto di vista del tempo e delle risorse necessarie a portarlo a termine.

Grazie dell'attenzione.

