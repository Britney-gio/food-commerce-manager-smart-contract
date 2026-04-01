# POF - Planty of Food Smart Contract

Smart contract sviluppato in **Solidity** per gestire un e-commerce decentralizzato di prodotti alimentari **plant-based sostenibili**, provenienti da produttori italiani.

L’obiettivo del progetto è simulare un sistema di vendita completo on-chain, gestendo acquisti, vendite e analisi dati direttamente su blockchain.

---

## Funzionalità principali

### Per gli utenti

- Acquisto prodotti in ETH
- Registrazione automatica delle vendite
- Possibilità di lasciare recensioni
- Consultazione storico acquisti
- Analisi vendite per periodo

### Per l’amministratore

- Aggiunta nuovi prodotti
- Prelievo fondi dal contratto

---

## 🔗 Deploy

**Network:** Sepolia Testnet

**Contract Address:**  
`0xe7e78586E33C4F02c749324238B1163BC61bBAc0`

**Hash Transazione:**
0xea26df11a124092a6c7eeeb0b7179c762212044e732f43e86c4a6b8a228a2a10

**Etherscan:**  
https://sepolia.etherscan.io/address/0xe7e78586E33C4F02c749324238B1163BC61bBAc0

---

## Architettura

Il progetto è suddiviso in tre file principali:

### FoodCommerceManager.sol.txt

Contiene la logica principale dello smart contract.

Include:

- gestione prodotti
- gestione vendite
- acquisti
- sistema di rating
- controllo amministratore (Ownable)

---

### FoodCommerceTypes.sol.txt

Contiene la struct condivisa:

- `Sale`

Serve a migliorare modularità e riutilizzo del codice.

---

### FoodCommerceLibrary.sol.txt

Contiene funzioni di supporto:

- `getPurchasesByBuyer()`
- `getTotalSalesInPeriod()`

Utilizzata per filtrare e analizzare i dati delle vendite.

---

## Tecnologie utilizzate

- Solidity ^0.8.x
- Remix IDE
- MetaMask
- Sepolia Testnet

---

## Flusso del sistema

1. L’amministratore aggiunge prodotti
2. L’utente acquista inviando ETH
3. Il contratto registra la vendita (`salesMap`)
4. Viene emesso un evento `Purchase`
5. L’utente può lasciare una recensione
6. I dati possono essere analizzati tramite funzioni dedicate

---

## Miglioramenti apportati

- Sostituito `.transfer` con `.call` per maggiore sicurezza
- Eliminata duplicazione dati tra array e mapping
- `salesMap` utilizzato come unica fonte di verità

---

## Note

Progetto sviluppato durante il percorso **Blockchain Development** con Start2Impact.

---

# Autore

Sviluppato da **Giorgia Nieli**

Email  
giorgianieli@gmail.com

LinkedIn  
https://www.linkedin.com/in/giorgia-nieli-98b0882b0/
