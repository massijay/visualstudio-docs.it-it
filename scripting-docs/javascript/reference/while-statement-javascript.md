---
title: "Istruzione while (JavaScript) | Microsoft Docs"
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
  - "while_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "strutture di ciclo, istruzioni while"
  - "while (istruzione)"
ms.assetid: d63777cf-0e1a-4555-8d3a-334381001f48
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Istruzione while (JavaScript)
Esegue un'istruzione o una serie di istruzioni finché una condizione specificata non risulta `false`.  
  
## Sintassi  
  
```  
while (expression) {  
    statements  
}   
```  
  
## Parametri  
 `expression`  
 Necessario.  Espressione booleana che viene verificata prima di ciascuna iterazione del ciclo.  Se `expression` è `true`, il ciclo viene eseguito.  Se `expression` è `false`, il ciclo viene terminato.  
  
 `statements`  
 Opzionale.  Una o più istruzioni da eseguire se `expression` è `true`.  
  
## Note  
 L'istruzione `while` verifica `expression` precedentemente alla prima esecuzione del ciclo.  Se `expression` è `false` già alla prima iterazione, il ciclo non verrà mai eseguito.  
  
## Esempio  
 Nel codice seguente viene illustrato l'utilizzo dell'istruzione `while`.  
  
```javascript  
var i = 0;  
var j = 10;  
while (i < 100) {  
    if (i == j)  
        break;  
    i++;  
}  
document.write(i);  
  
// Output: 10  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Vedere anche  
 [Istruzione break](../../javascript/reference/break-statement-javascript.md)   
 [Istruzione continue](../../javascript/reference/continue-statement-javascript.md)   
 [Istruzione do...while](../../javascript/reference/do-dot-dot-dot-while-statement-javascript.md)   
 [Istruzione for](../../javascript/reference/for-statement-javascript.md)   
 [Istruzione for...in](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)