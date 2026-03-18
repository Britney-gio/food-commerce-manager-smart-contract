# POF - Planty of Food Smart Contract - Start2Impact Project — Solidity Smart Contract

Smart contract sviluppato per gestire l’e-commerce decentralizzato dell’azienda **POF (Planty of Food)**, una piattaforma che promuove prodotti alimentari **plant-based sostenibili provenienti da produttori italiani**.

L'obiettivo del progetto è sviluppare uno smart contract che possa interagire con l’e-commerce dell’azienda e gestire l’intero processo di vendita.

Il cliente ha richiesto che lo smart contract permetta di:

- acquistare prodotti
- registrare automaticamente le vendite
- inviare recensioni dopo l’acquisto
- analizzare e tracciare il numero di vendite
- consultare lo storico degli acquisti per cliente

Inoltre il proprietario dello smart contract deve avere la possibilità esclusiva di:

- aggiungere nuovi prodotti allo store
- prelevare i fondi accumulati nello smart contract

---

## Smart Contract Deployment

Il contratto è stato deployato con successo sulla rete Ethereum **Sepolia Testnet** tramite Remix IDE.

**Network:** Sepolia Testnet  

**Contract Address:**  
`0x7A6EDDd49901334D0680f6985dBC2E34E1295F06`

**Link Etherscan:**
https://sepolia.etherscan.io/address/0x7A6EDDd49901334D0680f6985dBC2E34E1295F06

**Transaction Hash:**  
`0x366...aa765`

---

# Realizzazione del progetto

Il progetto è stato sviluppato utilizzando **Solidity** tramite l'editor **Remix IDE**, dove sono stati eseguiti:

- scrittura del codice
- compilazione
- test
- debug
- deploy su testnet

---

# Architettura del progetto

Il progetto è suddiviso in **tre file principali**.

---

## FoodCommerceManager.sol

Questo file contiene due contratti:

### Ownable

Contratto che gestisce la **logica di proprietà** dello smart contract.  
Al momento del deploy viene registrato automaticamente l'indirizzo dell'amministratore.

Questo consente di limitare alcune funzioni solo al proprietario del contratto.

---

### FoodCommerceManager

Contratto principale che implementa tutta la logica dell’e-commerce.

Il contratto è organizzato in tre sezioni principali seguendo un ordine preciso.

---

### 1. Funzioni amministrative (solo owner)

**withdraw()**

Permette all'amministratore di prelevare i fondi presenti nello smart contract, dopo aver verificato che il saldo sia sufficiente.

**addProduct()**

Permette all'amministratore di aggiungere nuovi prodotti allo store, effettuando controlli sui dati inseriti e salvandoli nell'array dei prodotti.

---

### 2. Funzioni di lettura

**getProduct()**

Permette a qualsiasi utente di ottenere le informazioni di un prodotto tramite il suo identificativo `idProduct`.

**getSale()**

Restituisce le informazioni di una vendita tramite `idSale`.

**getPurchasesByBuyer()**

Permette di recuperare tutte le vendite effettuate da uno specifico indirizzo Ethereum.

**getTotalSalesInPeriod()**

Calcola il totale degli ETH incassati dal contratto in un determinato intervallo temporale.

---

### 3. Funzioni core del progetto

**buyProduct()**

Permette ad un utente di acquistare uno o più prodotti inviando ETH.  
La funzione esegue diversi controlli e registra la vendita nello smart contract.

Durante l'acquisto viene inoltre emesso l'evento `Purchase`.

**rateSale()**

Permette al buyer che ha effettuato l'acquisto di lasciare una valutazione dell'esperienza.

Una vendita può essere valutata **una sola volta** e solo dal buyer che l'ha effettuata.

---

Le funzioni insieme permettono la gestione completa di:

- prodotti
- acquisti
- pagamenti
- recensioni
- analisi delle vendite

---

## FoodCommerceTypes.sol

Library che contiene la **struct condivisa `Sale`**.

Questa scelta è stata adottata per evitare duplicazione di codice tra contratti e migliorare la modularità del progetto.

La struct `Sale` contiene:

- idSale
- idProduct
- nameProduct
- amountSold
- totalPaid
- purchaseTimestamp
- buyer
- rating

---

## FoodCommerceLibrary.sol

Library contenente funzioni di utilità utilizzate dal contratto principale.

### getPurchaseByBuyer()
### getTotalSalesInPeriod()

---

# Scelte tecniche

## Uso delle struct

Le struct sono utilizzate per rappresentare dati complessi.

Nel progetto sono utilizzate per memorizzare:

- prodotti
- vendite

Questo permette di raggruppare più informazioni correlate in una singola struttura.

---

## Uso di array e mapping

Nel progetto vengono utilizzate entrambe le strutture dati.

### Array
- Product[] products
- Sale[] sales


Gli array permettono di:

- iterare sugli elementi
- effettuare controlli sui dati
- gestire liste dinamiche

---

### Mapping
`mapping(uint => Sale) salesMap`

Il mapping permette di accedere rapidamente ad una vendita tramite il suo identificativo `idSale`, evitando di scorrere tutto l'array.

L'utilizzo combinato di **array + mapping** permette di ottenere sia:

- iterazione efficiente
- accesso diretto ai dati

---

## Eventi

Il progetto utilizza l'evento:

**Purchase**

Questo evento viene emesso ogni volta che viene effettuato un acquisto.

Gli eventi permettono di:

- tracciare le operazioni on-chain
- integrare facilmente il contratto con frontend o servizi off-chain.

---

## Modifier

Sono stati utilizzati modifier per migliorare la sicurezza del contratto.

**onlyOwner()**

Limita alcune funzioni all'amministratore dello smart contract.

**hasSufficientFunds()**

Verifica che il contratto abbia fondi sufficienti prima di permettere un prelievo.

---

# Autore

Sviluppato da **Giorgia Nieli**
<p>
(https://github.com/Britney-gio/food-commerce-manager-smart-contract/blob/main/gn-logo.jpg)
</p>

Email  
giorgianieli@gmail.com

LinkedIn  
https://www.linkedin.com/in/giorgia-nieli-98b0882b0/
