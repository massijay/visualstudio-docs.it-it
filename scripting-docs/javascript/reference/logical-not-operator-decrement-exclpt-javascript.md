---
title: "Operatore di NOT logico (!) (JavaScript) | Microsoft Docs"
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
  - "!"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "! operatore"
  - "! operatore, informazioni sull'operatore !"
  - "Operatore NOT logico"
ms.assetid: 68c3dc71-ae95-4293-9155-67405846d71d
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Operatore di NOT logico (!) (JavaScript)
Esegue una negazione logica in un'espressione.  
  
## Sintassi  
  
```  
  
result = !expression  
```  
  
## Parametri  
 *result*  
 Qualsiasi variabile.  
  
 *expression*  
 Qualsiasi espressione.  
  
## Note  
 Nella tabella seguente viene illustrata la modalità di determinazione di *result*.  
  
|Se `expression` è|`result` sarà|  
|-----------------------|-------------------|  
|True|False|  
|False|True|  
  
 Con tutti gli operatori unari, quale l'operatore **\!**, le espressioni vengono valutate nel modo seguente:  
  
-   Se l'operatore viene applicato a espressioni undefined o `null`, verrà generato un errore di runtime.  
  
-   Gli oggetti vengono convertiti in stringhe.  
  
-   Le stringhe vengono convertite in numeri se possibile.  In caso contrario, verrà generato un errore di runtime.  
  
-   I valori booleani vengono considerati come numeri e precisamente come 0 nel caso di false, come 1 nel caso di true.  
  
 L'operatore viene applicato al numero risultante.  
  
 Nel caso dell'operatore **\!**, se *expression* è diverso da zero, *result* sarà uguale a zero.  Se invece *expression* è uguale a zero, il valore di *result* sarà 1.  
  
## Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Vedere anche  
 [Operatore NOT bit per bit \(~\)](../../javascript/reference/bitwise-not-operator-decrement-tilde-javascript.md)   
 [Precedenza tra gli operatori](../../javascript/operator-subtractprecedence-javascript.md)   
 [Riepilogo degli operatori \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)