---
title: "Metodo delete (WeakMap) (JavaScript) | Microsoft Docs"
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
ms.assetid: 7d54ae55-e514-45ba-b403-d1eee46837d2
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Metodo delete (WeakMap) (JavaScript)
Rimuove l'elemento specificato da un oggetto `WeakMap`.  
  
## Sintassi  
  
```javascript  
weakmapObj.delete(key)  
```  
  
#### Parametri  
 `weakmapObj`  
 Necessario.  Un oggetto `WeakMap`.  
  
 `key`  
 Necessario.  Chiave dell'elemento da rimuovere.  
  
## Valore proprietà\/Valore restituito  
 `true` se l'elemento è stato rimosso.  
  
## Esempio  
 Nell'esempio seguente viene illustrato come aggiungere un membro a un oggetto `WeakMap` e quindi eliminarlo.  
  
```javascript  
function Dog(breed) {  
    this.breed = breed;  
}  
  
var dog = new Dog("yorkie");  
  
var wm = new WeakMap();  
wm.set(dog, "fido");  
wm.delete(dog);  
```  
  
## Requisiti  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]