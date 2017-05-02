---
title: "Operatori di incremento (++) e decremento (--) (JavaScript) | Microsoft Docs"
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
  - "--"
  - "++"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "operatori di incremento, sintassi"
  - "++ (operatore)"
  - "++ (operatore), informazioni"
  - "operatori di decremento, sintassi"
  - "-- (operatore)"
ms.assetid: 49eaf4cf-8818-478d-a429-cdd2ece20811
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Operatori di incremento (++) e decremento (--) (JavaScript)
L'operatore di incremento incrementa il valore di una variabile di uno, mentre l'operatore di decremento decrementa il valore di uno.  
  
## Sintassi  
  
```  
  
      result = ++variable  
result = --variable  
result = variable++  
result = variable--  
```  
  
## Parametri  
 `result`  
 Qualsiasi variabile.  
  
 `variable`  
 Qualsiasi variabile.  
  
## Note  
 Se l'operatore compare prima della variabile, il valore viene modificato prima che l'espressione venga valutata.  Se l'operatore compare dopo la variabile, il valore viene modificato dopo che l'espressione è stata valutata.  In altre parole, dato `j = ++k;`, il valore di `j` è il valore originale di `k` più uno; dato `j = k++;`, il valore di `j` è il valore originale di `k`, che viene incrementato dopo che il relativo valore viene assegnato a `j`.  
  
## Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Vedere anche  
 [Precedenza tra gli operatori](../../javascript/operator-subtractprecedence-javascript.md)   
 [Riepilogo degli operatori \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)