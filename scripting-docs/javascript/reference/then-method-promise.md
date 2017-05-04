---
title: "Metodo then (Promise) | Microsoft Docs"
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
ms.assetid: c7f3259d-78f7-4ca7-8bdf-99fbd3f41e8d
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Metodo then (Promise)
Consente di specificare il lavoro da eseguire in caso di evasione di una promessa.  
  
## Sintassi  
  
```  
  
promise.then(onCompleted, onRejected);  
```  
  
#### Parametri  
 `promise`  
 Obbligatorio.  Oggetto Promise.  
  
 `onCompleted`  
 Obbligatorio.  La funzione del gestore di evasione del metodo da eseguire quando la promessa viene completata correttamente.  
  
 `onRejected`  
 Facoltativo.  La funzione del gestore errori da eseguire quando l'oggetto Promise viene rifiutato.  
  
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
  
## Requisiti  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## Vedere anche  
 [Oggetto Promise](../../javascript/reference/promise-object-javascript.md)