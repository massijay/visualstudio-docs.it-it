---
title: "Metodo add (WeakSet) (JavaScript) | Microsoft Docs"
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
ms.assetid: d35d0287-6b33-4720-b9d7-8954c428ce4e
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Metodo add (WeakSet) (JavaScript)
Aggiunge un nuovo elemento a un oggetto `WeakSet`.  
  
## Sintassi  
  
```javascript  
weaksetObj.add(obj)  
```  
  
#### Parametri  
 `weaksetObj`  
 Necessario.  Oggetto `WeakSet`.  
  
 `obj`  
 Necessario.  Nuovo elemento dell'oggetto `WeakSet`.  
  
## Note  
 Il nuovo elemento deve essere un oggetto, anziché un valore arbitrario, e deve essere univoco.  Se si aggiunge un elemento non univoco a `WeakSet`, il nuovo elemento non verrà aggiunto alla raccolta.  
  
## Esempio  
 L'esempio seguente mostra come aggiungere membri a un set e verificare che siano stati aggiunti.  
  
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