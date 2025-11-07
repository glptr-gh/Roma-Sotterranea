# CARTELLA XML

## Indice 
1. [Chiese_di_Roma_Angeli_Sotterranei.xml](https://github.com/glptr-gh/Roma-Sotterranea/blob/main/data/XML/Chiese_di_Roma_Angeli_Sotterranei.xml)

## Chiese_di_Roma_Angeli_Sotterranei.xml

### Nome del file 
Chiese_di_Roma_Angeli_Sotterranei.xml

### Descrizione 
Dopo aver scaricato i brani scelti dall'opera di Diego Angeli [Diego Angeli, Le Chiese di Roma, Roma, Società Editrice Dante Alighieri, 1922.](https://archive.org/details/lechiesediromagu00ange_0/page/n7/mode/2up) in formato ```.txt```, essi sono stati caricati su [VISUAL STUDIO CODE](https://vscode.dev/) e marcati in TEI. il testo è stato strutturato secondo due approcci differenti: dal punto di vista srtutturale e dal punto di vista semantico. Del testo, infatti, secondo le linee guida TEI sono stati marcati:

#### Marcatura Strutturale

- **Paragrafi**, con i tag <div type="section"
- **Capoversi**, come <p
- **Liste**, mediante i tag <list rend="numbered inline"; e <item
- **Corsivi**, con <hi rend="italic"
- **Grassetti**, con <hi rend="bold"
- **Note a piè di pagina**, <note place="foot"

#### Marcatura Semantica

- **Opere d'arte**, come <ref type="work"
- **Titoli delle opere d'arte**, con i tag <title
- **Materiale delle opere d'arte**: <material
- **Autori delle opere d'arte**, marcati come <author
- **Date**, marcate come <date when o <date from="x" to="y"
- **Luoghi**, come <place
- **Persone**, marcate con il tag <persName
- **Famiglie**, per cui è stato utilizzato <ref type="org"
- **Avvenimenti**: <ref type="event"
- **Lingue straniere (spec. Latino e Greco)**, marcate come <foreign xml:lang="x"
- **Numeri**, come <num type="caridnal" value="x" oppure <num type="ordinal" value="y"
- **Misure**, marcate con il tag <measure type="x" quantity="y" unit="z"
- **Valori monetari**, marcati come misure e il tag @unit completato con la sigla della valuta utilizzata in Wikidata
- **Concetti generici**, come <rs
