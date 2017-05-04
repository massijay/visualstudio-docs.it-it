---
title: "Operatore NOT bit per bit (~) (JavaScript) | Microsoft Docs"
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
  - "~"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "bit per bit (operatori), NOT (operatore)"
  - "NOT (operatore)"
ms.assetid: 39f92474-fe05-4a8b-9ad8-caca93f82bca
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Operatore NOT bit per bit (~) (JavaScript)
Esegue un'operazione NOT \(negazione\) bit per bit su un'espressione.  
  
## Sintassi  
  
```  
  
result = ~ expression  
```  
  
## Parametri  
 *result*  
 Qualsiasi variabile.  
  
 *expression*  
 Qualsiasi espressione.  
  
## Note  
 Con tutti gli operatori unari, quale l'operatore `~`, le espressioni vengono valutate nel modo seguente:  
  
-   Se l'operatore viene applicato a espressioni undefined o `null`, verrà generato un errore di runtime.  
  
-   Gli oggetti vengono convertiti in stringhe.  
  
-   Le stringhe vengono convertite in numeri se possibile.  In caso contrario, verrà generato un errore di runtime.  
  
-   I valori booleani vengono considerati come numeri e precisamente come 0 nel caso di false, come 1 nel caso di true.  
  
 L'operatore viene applicato al numero risultante.  
  
 L'operatore `~` esamina la rappresentazione binaria dei valori dell'espressione ed esegue un'operazione di negazione bit per bit.  
  
 Le cifre pari a 1 nell'espressione diventano 0 nel risultato.  Le cifre pari a 0 nell'espressione diventano 1 nel risultato.  
  
 Nell'esempio seguente viene illustrato l'utilizzo dell'operatore NOT \(~\) bit per bit.  
  
```  
var temp = ~5;  
```  
  
 Il valore risultante è \-6, come illustrato nella tabella seguente.  
  
|Espressione|Valore binario \(complemento a due\)|Valore decimale|  
|-----------------|------------------------------------------|---------------------|  
|5|00000000 00000000 00000000 00000101|5|  
|~5|11111111 11111111 11111111 11111010|\-6|  
  
## Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Vedere anche  
 [Operatore di NOT logico \(\!\)](../../javascript/reference/logical-not-operator-decrement-exclpt-javascript.md)   
 [Precedenza tra gli operatori](../../javascript/operator-subtractprecedence-javascript.md)   
 [Riepilogo degli operatori \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)