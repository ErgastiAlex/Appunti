# Domande Sistemi Informativi

###### Illustrare il concetto di stratificazione dei protocolli nelle reti di comunicazione.

Durante l'evoluzione la progettazione delle reti si è dovuto fare fronte a una continua evoluzione tecnologica. Per creare una rete il più possibile verasile si è passati a una stratificazione dove ogni livello semplifica le operazioni a quello successivo.
Dal basso abbiamo:
- livello fisico: si intende tutto ciò che collega fisicamente due host.
- data link: gestisce l'organizzazione dei dati per eesere trasmessi sulla rete fisica.
- rete: si occupa dell'indirizzamento e instradamento dei pacchetti.
- trasporto: definisce direttive per trasportare le informazioni in modo affidabile.
- sessione: stabilisce la creazione di sessioni di comunicazione tra 2 host.
- presentazione: converte i vari tipi di rappresentazione per essere compresi della diverse macchine.
- applicativo: specifica come ogni singola applicazione utilizza la rete per scambiare dati.

Lo standard più usato è TCP/IP che semplifica lo stack ISO/OSI in 5 livelli:
- fisico
- linea
- rete
- trasporto
- applicativo

###### Descrivere le caratteristiche degli schemi a stella e fiocco di neve nella progettazione di DataWarehouse, evidenziando le differenze rispetto agli schemi tradizionali di gestione dei dati in un database.
I database usati nei DataWarehouse devono essere ottimizzati per l'accesso rapido ai dati durante una analisi.
per questo solitamente si utilizza un sistema a stella dove si pone al centro una "fact table" che contiene gli elementi da registare.
i rami della stella sono le dimensioni che si utilizzano poi per fare l'aggregazione dei dati durante l'analisi.
quando il database è molto gerarchico si avrebbero delle dimensioni che crescono in dimensione e quaindi si tenda a passare a una struttura "snowflake" che assomiglia di più a un database entità-renalzione standard.

###### Illustrare sinteticamente il concetto di “commoditizzazione delle ICT”.
Con l'avanzare tecnologico di sistemi informatici e reti di comunicazione i sistemi ICT hanno evidenziato caratteristiche simili a quelle delle "comodty", ovvero una elevata standardizzazione, un alta facilità di replicazione data dal fatto che i dati sono per definizione al risosrsa più replicabile, una facilitò di distribuzione che è superiore a qualunque prodotto e una riduzione dei costi.
Tutto questo ha portato sempre di più a considerare questi sitemi con un vero e prorpio prodotto e a fare nascere un mercato dell'ICT.

###### Descrivere le differenze fra WAN,MAN,LAN e PAN

- PAN (Personal Area Network): Si intende quella rete basata su dispositivi vicini a una persona, come smartphone, smartwatch o simile. Utilizza principalmente tecnologie come Bluetooth, RFID o ZigBee

- LAN (Local Area Network): Rete con estensione di qualche stanza o un edificio. Si utilizzano tecnologie omogenee (wifi ed ethernet) e permette di avere alte prestazioni (~Gbps)

- MAN (Metropolitan Area Network): Rete di espansione metropolitana, connette intere città tra di loro, tecnologia limitatamente disomogenea e con prestazioni variabili in base al numero di utenti.

- WAN (Wide Area Network): Interconnessione tra varie MAN, per esempio collegamenti dorsali tra nazioni o continenti.

###### Descriviere i limiti delle metodologie tradizionali di project management ai progetti IT

Le tecnologie tradizionali falliscono nei progetti IT a causa di varie caratteristiche di quest'ultimi:

- Contesto dinamico: Un progetto IT è sviluppato in un contesto che cambia, sia come requisiti, sia come legislazione ed è quindi necessario adattarlo anche in corso d'opera

- Requisiti non chiari: Non sempre il cliente è in grado di spiegare cosa gli serva

- Forte dipendenza dai dettagli: Un progetto IT può risultare fallimentare se piccoli dettagli si rivelano non funzionanti

- Difficoltà di analisi stato di avanzamento: Nei progetti IT un utilizzo del 50% delle risorse non corrisponde ad uno stato di avanzamento del 50%

- Necessità di documentazione: Trade-off -> Costo, Documentazione e tempo

- Il project manager non può conoscere tutto, quindi alcuni cambiamenti potrebbero portare cambi radicali nel progetto

- Nello sviluppo IT è necessario che il progetto tenga conto sia del contesto in cui opera l'azienda (dinamico o statico) sia del contesto dove verrà utilizzato il software(es: l'italia ha determinate leggi)

###### Descrivere fornendo un esempio cosa si intenda per cubo multi-dimensionale nelle analisi OLAP (Online Analytical Processing).

Nelle analisi OLAP si organizzano i dati in cubi multidimensionali ponento una determinata dimensione su ogni asse di riferimento.
a questo punto si puù procedere con i vari tipi di analisi che ripicamente sono:
- slice: ovvero si taglia un il cubo per fissare una misura specifica di una dimensione.
- drill down/up: si prende una misura e da quella si analizzano tutte le altre dimensioni.
- drill across: si analizza passando attraverso le varie misure di una dimansione.
- rotazione: tipica analisi dove si ruota l'aggregazione.

###### La società che ha realizzato l’applicazione YOUP (vedi Domanda n. 1) gestisce il sistema attraverso propri server, ospitati in una propria infrastruttura. A quali problemi di sicurezza informatica dovrà fare attenzione e perché?

TODO

###### Illustrare le differenze, fornendo anche alcuni esempi, fra requisiti funzionali e non funzionali nell’analisi dei requisiti di un progetto software.

La differenza tra requisito funzionale e non è che un requisito funzionale descrive qualcosa che l'utente richiede e che può utilizzare, quindi una vera e propria funzione (Requisiti cliente, es: Devo poter visualizzare le fatture emesse).
I requisiti non funzionali descrivono proprietà del sistema e si raggruppano in:

- Di Prodotto: Determinate caratteristiche che il prodotto deve avere, come usabilità o prestazione
- Organizzativi: Requisiti di organizzazione della progettazione
- Esterni: Requisiti etici, legislativi e di sicurezza.

###### Illustrare il significato di portafoglio applicativo e spiegare l’utilità dell’integrazione fra portafoglio applicativo e diagramma dei processi (per es. modellato attraverso la catena del valore di Porter).

Per portafoglio applicativo si intende l'insieme di software che un'azienda usa per lavoare. solitamente un portafoglio applicativo molto vasto è sintomo di un'azienda con un sistema nformativo poco strtturato e organizzato.
spsso si integra con il diagramma dei processi in modo da rendere evidente in quale momento del processo produttivo viene utlizzato ogni pacchetto applicativo.

###### Descrivere sinteticamente, ed eventualmente attraverso esempi, la differenza fra steganografia e crittografia nella comunicazione di messaggi segreti.

- steganografia : nascondere informazioni in un oggetto (fisico o non) per trasmetterle senza che vengano riconosciute.
- crittogrfia: cambiare le informazioni in modo che solo mittente e destinatario riescano a capirla.

###### Illustrare sinteticamente le principali caratteristiche delle tecnologie di comunicazione wireless utilizzate per distanze limitate (reti LAN/PAN).

Le principali tecnologie senza fili utilizzate nelle reti PAN sono:

- Bluetooth: Ha un raggio di qualche decina di metri e velocità variabile in base alla versione, il bluetooth 5.0 è in grado di modulare in base alla distanza la velocità massima ed esegue un continuo cambio di banda per evitare interferenze

- RFID: Utilizzato per lo scambio di pochi kbps di dati, necessita di un reader in grado di ricevere i dati da un tag, che può essere passivo, ovvero riceve energia dal reader o attivo, ovvero contiene al suo interno una batteria

Nelle reti LAN invece viene utilizzato il Wi-Fi, necessità di un hotspot, ovvero un punto di connessione, ha capacità di banda e di raggiungimento variabile in base alla frequenza, il Wi-Fi 2.4Ghz riesce a "passare" i muri più facilmente ha quindi un raggio di ricezione più ampio a scapito di velocità più lente, il Wi-Fi 5Ghz invece ha un raggio più corto ma prestazioni molto più elevate, anche fino al Gbps

###### Illustrare sinteticamente le principali ragioni ed i fenomeni (sia tecnologici che di mercato) che hanno consentito l’evoluzione delle architetture dei Sistemi Informativi da quelle centralizzate a quelle distribuite.

I costi esorbitanti della tecnologia all'inizio portavano a costruire ochi sistemi centralizzati. Con la necessità di avere però un sistema di controllo molto rapido le aziende hanno iniziato a portare questi sistemi sempre più vicini a loro fino ad arrivare ad avere sistemi minuscoli e molto economci che controllino ogni aspetto del processo produttivo.

###### Illustrare le principali tipologie di Sistemi Informativi secondo una classificazione organizzativa/di mercato.

TODO: Expand
Esistono 3 tipologie di sistemi informativi:

- Operazionali: Aiutano un operatore nello svolgere funzioni molto pratiche, quindi per esempio fatture, ordini, etc..
- MIS: Forniscono dati aggregati e vengono utilizzate da figure gestionali per decisione di business
- Analytics: Forniscono non solo dati aggregati ma anche il dettaglio di questi e vengono utilizzate dai vertici per le decisioni

Si possono suddividere anche in:

- Personali
- Collaborativi o enterprise

###### Illustrare i principi generali della modalità di gestione dei requisiti utente attraverso le User stories.

Le User Stories vengono utilizzate per la definizione dei requisiti funzionali e vengono espresse in questo modo:

    Come \<Ruolo>, Voglio \<Funzione>, così che \<Motivazione>

Le user stories devono essere:

- Piccole
- Testabili (Tramite Acceptance Criteria)
- Stimabili
- Preziose
- Negoziabili

Si basano sulle 3C:

- Card (Espressa prima)
- Conversation (Negoziazione)
- Confirmation (Conferma delle richieste)

###### Descrivere sinteticamente le principali tendenze evolutive delle applicazioni CRM.

i sistemi CRM servono alle aziende per comunicare in modo efficace ed efficente con i clienti. spesso questi sistemi sono integrati negli ERP come moduli di base o aggiuntivi.
Con l'avanzare della tecnologia si è passati dal call center a spostare il sistema online con chat.
il trend è ora di spotare il sistema sui social e se possibile aggiungere dei chatbot che provino a risolvere i problemi più basilari o indirizzare al reparto corretto il cliente.

###### Come è fatto un portafoglio applicativo spaghetti integration e che problemi ha
