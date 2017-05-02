---
title: "Oggetto Promise (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 358ad98b-f7fa-448c-9ee0-ef1e2a45e9c6
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Oggetto Promise (JavaScript)
Fornisce un meccanismo per pianificare il lavoro da eseguire su un valore che non è stato calcolato.  È un'astrazione per la gestione delle interazioni con le API asincrone.  
  
## Sintassi  
  
```  
var promise = new Promise(function(resolve, reject) { ... });  
```  
  
#### Parametri  
 `promise`  
 Obbligatorio.  Nome della variabile a cui l'oggetto promise è assegnato.  
  
 `resolve`  
 Obbligatorio.  Funzione eseguita per indicare che la promessa è stata completata.  
  
 `reject`  
 Facoltativo.  Funzione eseguita per indicare che la promessa è stata rifiutata con un errore.  
  
## Note  
 Una promessa deve essere completata con un valore o rifiutata con un motivo.  Il metodo `then` dell'oggetto Promise viene eseguito quando la promessa viene completata o rifiutata, a seconda dell'evento che si verifica per primo.  Se la promessa viene completata correttamente, viene eseguita la funzione del gestore di evasione del metodo `then`.  Se la promessa viene rifiutata, viene eseguita la funzione del gestore errori del metodo `then` o del metodo `catch`.  
  
## Esempio  
 L'esempio seguente mostra come chiamare una funzione \(`timeout`\) che restituisce una promessa.  Il gestore di evasione del metodo `then` viene eseguito dopo la scadenza di un intervallo di timeout di 5000 ms.  
  
```javascript  
function timeout(duration) {  
    return new Promise(function(resolve, reject) {  
        setTimeout(resolve, duration);  
    });  
}  
  
// Note: This code uses arrow function syntax  
var m = timeout(5000).then(() => {  
    console.log("done!");  
})  
  
// Output (after 5 seconds):  
// done!  
```  
  
## Esempio  
 È anche possibile concatenare le chiamate al metodo `then` come illustrato nel codice seguente.  Per supportare il concatenamento, ogni gestore di completamento deve restituire una promessa.  In questo codice, che chiama la stessa funzione `timeout`, la prima chiamata a timeout viene restituita dopo 1000 ms.  Il primo gestore di completamento chiama di nuovo `timeout` e questa promessa viene restituita dopo 2000 ms.  Il relativo gestore di completamento genera quindi un errore.  Il gestore errori chiama `Promise.all`, che viene restituita solo quando entrambe le chiamate a timeout sono state completate o rifiutate.  
  
```javascript  
var p = timeout(1000).then(() => {  
    return timeout(2000);  
}).then(() => {  
    throw new Error("error");  
}).catch(err => {  
    return Promise.all([timeout(100), timeout(200)]);  
})  
```  
  
## Requisiti  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## Funzioni  
 La tabella seguente illustra le funzioni dell'oggetto `Promise`.  
  
|Funzione|Descrizione|  
|--------------|-----------------|  
|[Funzione Promise.all](../../javascript/reference/promise-all-function-promise.md)|Unisce due o più promesse e viene restituita solo quando tutte le promesse specificate sono state completate o rifiutate.|  
|[Funzione Promise.race](../../javascript/reference/promise-race-function-promise.md)|Crea una nuova promessa che sarà risolta o rifiutata con lo stesso valore dei risultati della prima promessa da risolvere o rifiutare tra gli argomenti passati.|  
|[Funzione Promise.reject](../../javascript/reference/promise-reject-function-promise.md)|Crea una nuova promessa rifiutata con un risultato uguale all'argomento passato.|  
|[Funzione Promise.resolve](../../javascript/reference/promise-resolve-function-promise.md)|Crea una nuova promessa risolta con un risultato uguale al relativo argomento.|  
  
## Metodi  
 La tabella seguente illustra le funzioni dell'oggetto `Promise`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[Metodo catch](../../javascript/reference/catch-method-promise.md)|Consente di specificare il lavoro da eseguire in caso di rifiuto di una promessa.|  
|[Metodo then](../../javascript/reference/then-method-promise.md)|Consente di specificare il lavoro da eseguire in caso di evasione di una promessa.|