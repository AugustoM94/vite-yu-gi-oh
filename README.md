# .
## Descrizione:
Create un nuovo progetto utilizzando Vite e Vue 3 e definite i componenti necessari per strutturare il layout come da screenshot allegato.
Al caricamento della pagina, effettuate una chiama ajax all'API di Yu Gi Oh: https://db.ygoprodeck.com/api/v7/cardinfo.php e con i dati restituiti, stampate una card per ogni carta.

- creazione progetto con Vite
- creazione componenti ( header, footer, main)
- in store.js variabile vuota `cards` per salvare dati chiamata axios
- in App.vue import di `store.js`
- in App.vue funzione `getCards` che fa chiamata axios a api e salva dati in `store.cards`
- in App.vue eseguire `getCards` in created()
- analizzare risposta con console log e salvare in `store.cards` soltanto la proprietà con le cards
- in AppMain.vue import di `store.js`
- v-for semplice di `store.cards` in AppMain.vue per vedere se ci sono dati (es: <div v-for="card in cards"> )
- usare un componente con props per le cards in AppMain.vue (es. <Cards v-for="(card, index) in cards" :item="card" />

**ATTENZIONE**: l'api restituisce tutti i risultati in un colpo solo. Per evitare attese e/o rallentamenti nelle richieste, potete diminuire il numero di risultati sfruttando i parametri *num* e *offset*

https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0

**Bonus:** 
Creare un componente loader da visualizzare fintantoché i risultati non sono pronti.

- creazione componente Loading
- in AppMain.vue v-if (cards sono meno di 20) -> Loading, v-else -> Card v-for

**Documentazione**: https://ygoprodeck.com/api-guide/



## Descrizione:
Continuate a lavorare nella stessa repo di ieri e aggiungete una select per filtrare i risultati in base all'archetipo.
Per le option della select degli archetype potete copiarle dai risultati di questo endpoint dell'api:
https://db.ygoprodeck.com/api/v7/archetypes.php

Quando l'utente seleziona un vlore dalla lista, viene effettuata una chiamata alle API con l'archetipo selezionato (usare solo $emit no store)

- creazione di componente AppSearch con select
- creazione di proprietà in store dei valori delle options
- creazione di proprietà in store del valore del select e binding con select
- v-for delle options in AppSearch
- evento @change su select con emit di un event custom
- importare componente in App.vue ( o AppMain )
- evento custom su AppSearch in App.vue che esegue funzione getCards
- modificare getCards che verifica del valore del select, se sì, modifica URL di chiamata axios





