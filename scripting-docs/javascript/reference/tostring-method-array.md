---
title: "Metodo toString (Array) | Microsoft Docs"
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
ms.assetid: 71fbea85-3e00-41b0-b167-25e4281e5e8a
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Metodo toString (Array)
Restituisce una rappresentazione in forma di stringa di una matrice.  
  
## Sintassi  
  
```  
  
array.toString()  
```  
  
## Parametri  
 `array`  
 Obbligatorio.  Matrice da rappresentare come stringa.  
  
## Valore restituito  
 Rappresentazione in forma di stringa della matrice.  
  
## Note  
 Gli elementi di un oggetto `Array` vengono convertiti in stringhe.  Le stringhe risultati sono concatenate e separate da virgole.  
  
## Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo del metodo **toString** con una matrice.  
  
```javascript  
var arr = [1, 2, 3, 4];  
var s = arr.toString();  
document.write(s);  
  
// Output: 1,2,3,4  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]