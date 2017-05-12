---
title: "Funzione Symbol.for (JavaScript) | Microsoft Docs"
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
ms.assetid: 27db15f3-9108-4892-8f89-e84031729cb6
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Funzione Symbol.for (JavaScript)
Restituisce il simbolo relativo a una chiave specificata o, se la chiave non è presente, crea un nuovo oggetto simbolo con la nuova chiave.  
  
## Sintassi  
  
```vb  
Symbol.for(key);  
```  
  
#### Parametri  
 `key`  
 Obbligatorio.  Chiave per il simbolo che viene usata anche come descrizione.  
  
## Note  
 Questo metodo cerca il simbolo nel registro dei simboli globali.  Se si serializzano i simboli sotto forma di stringhe, usare il registro dei simboli globali per assicurare il mapping di una particolare stringa al simbolo corretto per tutte le ricerche.  
  
## Esempio  
  
```javascript  
var sym = Symbol.for("desc");  
  
console.log(sym.toString());  
  
// Two different object references.  
console.log(Symbol("symbol") === Symbol.for("symbol");)  
// Single object reference.   
console.log(Symbol.for("symbol") === Symbol.for("symbol");)  
  
// Output:  
// Symbol(desc);  
// false  
// true  
```  
  
## Requisiti  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]