---
title: "Metodo delete (Set) (JavaScript) | Microsoft Docs"
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
ms.assetid: 052c409e-10c9-49f2-955d-5ad7e31c14f3
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Metodo delete (Set) (JavaScript)
Rimuove l'elemento specificato da un set.  
  
## Sintassi  
  
```javascript  
setObj.delete(value)  
```  
  
#### Parametri  
 `setObj`  
 Necessario.  Un oggetto `Set`.  
  
 `value`  
 Necessario.  Elemento da rimuovere.  
  
## Valore proprietà\/Valore restituito  
 `true` se l'elemento è stato rimosso.  
  
## Esempio  
 Nell'esempio seguente viene illustrato come aggiungere dei membri a un oggetto `Set` e quindi eliminarne uno.  
  
```javascript  
var s = new Set();  
s.add("Thomas Jefferson");  
s.add(1776);  
s.add("founding father");  
s.delete("founding father");  
  
s.forEach(function (item) {  
    document.write(item.toString() + ", ");  
});  
  
// Output:  
// Thomas Jefferson, 1776,  
```  
  
## Requisiti  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]