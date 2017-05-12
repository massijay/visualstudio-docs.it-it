---
title: "Funzione Math.round (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "round"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Math (oggetto)"
  - "round (metodo)"
ms.assetid: 51008df3-5d0c-4951-84cb-4f41000db0be
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Funzione Math.round (JavaScript)
Restituisce un'espressione numerica specificata arrotondata al numero intero più vicino.  
  
## Sintassi  
  
```  
  
Math.round(  
number  
)   
```  
  
## Note  
 L'argomento `number` obbligatorio è il valore da arrotondare al numero intero più vicino.  
  
 Per i numeri positivi, se la parte decimale di `number` è maggiore o uguale a 0,5, il valore restituito è uguale all'intero più piccolo maggiore di `number`.  Se la parte decimale è minore di 0,5, il valore restituito corrisponderà all'intero più grande minore o uguale a `number`.  
  
 Per i numeri negativi, se la parte decimale equivale a \-0,5, il valore restituito corrisponderà all'intero più piccolo maggiore del numero.  
  
 `Math.round(8.5)`, ad esempio, restituisce 9, mentre `Math.round(-8.5)` restituisce \-8.  
  
## Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Si applica a**: [Oggetto Math](../../javascript/reference/math-object-javascript.md)  
  
## Vedere anche  
 [Funzione Math.random](../../javascript/reference/math-random-function-javascript.md)