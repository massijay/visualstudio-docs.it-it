---
title: "Funzione Math.imul (JavaScript) | Microsoft Docs"
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
ms.assetid: dce5e11c-36b9-4c39-84d3-6cd494dd1cbf
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Funzione Math.imul (JavaScript)
Restituisce il prodotto di due numeri che vengono considerati come valori integer firmati a 32 bit.  
  
## Sintassi  
  
```  
Math.imul(x, y);  
```  
  
#### Parametri  
 `x`  
 Obbligatorio.  Primo numero.  
  
 `y`  
 Obbligatorio.  Secondo numero.  
  
## Note  
 Questa funzione viene usata per i compilatori come Emscripten e Mandreel, che non implementano la moltiplicazione di valori integer nello stesso modo di JavaScript.  
  
## Esempio  
 L'esempio di codice seguente illustra come moltiplicare numeri tramite `Math.imul`.  
  
```javascript  
var result1 = Math.imul(2, 5);  
// result1 == 10  
  
var result2 = Math.imul(Math.pow(2, 32) - 1, Math.pow(2, 32) - 2);  
// result2 == 2  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]