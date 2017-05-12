---
title: "Metodo fill (Array) (JavaScript) | Microsoft Docs"
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
ms.assetid: 11526627-c0bb-4157-a8c4-0a039079b4a1
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Metodo fill (Array) (JavaScript)
Popola una matrice con un valore specificato.  
  
## Sintassi  
  
```  
arrayObj.fill(value [ , start [ , end ] ]);  
```  
  
#### Parametri  
 `arrayObj`  
 Obbligatorio.  Oggetto array.  
  
 `value`  
 Obbligatorio.  Valore usato per popolare la matrice.  
  
 `start`  
 Facoltativo.  Indice iniziale usato per popolare i valori della matrice.  Il valore predefinito è 0.  
  
 `end`  
 Facoltativo.  Indice finale usato per popolare i valori della matrice.  Il valore predefinito è la proprietà length dell'oggetto `this`.  
  
## Note  
 Se `start` è negativo, `start` viene gestito come `length`\+`start`, dove `length` è la lunghezza della matrice.  Se `end` è negativo, `end` viene considerato come `length`\+`end`.  
  
## Esempio  
 Gli esempi di codice seguenti popolano una matrice con valori.  
  
```javascript  
[0, 0, 0].fill(7, 1);  
// Array contains [0,7,7]  
  
[0, 0, 0].fill(7);  
// Array contains [7,7,7]  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]