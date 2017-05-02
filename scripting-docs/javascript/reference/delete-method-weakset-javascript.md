---
title: "Metodo delete (WeakSet) (JavaScript) | Microsoft Docs"
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
ms.assetid: 19e93366-7d42-4abf-b7b9-fcf943fa17a3
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Metodo delete (WeakSet) (JavaScript)
Rimuove l'elemento specificato da un oggetto `WeakSet`.  
  
## Sintassi  
  
```javascript  
weaksetObj.delete(obj)  
```  
  
#### Parametri  
 `weaksetObj`  
 Obbligatorio.  Oggetto `WeakSet`.  
  
 `obj`  
 Obbligatorio.  Elemento da rimuovere.  
  
## Valore proprietà\/Valore restituito  
 `true` se l'elemento è stato rimosso.  
  
## Esempio  
 Nell'esempio seguente viene illustrato come aggiungere ed eliminare elementi di un oggetto `WeakSet`.  
  
```javascript  
var ws = new WeakSet();  
  
var str = new String("Thomas Jefferson");  
var num = new Number(1776);  
  
ws.add(str);  
ws.add(num);  
  
console.log(ws.has(str));  
console.log(ws.has(num));  
  
ws.delete(str);  
console.log(ws.has(str));  
  
// Output:  
// true  
// true  
// false  
```  
  
## Requisiti  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]