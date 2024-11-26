**Cataldo Nicholas Montini Mattia Varricchio Lorenzo**

---
# Documentazione del Progetto Pokémon


- **Introduzione**
- **Struttura del progetto**
- **Spiegazione API e del localStorage**
- **Gestione su Trello**
- **Spiegazione codice**
- **Conclusioni**

---

## Introduzione

l progetto mira a sviluppare un Pokédex interattivo utilizzando HTML, CSS e JavaScript, insieme all'integrazione della PokeAPI. 
L'applicazione permette agli utenti di:
- **Esplorazione Completa del Pokédex:** Gli utenti possono navigare attraverso una lista completa di oltre 1000 Pokémon, visualizzando informazioni dettagliate su tipi, abilità, statistiche ed evoluzioni. 
Ogni Pokémon è presentato con immagini animate e dati aggiornati.
- **Mini-Gioco di Cattura Interattiva:** Abbiamo implementato un mini-gioco che simula la cattura di Pokémon selvatici. 
Gli utenti possono scegliere tra diversi ambienti, come terra e acqua, e tentare di catturare Pokémon utilizzando meccaniche di gioco basate su probabilità.
- **Gestione della Lista Personale di Pokémon:** Una volta catturati, i Pokémon vengono aggiunti a una lista personale, dove gli utenti possono visualizzare i propri Pokémon, accedere a dettagli aggiuntivi e persino liberare Pokémon per fare spazio a nuove catture.

L'obiettivo principale è offrire un'esperienza coinvolgente che combina l'esplorazione del mondo dei Pokémon con conoscenze da noi acquisite, progetto mirato a creare un'applicazione che non sia solo funzionale, ma anche e soprattutto divertente. 


---

## Struttura del Progetto

Il progetto è organizzato in diversi file HTML, CSS, JavaScript e immagini. 
Di seguito, una panoramica della struttura dei file e delle loro funzionalità principali:


### File HTML e JavaScript

1. **`index.html`**

 - **Descrizione:** Funziona come la pagina principale dell'applicazione, offrendo       un'interfaccia in stile Pokédex che accoglie l'utente e lo indirizza alle diverse funzionalità disponibili.
- **Navigazione Principale:** La pagina contiene tre pulsanti principali: Gioca, Lista Personale e Pokémon Totali, che reindirizzano rispettivamente alle pagine GiocaPokemon.html, PersonalList.html e PokemonTotali.html.
- **Estetica:** L'interfaccia è progettata per richiamare l'aspetto di un vero Pokédex, con elementi grafici e stili che riflettono il mondo dei Pokémon.
- **Stile**:
  - Utilizza **Tailwind CSS** e **DaisyUI** per il design.
  - Include font e immagini per richiamare l'estetica dei Pokémon.

2. **`GiocaPokemon.html`**

   - **Descrizione**: Pagina dedicata al mini-gioco di cattura dei Pokémon.
   - **Funzionalità**:
     - Permette all'utente di muovere un personaggio (Scooby-Doo), utilizzando i tasti direzionali o i tasti WASD,
     in un ambiente con dei pokémon rappresentati dai dei tag.
     - Offre la possibilità di scegliere tra due ambienti: **Terra** o **Acqua**.
     - Quando l'utente interagisce con un pokémon, viene reindirizzato alla pagina battaglia.html.
   - **Stile**:
     - l'ambiente e Scooby cambiano in base al tema selezionato.
     - Utilizza un canvas per gestire il movimento e l'interazione.

3. **`Battaglia.html`**

   - **Descrizione**: Simula l'incontro con un Pokémon selvatico.
   - **Funzionalità**:
     - Visualizza un Pokémon casuale, se trovato nell'ambiente dell'acqua potrà essere solo di tipo acqua.
     - L'utente può scegliere di **catturare** o **scappare**.
     - Implementata una logica di cattura basata su **probabilità (20%) e tentativi limitati (5)**.
     - I Pokémon catturati vengono salvati nel **localStorage** e visualizzati poi lista personale.
   - **Stile**:
     - Presenti animazioni e transizioni.
     - Utilizzate immagini come la Pokéball e reazioni del personaggio.

4. **`PersonalList.html`**

   - **Descrizione**: Mostra la lista dei Pokémon catturati dall'utente.
   - **Funzionalità**:
     - Recupera i dati dei Pokémon dal **localStorage**.
     - Permette di visualizzare le caratteristiche di ciascun Pokémon.
     - Carica e visualizza tutti i Pokémon con immagini (animate se presenti) e nomi.
     - Consente all'utente di **liberare** un Pokémon.
   - **Stile**:
     - Presenta una griglia di card per ogni Pokémon.
     - Include un popup per i dettagli approfonditi.

5. **`PokemonTotali.html`**

   - **Descrizione**: Elenca tutti i Pokémon disponibili tramite la PokeAPI.
   - **Funzionalità**:
     - Carica e visualizza tutti i Pokémon con immagini (animate se presenti) e nomi.
     - Permette di visualizzare le caratteristiche di ciascun Pokémon.

---

## Spiegazione delle API

Il progetto utilizza la **PokeAPI** per recuperare informazioni dettagliate sui Pokémon, come tipi, abilità, statistiche ed evoluzioni.

**Una fetch** È un API utilizzata per effettuare richieste http e recuperare risorse da un server, accetta due parametri, URL a cui inviare la richiesta (obbligatorio) e le opzioni da impostare nella richiesta come il metodo di richiesta qui (facoltativo).
In realtà la fetch() restituisce a Promise, quindi necessario aggiungere i metodi .then() e .catch(), se la richiesta restituisce una risposta .then() verrà chiamato, se restituisce un errore eseguito catch


### Esempio di Utilizzo della PokeAPI

Per ottenere i dettagli di un Pokémon specifico:

```javascript
fetch(`https://pokeapi.co/api/v2/pokemon/${pokemonId}`)
  .then(response => response.json())
  .then(data => {
    // Utilizzo dei dati del Pokémon
    console.log(data);
  })
  .catch(error => console.error("Errore nel recupero dei dettagli Pokémon:", error));
```

### Funzionalità Implementate con le API

- **Recupero della Lista Completa dei Pokémon**:
  - `https://pokeapi.co/api/v2/pokemon?limit=1302`
  - Utilizzato per popolare la pagina `PokemonTotali.html`.

- **Dettagli Specifici di un Pokémon**:
  - `https://pokeapi.co/api/v2/pokemon/{id}`
  - Fornisce informazioni su sprite, tipi, abilità e statistiche.

- **Informazioni sulle Evoluzioni**:
  -`https://pokeapi.co/api/v2/pokemon-species/{id}`
  - Utilizzato per determinare le evoluzioni di un Pokémon nella pagina dei dettagli.

- **Filtraggio per Tipo di Pokémon**:
  - `https://pokeapi.co/api/v2/type/{type}`
  - Implementato in `GiocaPokemon.html` per filtrare i Pokémon in base al tema selezionato.

## Spiegazione del localStorage
Il `localStorage` è utilizzato per salvare informazioni persistenti lato client, come la lista dei Pokémon catturati dall'utente e le preferenze del tema.
Questo approccio evita la necessità di un backend server e semplifica l'architettura dell'applicazione, rendendola completamente lato client.


### Esempio di Utilizzo del localStorage

Per ottenere i dettagli di un Pokémon specifico:

```javascript
function salvaNumero(numero) {
  // Verifica se il numero fornito è valido
  if (isNaN(numero) || numero === null || numero === undefined) {
      console.error("Il valore fornito non è un numero valido.");
      return;
  }
  // Recupera l'array esistente di Pokémon catturati dal localStorage
  let listaCatturati = JSON.parse(localStorage.getItem("ListaCatturati"));
  // Se non esiste ancora l'array, inizializzalo come vuoto
  if (!Array.isArray(listaCatturati)) {
      listaCatturati = [];
  }
  // Verifica se il numero del Pokémon è già presente nell'array
  if (listaCatturati.includes(numero)) {
      console.log("Questo Pokémon è già stato catturato.");
      return;  // Esce senza fare nulla se il Pokémon è già stato catturato
  }
  // Aggiungi il numero del Pokémon all'array
  listaCatturati.push(numero);
  // Salva l'array aggiornato nel localStorage
  localStorage.setItem("ListaCatturati", JSON.stringify(listaCatturati));
  console.log("Numero salvato con successo!");
}
```
Funzione utilizzata in `GiocaPokemon.html` per salvare il numero del Pokémon catturato nel localStorage.


---
## Gestione del Progetto su Trello

Per organizzare e monitorare lo sviluppo del progetto e tenere traccia dei vari test svolti, abbiamo utilizzato l'applicazione **Trello**.

### Vantaggi dell'Uso di Trello

- **Pianificazione delle Attività**:
  - Creazione di **liste** per suddividere il lavoro in fasi come "Da Fare", "In Corso" e "Completato".
  - Assegnazione di **card** specifiche per ogni funzionalità o componente da sviluppare.

- **Collaborazione**:
  - Possibilità di assegnare task a membri del team.
  - Comunicazione e condivisione di feedback direttamente sulle card.

- **Monitoraggio dei Test e Debugging**:
  - Tracciamento dei bug e delle problematiche riscontrate.
  - Pianificazione dei test necessari appunto per testare il codice.

- **Documentazione e Risorse**:
  - Salvataggio di link utili, documenti di riferimento e note direttamente nelle card.

---
## Spiegazione del codice
- `index.html`
```html
<body>
    <div class="pokedex-container">
        <!-- Flexbox per Logo e Titolo in alto -->
        <div class="header-container">
            <img src="immagini/pokemon-logo.png" alt="Pokemon Logo" class="pokemon-logo">
            <h1 class="outlined-text">Pokédex</h1>
        </div>

        <!-- Contenitore dei bottoni all'interno del Pokedex -->
        <div class="button-container">
            <!--Bottone che ti permette di andare sulla pagina GiocaPokemon.html-->
            <a href="GiocaPokemon.html">
                <button
                    class="btn rounded-lg w-64 mx-auto outlined-text py-4 px-6 transition-transform duration-200 hover:scale-110">GIOCA</button>
            </a>
            <!--Bottone che ti permette di andare sulla pagina PersonalList.html-->
            <a href="PersonalList.html">
                <button
                    class="btn rounded-lg w-64 mx-auto outlined-text py-4 px-6 transition-transform duration-200 hover:scale-110">LISTA
                    PERSONALE</button>
            </a>
            <!--Bottone che ti permette di andare sulla pagina PokemonTotali.html-->
            <a href="PokemonTotali.html">
                <button
                    class="btn rounded-lg w-64 mx-auto outlined-text py-4 px-6 transition-transform duration-200 hover:scale-110">POKEMON
                    TOTALI</button>
            </a>
        </div>
    </div>
</body>
```
Presenti diversi bottoni utilizzati per reindirizzamento sulle altre pagine.

- `PokemonTotali.html`
```javascript
function showDetails(pokemon) {
            pokemonName.textContent = pokemon.name.charAt(0).toUpperCase() + pokemon.name.slice(1);

            // Prende lo sprite dinamico se esiste se no usa quello statico.
            const animatedSpriteUrl = pokemon.sprites.versions["generation-v"]["black-white"].animated.front_default;
            const staticSpriteUrl = pokemon.sprites.front_default;
            pokemonImage.src = animatedSpriteUrl ? animatedSpriteUrl : staticSpriteUrl;

            // Visualizza il tipo, l'ID  e le statistiche del Pokémon
            pokemonType.textContent = `Tipo: ${pokemon.types.map(type => type.type.name).join(', ')} ; id: ${pokemon.id}`;
            pokemonAbilities.textContent = `Abilità: ${pokemon.abilities.map(ability => ability.ability.name).join(', ')}`;
            pokemonStats.textContent = 'Stats: ' + pokemon.stats.map(stat => `${stat.stat.name}: ${stat.base_stat}`).join(', ');

            // Recupera i dati di evoluzione del Pokémon
            fetch(`https://pokeapi.co/api/v2/pokemon-species/${pokemon.id}`)
                .then(response => response.json())
                .then(speciesData => {
                    if (speciesData.evolves_from_species) {
                        pokemonEvolution.textContent = `Si evolve da: ${speciesData.evolves_from_species.name}`;
                    } else {
                        pokemonEvolution.textContent = 'Questa è la prima evoluzione.';
                    }
                })
                .catch(error => console.error("Errore nel recupero dei dati di evoluzione:", error));
            detailsPopup.style.display = 'flex'; // Mostra il popup
        }
```
Quando l'utente clicca sulla card di un Pokémon, la funzione `showDetails(pokemon)` viene chiamata per mostrare un popup con dettagli aggiuntivi. Qui vengono visualizzati il tipo, le abilità, le statistiche e l'evoluzione (se disponibile). Se il Pokémon ha una forma evolutiva, l'API fornisce il nome dell'evoluzione precedente.

- `Battaglia.html`

Questa funzione `getFilteredPokemon` ha lo scopo di ottenere una lista di Pokémon filtrati in base al tema selezionato (in particolare, se il tema è "acqua" o meno).
La funzione è dichiarata come **async**, il che significa che può contenere operazioni asincrone, come richieste HTTP. Questo permette di usare **await** per attendere il completamento delle richieste prima di proseguire con l'esecuzione del codice.
```javascript 
async function getFilteredPokemon(){...}
```
  1. Viene creato un array contenente tutti i pokémon.

  ```javascript 
const allPokemonIds = Array.from({ length: 1025 }, (_, i) => i + 1);
```
  2. Verifica se il tema selezionato è **acqua**.
  ```javascript 
if (temaSelezionato === "acqua") {...}
```
  
  3. Se il tema è **acqua** la funzione esegue una richiesta HTTP alla PokeAPI per ottenere i Pokémon di tipo water e poi ritorna l'array.
  ```javascript 
const waterPokemon = await fetch("https://pokeapi.co/api/v2/type/water")
    .then((response) => response.json())  // Ottieni i dati dalla PokeAPI
    .then((data) => data.pokemon.map((p) => parseInt(p.pokemon.url.split("/").filter(Boolean).pop())));  // Estrai gli ID dei Pokémon di tipo acqua
```
```javascript 
return waterPokemon;  // Ritorna solo i Pokémon d'acqua
```
  4. Se il tema non è acqua, crea un array escludendo i pokémon di tipo water e ritorna l'array.
  ```javascript 
else {
    const waterPokemon = await fetch("https://pokeapi.co/api/v2/type/water")
        .then((response) => response.json())  // Ottieni i dati della PokeAPI
        .then((data) => data.pokemon.map((p) => parseInt(p.pokemon.url.split("/").filter(Boolean).pop())));  // Estrai gli ID dei Pokémon di tipo acqua
    return allPokemonIds.filter((id) => !waterPokemon.includes(id));  // Ritorna solo i Pokémon che non sono di tipo acqua
}
```
```javascript 
return allPokemonIds.filter((id) => !waterPokemon.includes(id));  // Ritorna solo i Pokémon che non sono di tipo acqua
```
---

Funzione `fetchAndDisplayPokemon` ha lo scopo di ottenere un Pokémon casuale (in base a un filtro precedentemente definito), recuperare i dettagli del Pokémon, e visualizzarne l'immagine. Inoltre, calcola la posizione centrale dell'immagine del pokémon

1. La funzione getFilteredPokemon() viene chiamata per ottenere una lista di ID di Pokémon filtrati, restituisce un array di Pokémon che soddisfano il tema selezionato.
```javascript 
const availablePokemon = await getFilteredPokemon();  // Ottieni i Pokémon disponibili in base al tema
```

2. Questa riga seleziona un ID di un Pokémon in modo casuale tra quelli disponibili (cioè tra gli ID restituiti dalla funzione `getFilteredPokemon`).
```javascript 
randomPokemonId = availablePokemon[Math.floor(Math.random() * availablePokemon.length)];  // Seleziona un Pokémon casuale
```
3. Dopo aver selezionato un ID casuale, la funzione fetch effettua una richiesta HTTP alla PokeAPI per ottenere i dettagli del Pokémon. L'URL della richiesta è dinamico e contiene l'ID del Pokémon selezionato (randomPokemonId).

```javascript
fetch(`https://pokeapi.co/api/v2/pokemon/${randomPokemonId}`)
    .then((response) => response.json())  // Recupera i dettagli del Pokémon
    .then((data) => {
        ...
    })
``` 
4. Recuperata sia l'immagine statica che quella animata, Se l'immagine animata (`animatedSpriteUrl`) è disponibile, verrà usata. Se non lo è (vale a dire, se animatedSpriteUrl è undefined o null), verrà usata l'immagine statica (`staticSpriteUrl`)

```javascript
const animatedSpriteUrl = data.sprites.versions["generation-v"]["black-white"].animated.front_default;  // URL dell'immagine animata, se disponibile
const staticSpriteUrl = data.sprites.front_default;  // URL dell'immagine statica
const pokemonImageUrl = animatedSpriteUrl || staticSpriteUrl;  // Usa l'immagine animata se disponibile, altrimenti usa quella statica
```

5. La funzione logPokemonCenter calcola il centro dell'immagine del Pokémon, usando il metodo `getBoundingClientRect()` per ottenere le dimensioni e la posizione dell'immagine sulla pagina.
```javascript
function logPokemonCenter() {
    const rect = pokemonImage.getBoundingClientRect();  // Ottieni la posizione e le dimensioni dell'immagine
    pokemonCenterX = rect.left + rect.width / 2;  // Calcola la coordinata X del centro
    pokemonCenterY = rect.top + rect.height / 2;  // Calcola la coordinata Y del centro
    console.log(`Centro del Pokémon: X = ${pokemonCenterX}, Y = ${pokemonCenterY}`);
}
```

---

## Conclusioni

Il progetto del Pokédex interattivo ha permesso di:

- **Sviluppare Competenze Tecniche**:
  - Approfondimento nell'uso di **JavaScript** avanzato e delle chiamate **fetch**.
  - Integrazione di **API esterne** per arricchire l'applicazione con dati reali.


- **Organizzare il Lavoro in Team**:
  - Utilizzo efficace di **Trello** per la gestione del progetto.
  - Miglioramento della comunicazione e della collaborazione tra i membri.

Il risultato finale è un'applicazione web che offre agli utenti la possibilità di vivere il mondo pokémon con un tocco di creatività e in maniera divertente.

---

**NICHOLAS CATALDO MONTINI MATTIA VARRICCHIO LORENZO**





