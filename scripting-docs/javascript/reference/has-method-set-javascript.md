---
title: "Metodo has (Set) (JavaScript) | Microsoft Docs"
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
ms.assetid: fb80f2e0-fc5e-4508-af14-1c3b3b833636
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Metodo has (Set) (JavaScript)
Restituisce `true` se il set contiene l'elemento specificato.  
  
## Sintassi  
  
```javascript  
setObj.has(value)  
```  
  
#### Parametri  
 `setObj`  
 Necessario.  Un oggetto `Set`.  
  
 `value`  
 Necessario.  Elemento su cui eseguire il test.  
  
## Valore proprietà\/Valore restituito  
 `true` se il set contiene l'elemento specificato.  
  
## Esempio  
 Di seguito viene illustrato come aggiungere dei membri a un'oggetto `Set` e quindi controllare se il set contiene un membro specifico.  
  
```javascript  
var s = new Set();  
s.add("Thomas Jefferson");  
s.add(1776);  
  
document.write(s.has(1776));  
document.write(s.has("1776"));  
  
// Output:  
// true  
// false  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]