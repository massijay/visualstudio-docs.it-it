---
title: "Metodo has (WeakSet) (JavaScript) | Microsoft Docs"
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
ms.assetid: e24f0876-26bd-4007-b12a-360bb6fa0951
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Metodo has (WeakSet) (JavaScript)
Restituisce `true` se `WeakSet` contiene l'elemento specificato.  
  
## Sintassi  
  
```javascript  
setObj.has(obj)  
```  
  
#### Parametri  
 `setObj`  
 Necessario.  Oggetto `WeakSet`.  
  
 `obj`  
 Necessario.  Elemento su cui eseguire il test.  
  
## Valore proprietà\/Valore restituito  
 `true` se il set contiene l'elemento specificato.  
  
## Esempio  
 L'esempio seguente mostra come aggiungere membri a un oggetto `WeakSet` e quindi verificare se il set contiene un membro specifico.  
  
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