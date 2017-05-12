---
title: "Funzione Object.assign (Object) (JavaScript) | Microsoft Docs"
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
ms.assetid: 2dd6b312-dcd3-414e-8d53-088c6341c46d
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Funzione Object.assign (Object) (JavaScript)
Copia i valori da uno o più oggetti di origine in un oggetto di destinazione.  
  
## Sintassi  
  
```  
Object.assign(target, ...sources );  
```  
  
#### Parametri  
 `target`  
 Obbligatorio.  Oggetto in cui vengono copiate le proprietà enumerabili.  
  
 `...sources`  
 Obbligatorio.  Uno o più oggetti da cui vengono copiate le proprietà enumerabili.  
  
## Eccezioni  
 Questa funzione genera un `TypeError` se si verifica un errore di assegnazione, che termina l'operazione di copia.  Se una proprietà di destinazione non è scrivibile, verrà generato un `TypeError`.  
  
## Note  
 Questa funzione restituisce l'oggetto di destinazione.  Solo le proprietà *propriamente enumerabili* vengono copiate dall'oggetto di origine a quello di destinazione.  È possibile usare questa funzione per unire o clonare oggetti.  
  
 Le origini `null` o `undefined` vengono considerate come oggetti vuoti e non forniscono alcun contributo all'oggetto di destinazione.  
  
## Esempio  
 L'esempio di codice seguente illustra come unire un oggetto tramite `Object.assign`.  
  
```javascript  
var first = { name: "Bob" };  
var last = { lastName: "Smith" };  
  
var person = Object.assign(first, last);  
console.log(person);  
  
// Output:  
// { name: "Bob", lastName: "Smith" }   
```  
  
## Esempio  
 L'esempio seguente illustra come clonare un oggetto tramite `Object.assign`.  
  
```javascript  
var obj = { person: "Bob Smith"};  
var clone = Object.assign({}, obj);  
```  
  
## Requisiti  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]