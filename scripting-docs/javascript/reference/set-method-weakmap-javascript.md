---
title: "Metodo set (WeakMap) (JavaScript) | Microsoft Docs"
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
ms.assetid: 29fc72b1-224f-4f19-8c06-5d926d695b03
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Metodo set (WeakMap) (JavaScript)
Aggiunge un nuovo elemento a un oggetto `WeakMap`.  
  
## Sintassi  
  
```javascript  
weakmapObj.set(key, value)  
```  
  
#### Parametri  
 `weakmapObj`  
 Necessario.  Oggetto `WeakMap`.  
  
 `key`  
 Necessario.  Oggetto che rappresenta la chiave dell'elemento da aggiungere.  Deve essere un riferimento a un oggetto.  
  
 `value`  
 Necessario.  Valore dell'elemento da aggiungere.  
  
## Valore proprietà\/Valore restituito  
 Restituisce l'oggetto `WeakMap` che contiene la nuova coppia chiave\/valore.  
  
## Note  
 Se si aggiunge un valore alla raccolta utilizzando una chiave esistente, il nuovo valore sostituisce quello vecchio.  
  
## Esempio  
 Nell'esempio seguente viene illustrato come aggiungere membri a un oggetto `WeakMap`.  
  
```javascript  
var dog = {  
    breed: "yorkie"  
}  
  
var cat = {  
    breed: "burmese"  
}  
  
var wm = new WeakMap();  
wm.set(dog, "fido");  
wm.set(cat, "pepper");  
```  
  
## Requisiti  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]