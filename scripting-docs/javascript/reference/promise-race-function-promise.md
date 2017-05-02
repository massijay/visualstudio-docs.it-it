---
title: "Funzione Promise.race (Promise) | Microsoft Docs"
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
ms.assetid: 9236eced-d313-4d03-8c3e-d89d762b3084
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Funzione Promise.race (Promise)
Crea una nuova promessa che sarà risolta o rifiutata con lo stesso valore dei risultati della prima promessa da risolvere o rifiutare tra gli argomenti passati.  
  
## Sintassi  
  
```  
Promise.race(iterable)  
  
```  
  
#### Parametri  
 `iterable`  
 Obbligatorio.  Una o più promesse.  
  
## Note  
 Se una delle promesse in `iterable` è già in uno stato risolto o rifiutato, `Promise.race` restituisce una promessa risolta o rifiutata nello stesso modo con il valore dei risultati uguale al valore usato per risolvere \(o rifiutare\) la promessa.  Se più promesse in `iterable` sono già state risolte o rifiutate, `Promise.race` restituisce una promessa risolta nello stesso modo della prima promessa iterata.  Se nessuna promessa in iterable viene risolta o rifiutata, nemmeno la promessa restituita da `Promise.race` viene risolta o rifiutata.  
  
## Esempio  
  
```javascript  
var p1 = new Promise(function(resolve, reject) {  
    setTimeout(resolve, 0, 'success');  
});  
var p2 = new Promise(function(resolve, reject) { });  
var p2 = new Promise(function(resolve, reject) { });  
  
var race = Promise.race( [p1, p2, p3] );  
race.then(function(result) {  
    console.log(result);  
});  
  
// Output:  
// success  
  
var race = Promise.race( [Promise.reject('failure'),  
    Promise.resolve('success')] );  
race.catch(function(result) {  
    console.log(result);  
});  
  
// Output:  
// failure  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## Vedere anche  
 [Oggetto Promise](../../javascript/reference/promise-object-javascript.md)