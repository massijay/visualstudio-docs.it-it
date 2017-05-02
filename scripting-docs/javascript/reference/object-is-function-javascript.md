---
title: "Funzione Object.is (JavaScript) | Microsoft Docs"
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
ms.assetid: 6e2f6c6d-7cd2-47c4-a513-3ba53988d27d
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Funzione Object.is (JavaScript)
Restituisce un valore che indica se due valori sono uguali.  
  
## Sintassi  
  
```javascript  
Object.is(value1, value2)  
```  
  
#### Parametri  
 `value1`  
 Obbligatorio.  Primo valore da testare.  
  
 `value2`  
 Obbligatorio.  Secondo valore da testare.  
  
## Valore restituito  
 `true` se il valore è uguale; in caso contrario, `false`.  
  
## Note  
 Diversamente dall'operatore \=\=, `Object.is` non forza l'impostazione di alcun tipo durante il test dei valori.  
  
 Il confronto applicato da `Object.is` è simile a quello applicato dall'operatore \=\=\=, con la differenza che `Object.is` considera `Number.isNaN` un valore uguale a `NaN`.  Inoltre considera \+0 e \-0 come valori diversi.  
  
## Requisiti  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]