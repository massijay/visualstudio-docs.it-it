---
title: "Funzione Object.getOwnPropertySymbols (JavaScript) | Microsoft Docs"
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
ms.assetid: 68dd69b9-5a33-44c2-ba5f-21a4ae6c0879
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Funzione Object.getOwnPropertySymbols (JavaScript)
Restituisce le proprietà di simboli propri di un oggetto.  Le proprietà di simboli propri di un oggetto sono le proprietà definite direttamente sull'oggetto stesso e non ereditate dal prototipo dell'oggetto.  
  
## Sintassi  
  
```  
Object.getOwnPropertySymbols(object);  
```  
  
#### Parametri  
 `object`  
 Obbligatorio.  Oggetto che contiene i simboli propri.  
  
## Valore restituito  
 Matrice che contiene i simboli propri dell'oggetto.  
  
## Note  
 Per ottenere le proprietà dei simboli di un oggetto, sarà necessario usare `Object.getOwnPropertySymbols`.  `Object.getOwnPropertyNames` non restituirà le proprietà dei simboli.  
  
## Esempio  
 L'esempio di codice seguente illustra come ottenere le proprietà dei simboli di un oggetto.  
  
```javascript  
var obj = {};  
var key = Symbol('description');  
  
obj[key] = 'data';  
  
var symbols = Object.getOwnPropertySymbols(obj);  
  
console.log(s[0].toString());  
  
// Output:  
// undefined  
// Symbol(description)  
```  
  
## Requisiti  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]