---
title: "Metodo get (WeakMap) (JavaScript) | Microsoft Docs"
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
ms.assetid: d922c55d-486d-4feb-aedc-1f4867c417d2
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Metodo get (WeakMap) (JavaScript)
Restituisce un elemento specificato da un oggetto `WeakMap`.  
  
## Sintassi  
  
```javascript  
weakmapObj.get(key)  
```  
  
#### Parametri  
 `weakmapObj`  
 Necessario.  Un oggetto `WeakMap`.  
  
 `key`  
 Necessario.  Chiave di un elemento in `WeakMap`.  
  
## Valore proprietà\/Valore restituito  
 Restituisce l'oggetto associato alla chiave.  Se `WeakMap` non contiene la chiave, questo metodo restituisce un valore `undefined`.  
  
## Esempio  
 Nell'esempio seguente viene illustrato come recuperare i membri da un oggetto `WeakMap`.  
  
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
  
document.write(wm.get(dog) + ": ");  
document.write(dog.breed);  
document.write("<br />");  
document.write(wm.get(cat) + ": ");  
document.write(cat.breed);  
  
// Output:  
// fido: yorkie  
// pepper: burmese  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]