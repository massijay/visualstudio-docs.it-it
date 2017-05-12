---
title: "Metodo forEach (Map) (JavaScript) | Microsoft Docs"
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
ms.assetid: 9cdf0adc-77c7-4407-8ba7-ada0fb09e507
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Metodo forEach (Map) (JavaScript)
Esegue l'azione specificata per ciascun elemento in una mappa.  
  
## Sintassi  
  
```javascript  
mapObj.forEach(callbackfn[, thisArg])  
```  
  
#### Parametri  
 `mapObj`  
 Necessario.  Un oggetto `Map`.  
  
 `callbackfn`  
 Necessario.  Funzione che `forEach` chiama una volta per ogni elemento nella mappa.  `callbackfn` accetta fino a tre argomenti.  `forEach` chiama la funzione `callbackfn` una volta per ogni elemento nella mappa.  
  
 `thisArg`  
 Opzionale.  Un oggetto a cui la parola chiave `this` può fare riferimento nella funzione `callbackfn`.  Se `thisArg` viene omesso, si utilizza `undefined` come valore `this`.  
  
## Eccezioni  
 Se l'argomento `callbackfn` non è un oggetto funzione, viene generata un'eccezione `TypeError`.  
  
## Note  
 La sintassi della funzione di callback è la seguente:  
  
 `function callbackfn(value, key, mapObj)`  
  
 È possibile dichiarare la funzione di callback tramite un massimo di tre parametri, come illustrato nella tabella seguente.  
  
|Argomento di callback|Definizione|  
|---------------------------|-----------------|  
|`value`|Un valore contenuto nella mappa.|  
|`key`|Chiave contenuta nella mappa.|  
|`mapObj`|L'oggetto `Map` da attraversare.|  
  
## Esempio  
 Nell'esempio seguente viene illustrato come recuperare i membri di un oggetto `Map` utilizzando `forEach`.  
  
```javascript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
m.set("colors", 2);  
m.set({x:1}, 3);  
  
m.forEach(function (item, key, mapObj) {  
    document.write(item.toString() + "<br />");  
});  
  
document.write("<br />");  
document.write(m.get(2));  
  
// Output:  
// black  
// red  
// 2  
// 3  
//  
// red  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]