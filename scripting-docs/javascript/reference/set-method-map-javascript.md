---
title: "Metodo set (Map) (JavaScript) | Microsoft Docs"
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
ms.assetid: 31ee71a0-b09d-442a-9e02-825accf94ffa
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Metodo set (Map) (JavaScript)
Aggiunge un nuovo elemento a una mappa.  
  
## Sintassi  
  
```javascript  
mapObj.set(key, value)  
```  
  
#### Parametri  
 `mapObj`  
 Necessario.  Oggetto `Map`.  
  
 `key`  
 Necessario.  Chiave per il nuovo elemento.  
  
 `value`  
 Necessario.  Valore dell'elemento da aggiungere.  
  
## Valore proprietà\/Valore restituito  
 Restituisce l'oggetto `Map` che contiene la nuova coppia chiave\/valore.  
  
## Note  
 Se si aggiunge un valore alla raccolta utilizzando una chiave esistente, il nuovo valore sostituisce quello vecchio.  
  
## Esempio  
 Nell'esempio seguente viene illustrato come aggiungere membri a un oggetto `Map` e quindi recuperarli.  
  
```javascript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
m.set("colors", 2);  
  
m.forEach(function (item) {  
    document.write(item.toString() + "<br />");  
});  
  
// Output:  
// black  
// red  
// 2  
```  
  
## Requisiti  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]