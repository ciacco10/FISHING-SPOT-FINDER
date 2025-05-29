# FISHING-SPOT-FINDER
Fishing Spot Finder

INDICE
1. Descrizione e obiettivi del progetto
2. Istruzioni su come usare il progetto
3. Scelte architetturali fatte e la motivazione
4. Scomposizione in servizi e il loro ruolo
5. Architettura dei servizi e la loro implementazione
6. Stato del progetto
7. Problemi o cose da risolvere
1) Descrizione e obiettivi del progetto
Fishing Spot Finder è un'applicazione web progettata per aiutare pescatori
amatoriali ed esperti a trovare i migliori spot di pesca in Italia.
Gli utenti possono filtrare gli spot di pesca selezionando
la regione
la provincia
il tipo di pesce che desiderano pescare.
Per ogni spot, vengono mostrate:
le condizioni meteo in tempo reale,
i pesci presenti,
una mappa interattiva con marker.
L'obiettivo principale è semplificare la ricerca di luoghi ideali per la pesca,
migliorando l'esperienza degli utenti grazie a dati aggiornati e una grafica chiara.
2) Istruzioni su come usare il progetto
1. Installare e avviare un server locale, ad esempio XAMPP.

Fishing Spot Finder 1

2. Copiare il progetto nella cartella htdocs .
3. Inserire le proprie API Key di:
OpenWeather in .env.php
Google Maps in index.html
4. Avviare Apache da XAMPP.
5. Accedere via browser a: http://localhost/fishing-spot-finder/index.html
6. Selezionare una regione, una provincia e un tipo di pesce dai menu a tendina.
7. Visualizzare i risultati sulla mappa e in elenco testuale.
3) Scelte architetturali fatte e la motivazione
Abbiamo scelto un'architettura a servizi separati per renderlo facile da espandere
o modificare, per
la semplicità di integrazione tra front-end e back-end e per l'efficienza di
caricamento per l'utente.
Tecnologie scelte:
HTML, CSS, JavaScript per il front-end: semplicità e compatibilità.
PHP per il back-end: adatto per ambienti locali tipo XAMPP.
JSON locale: per i dati spot rapido e facile da aggiornare.
API esterne (Google Maps e OpenWeather): per dati geografici e meteo.
4) Scomposizione in servizi e il loro ruolo
index.html: interfaccia grafica, filtri di ricerca, mappa interattiva,
visualizzazione dei risultati.
results.php: riceve i parametri provincia e pesce, filtra gli spot da spots.json ,
richiama OpenWeather API e restituisce i dati al front-end.
.env.php: file di configurazione sicuro per memorizzare l'API Key di
OpenWeather.
data/spots.json: archivio statico degli spot di pesca italiani (nome, coordinate,
provincia, tipi di pesce).

Fishing Spot Finder 2

5) Architettura dei servizi e la loro implementazione
Schema logico:
Utente → index.html → fetch → results.php → (spots.json + OpenWeather API) →
Risultati (mappa + elenco)
Il front-end invia richieste GET a results.php .
Il PHP filtra gli spot, chiama OpenWeather per il meteo e restituisce un JSON.
Il front-end riceve i dati e aggiorna la mappa e la lista dei risultati.
Non abbiamo usato database o server complessi per mantenere la semplicità di
gestione e la compatibilità con XAMPP.
6) Stato del progetto
Funzionalità attuali implementate:
Ricerca degli spot per provincia e tipo di pesce.
Mappa interattiva con marker.
Informazioni testuali sugli spot (nome, pesci, recensioni, meteo).
Condizioni meteo aggiornate in tempo reale per ogni spot.
7) Problemi o cose da risolvere
Alcuni spot hanno coordinate approssimative: servirebbe affinare la posizione
esatta (es. centratura laghi).
