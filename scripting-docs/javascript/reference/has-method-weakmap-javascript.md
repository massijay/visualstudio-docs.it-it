---
title: "Metodo has (WeakMap) (JavaScript) | Microsoft Docs"
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
ms.assetid: 12bedca1-bde7-413a-a4e2-06c03559044f
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Metodo has (WeakMap) (JavaScript)
Restituisce `true` se l'oggetto `WeakMap` contiene l'elemento specificato.  
  
## Sintassi  
  
```javascript  
weakmapObj.has(key)  
```  
  
#### Parametri  
 `weakmapObj`  
 Necessario.  Un oggetto `WeakMap`.  
  
 `key`  
 Necessario.  Chiave dell'elemento su cui eseguire il test.  
  
## Valore proprietà\/Valore restituito  
 `true` se `WeakMap` contiene la chiave specificata.  
  
## Esempio  
 Di seguito viene illustrato come aggiungere un membro a un'oggetto `WeakMap` e quindi utilizzare `has` per verificarne la presenza.  
  
```javascript  
var dog = {  
    breed: "yorkie"  
}  
  
var wm = new WeakMap();  
wm.set(dog, "fido");  
  
document.write(wm.has(dog));  
  
// Output:  
// true  
```  
  
## Requisiti  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]