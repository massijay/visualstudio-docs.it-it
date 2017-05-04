---
title: "Metodo get (Map) (JavaScript) | Microsoft Docs"
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
ms.assetid: bebbd6bc-6e61-4674-8196-7e907798973f
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Metodo get (Map) (JavaScript)
Restituisce un elemento specificato da una mappa.  
  
## Sintassi  
  
```javascript  
mapObj.get(key)  
```  
  
#### Parametri  
 `mapObj`  
 Necessario.  Un oggetto `Map`.  
  
 `key`  
 Necessario.  Chiave di un elemento in `Map`.  
  
## Valore proprietà\/Valore restituito  
 Restituisce l'oggetto associato alla chiave.  Se `Map` non contiene la chiave, questo metodo restituisce un valore `undefined`.  
  
## Esempio  
 Nell'esempio seguente viene illustrato come recuperare un elemento da un oggetto `Map`.  
  
```javascript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
m.set("colors", 2);  
  
document.write(m.get(2));  
  
// Output:  
// red  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]