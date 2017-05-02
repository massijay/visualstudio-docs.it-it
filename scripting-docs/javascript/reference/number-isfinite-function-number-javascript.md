---
title: "funzione Number.isFinite (Number) (JavaScript) | Microsoft Docs"
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
ms.assetid: 41a91408-09d1-49f2-b7a0-6da105e2ed8e
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# funzione Number.isFinite (Number) (JavaScript)
Restituisce un valore booleano che indica se un valore è un numero finito.  
  
## Sintassi  
  
```  
Number.isFinite(numValue)   
```  
  
## Valore restituito  
 `false` se il valore è `NaN`, `+∞`, o `-∞`; in caso contrario, `true`.  
  
## Note  
  
## Esempio  
  
```javascript  
// Returns true  
Number.isFinite(100)  
Number.isFinite(-100)  
Number.isFinite(100 / 3)  
  
// Returns false  
Number.isFinite(Number.NaN)  
Number.isFinite(Infinity)  
Number.isFinite("100")  
```  
  
## Requisiti  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
 **Si applica a** : [Oggetto Number](../../javascript/reference/number-object-javascript.md)