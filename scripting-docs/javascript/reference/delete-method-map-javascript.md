---
title: "Metodo delete (Map) (JavaScript) | Microsoft Docs"
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
ms.assetid: a073e1a1-5862-485b-b2bd-26c66a3aff51
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Metodo delete (Map) (JavaScript)
Rimuove l'elemento specificato da una mappa.  
  
## Sintassi  
  
```javascript  
mapObj.delete(key)  
```  
  
#### Parametri  
 `mapObj`  
 Necessario.  Un oggetto `Map`.  
  
 `key`  
 Necessario.  Chiave dell'elemento da rimuovere.  
  
## Valore proprietà\/Valore restituito  
 `true` se l'elemento è stato rimosso.  
  
## Esempio  
 Nell'esempio seguente viene illustrato come aggiungere membri a un oggetto `Map` e quindi eliminarne uno.  
  
```javascript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
m.set("colors", 2);  
m.delete(1);  
  
m.forEach(function (item) {  
    document.write(item.toString() + "<br />");  
});  
  
// Output:  
// red  
// 2  
```  
  
## Requisiti  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]