---
title: "Funzione Math.clz32 (JavaScript) | Microsoft Docs"
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
ms.assetid: 34615d7a-6d88-4ab5-a696-7e496caa51db
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Funzione Math.clz32 (JavaScript)
Restituisce il numero di bit zero iniziali nella rappresentazione binaria a 32 bit di un numero.  
  
## Sintassi  
  
```  
  
Math.clz32(  
number  
)   
```  
  
## Note  
 Se `number` è 0, il risultato è 32.  Se il bit più significativo della codifica binaria a 32 bit di `number` è 1, il risultato è 0.  
  
## Requisiti  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
 **Si applica a**: [Oggetto Math](../../javascript/reference/math-object-javascript.md)