## L'edizione digitale VaSto: funzionalità e limitazioni 

L'edizione digitale VaSto presenta la "Storia Fiorentina" di Varchi, in particolare il suo testimone RC4. Allo stato attuale la piattaforma presenta il proemio del Primo Libro (versione Pilot).
L'edizione digitale è stata implementata su EVT2 - beta 2, customizzando quest'ultimo nei casi di necessità specifici riportati nei prossimi paragrafi.   
EVT-2 permette di caricare facilmente un file in formato XML (il quale segue l’encoding XML-TEI) contente l'encoding dell'edizione. Il documento XML che contiene il testo marcato è unico e contiene tutti gli elementi dell'edizione critica e diplomatica (opportunamente abilitati e disabilitati in un file CSS a seconda delle esigenze di visualizzazione).

La customizzazione della Piattaforma VaSto rispetto il pacchetto EVT-2 avviene attraverso la modifica di tre file: 
- il file XML contenente il testo marcato secondo le guidelines XML-TEI (in questo specifico caso ```data/pilot_proemio.xml```).
- il file json di configuarazione della visualizzazione (```config/config.json```).
- il file CSS messo a disposizione da EVT-2 per facilitare la customizzazione della visualizzazione (```config/custom_style.css```).

## L'edizione digitale Vasto: fuzionalità e visualizzazioni

Come descritto in precedenza, l'edizione digitale è composta dall'edizione diplomatica e critica insieme ad alcune funzionalità trasversali alle edizioni (o "knowledge site"). 


## Funzionalità trasversali alle edizioni
Con "funzionalità trasversali alle edizioni" (o "knowledge site") si intendono tutte quelle funzionalità consultabili nel sistema a prescidere dall' edizione (diplomatica o critica) sul quale l'utente si trova. Le funzionalità sono le seguenti:

* Nella presente edizione vengono attivate solo le visualizzazioni "Testo di Lettura" e "Immagine Testo"
*	Tutte le scelte stilistiche usate per indicare i fenomeni testuali e le pelculiarità sopracitate sono indicizzati nella sezione info in alto.
* Possibilità di scaricare il file XML che descrive l'edizione (bottone in alto a destra)
* Metadati descrittivi (bottone in alto a destra)
* Considerando la natura annalistica della "Storia Fiorentina", testo è ricco di citazioni di luoghi, persone e date, che vengono marcate e visualizzate grazie al menù in basso (```NamedEnititySelection```) ed inoltre visualizzate in un indice generato automaticamente (dal menù in alto a destra - "Apri Liste").

## Funzionalità dell'edizione diplomatica

L’edizione diplomatica si impegna a visualizzare il testo nel modo più simile possibile alle immagini proposte.
In particolare vengono annotati e visualizzati: 
* linebreak.
* le aggiunte a margine, in riga, o a piè di pagina. Inoltre nel testo vi è un’ancora (solitamente ```^```) che, se selezionata dall'utente, permette di illuminare l’addizione corrispondente. 
* Al centro della presente edizione diplomatica vi è la coesistenza di quattro diverse mani (cassature e addizioni) sul testimone RC4. L’edizione vuole quindi visualizzare in modo efficacie tale peculiarità. Le cassature sono rappresentate con  lo stile "line-trough" (scelta tipografica con linea colorata che passa al centro del testo) del colore corrispondente alla mano che l'ha creata. Allo stesso modo le aggiunte vengono segnalate con il colore del testo corrispondente alla mano che l'ha prodotta. La legenda relativa a questo aspetto è consultable cliccando sul bottone "info".
* Nella diplomatica le abbreviazioni vengono sciolte e segnalate in corsivo e grassetto. Tale analisi è stata curata da Dario Brancato. 
* Nella visualizzazione "Immagine-Testo" è presentata la corrispondenza tra testo diplomatico e facsimile. 

### Funzionalità aggiuntive rispetto ad EVT2 nell'edizione diplomatica 
* EVT2 non supporta alcuna visualizzazione dei marginalia del manoscritto. Le aggiunge a margine o a piè di pagina sono state customizzate specificamente per questa edizione. Lo stesso è stato fatto per le aggiunte in alto o in basso all'interno delle righe del testo (anche chiamate addizioni "in line"). 
* EVT2 non si occupa delle distinzioni delle mani nell'edizione diplomatica. I colori che segnalano le mani sono stati customizzati per questa edizione attraverso il file di customizzazione (CSS).   

## Funzionalità dell'edizione critica 

L'edizione critica presenta il testo RC4, dopo la redazione a cura di Dario Brancato, ma scindendolo in due testimoni fittizi: RC4 - il testo contenente l'ultima volontà dell'autore ed RC4c - il testo contenente le cassature postume a cura di Baldini.  
* Normalizzazioni del testo originale (regolarizzazioni, correzioni senza alcun riferimento tipografico).
* Abbreviazioni sciolte senza alcun riferimento tipografico.
* Il testo è in versione scroll-down. La divisione delle pagine è segnalata inline all'interno del testo (ad esempio con la dicitura [12v]).
* Le Note a margine e a piè di pagina sono rappresentate come parte integrante del testo senza alcuna distinzione tipografica ed appropriatamente inserite in esso. 
* Le segnalazioni tipografiche delle mani sono eliminate 
* Segni particolari (ad esempio ```^``` oppure ```-```) sono normalizzati e/o eliminati.
* Il testo è ottimizzato per la lettura e la comprensione testuale.
* La visualizzazione più indicata al confronto tra RC4 ed RC4c è la funzionalità "Collazione".

### Limitazioni significative dell'edizione critica 
* In tutte le visualizzazioni del testo critico abbiamo aggiunto dei piccoli riferimenti alla divisione in pagine (per esempio [8v]) marcati come ```<lb n="8v">``` nel testo. 
* Nella visualizzazione "Immagine-Testo". Il carosello di immagini (posizionato a sinistra nella visualizzazioni "Immagine Testo") non segue lo scroll-down del testo a destra. Non vi è quindi nella visualizzazione una corrispondenza dinamica tra scroll-down del testo critico e scorrimento delle immagini nel carosello. E' comunque ancora possibile un confronto manuale immagine-testo grazie all'indicazione nel testo della pagina del manoscritto (ad esempio "[8v]") su cui l'utente si trova. 
* La scelta di creare un testimone "fittizio" (RC4c) è stata dettata dal fatto che EVT2 richieda l'uso del tag ```<app>``` per abilitare la funzionalità "Collazione". 
* La prima scelta visuale per comparare il due testi è stata quella di utilizzare ```<app><rdgGrp><rdg wit="#RC4"></rdg><rdg wit="RC4c"></rdg></rdgGrp></app>```. Questo schema di encoding, supportato da EVT2, presenta ancora delle limitazioni nella visualizzazione (ad esempio qualsiasi tag inserito all'interno di ```<rdg>``` non viene visualizzato). Abbiamo dunque scelto di utilizzare invece lo schema XML-TEI ```<app><lem wit="#RC4"></lem><rdg wit="RC4c"></rdg></app>```. Nonostante questo schema presenti meno limitazioni, notiamo che gli spazi non vengono ben rispettati. Al momento attendiamo la release ufficiale di EVT2 beta2 per risolvere queste imperfezioni. 

## Lista dei tag XML-TEI utilizzati per l'encoding dell'edizione
Il progetto Vasto al momento, come già detto in precedenza, è da considerasi una versione pilot che necessita di essere arricchita con altri materiali. Allo scopo di ampliare il progetto, di seguito rilasciamo una legenda di tag che sono stati utilizzati nel file ```xml pilot_proemio.xml``` e che sono stati appostiamente customizzati per rispettare le esigenze del testimone. In particolare presentiamo qui di seguito la lista di tag presenti nel ```<body>``` del file XML. 

* titolo ```<head>```
* divisione pagine ```<pb> @n @xml:id``` con ```<lb @n>``` (l'ultimo per indicare la divisione in pagine dell'edizione critica).
* divisione per libri/sezioni ```<div>``` attrib ```@type @xml:id```
* divisione righe ```<lb>```
* integrazione abbreviazioni manoscritto ```<emph> @rend```
* aggiunte ```<add> @hand @place @n```
* cassature ```<del> @hand``` 
* normalizzazioni ```<choice><sic><corr>```
* regolarizzazione diplomatica-critica: ```<span><choice> <orig><reg>```
* collegamento tra ancora nel testo e la nota a margine corrispondente ```<span n="x"></span><span @place n="x">```

* nomi di persona ```<persName> @ref```
* nomi di luoghi ```<placeName> @ref```
* date <date> ```@when```

* ```<app><lem @wit @hand></lem><rdg @cause @wit"> </rdg></app>```

Per ulteriori esempi ed informazioni consulta il file ```data/pilot_proemio.xml```

