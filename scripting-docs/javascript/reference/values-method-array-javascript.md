---
title: "Metodo values (Array) (JavaScript) | Microsoft Docs"
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
ms.assetid: b20699d6-f8b1-4744-8551-9e81c82850dd
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Metodo values (Array) (JavaScript)
Restituisce un iteratore che contiene i valori della matrice.  
  
## Sintassi  
  
```  
arrayObj.values();  
```  
  
#### Parametri  
 `arrayObj`  
 Obbligatorio.  Oggetto array.  
  
## Note  
  
## Esempio  
 Nell'esempio seguente viene illustrato come ottenere i valori in una matrice.  
  
```javascript  
var v = ["a", "b", "c"].values();  
// v.next().value == "a"  
// v.next().value == "b"  
// v.next().value == "c"   
```  
  
## Requisiti  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]