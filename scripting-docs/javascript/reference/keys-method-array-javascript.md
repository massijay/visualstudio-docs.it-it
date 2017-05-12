---
title: "Metodo keys (matrice) (JavaScript) | Microsoft Docs"
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
ms.assetid: fc5b6a30-642c-4bd7-ad31-a42667af2f3f
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Metodo keys (matrice) (JavaScript)
Restituisce un iteratore che contiene i valori di indice della matrice.  
  
## Sintassi  
  
```  
arrayObj.keys();  
```  
  
#### Parametri  
 `arrayObj`  
 Obbligatorio.  Oggetto array.  
  
## Note  
  
## Esempio  
 L'esempio seguente mostra come ottenere i valori di chiave di una matrice.  
  
```javascript  
var k = ["a", "b", "c"].keys();  
// k.next().value == 0  
// k.next().value == 1  
// k.next().value == 2   
```  
  
## Requisiti  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]