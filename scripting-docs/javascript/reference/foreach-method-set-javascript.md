---
title: "Metodo forEach (Set) (JavaScript) | Microsoft Docs"
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
ms.assetid: 813bff6e-6098-4260-ab6e-b0d2da6be94d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Metodo forEach (Set) (JavaScript)
Esegue l'azione specificata per ciascun elemento in un set.  
  
## Sintassi  
  
```javascript  
setObj.forEach(callbackfn[, thisArg])  
```  
  
#### Parametri  
 `setObj`  
 Necessario.  Un oggetto `Set`.  
  
 `callbackfn`  
 Necessario.  `callbackfn` accetta fino a tre argomenti.  Funzione che `forEach` chiama una volta per ogni elemento nel set.  
  
 `thisArg`  
 Opzionale.  Un oggetto a cui la parola chiave `this` può fare riferimento nella funzione `callbackfn`.  Se `thisArg` viene omesso, si utilizza `undefined` come valore `this`.  
  
## Eccezioni  
 Se l'argomento `callbackfn` non è un oggetto funzione, viene generata un'eccezione `TypeError`.  
  
## Note  
 La sintassi della funzione di callback è la seguente:  
  
 `function callbackfn(value, key, setObj)`  
  
 È possibile dichiarare la funzione di callback tramite un massimo di tre parametri, come illustrato nella tabella seguente.  
  
|Argomento di callback|Definizione|  
|---------------------------|-----------------|  
|`value`|Un valore contenuto nel set.|  
|`key`|Un valore contenuto nel set.  Un set non ha chiavi, quindi questo è uguale a `value`.|  
|`setObj`|L'oggetto `Set` da attraversare.|  
  
## Esempio  
 Nell'esempio riportato di seguito viene illustrato l'utilizzo di `forEach`.  L'argomento `callbackfn` include il codice per la funzione di callback.  
  
```javascript  
var s = new Set();  
  
s.add("scale");  
s.add(10);  
s.add("5");  
  
s.forEach(function(item, sameItem, s) {  
    document.write("Size of the set object is: " + s.size + "<br />");  
    document.write("Deleting item: " + item + "<br />");  
    s.delete(sameItem);  
});  
  
// Output:  
// Size of the set object is: 3  
// Deleting item: scale  
// Size of the set object is: 2  
// Deleting item: 10  
// Size of the set object is: 1  
// Deleting item: 5  
```  
  
## Esempio  
 Nell'esempio seguente viene illustrato che è possibile recuperare i membri da un set passando un solo parametro alla funzione di callback.  
  
```javascript  
var s = new Set();  
s.add("Thomas Jefferson");  
s.add(1776);  
s.add("founding father");  
  
s.forEach(function (item) {  
    document.write(item.toString() + ", ");  
});  
  
// Output:  
// Thomas Jefferson, 1776, founding father,  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]