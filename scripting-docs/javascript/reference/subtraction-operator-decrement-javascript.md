---
title: "Operatore di sottrazione (-) (JavaScript) | Microsoft Docs"
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
  - "-"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "- (operatore)"
  - "- (operatore), informazioni sull'operatore -"
  - "aritmetici (operatori), sottrazione"
  - "negazione (operatore)"
  - "operatori, sottrazione"
  - "sottrazione (operatore), sintassi"
ms.assetid: cd0681d3-15cd-49fe-b4dd-e087de55d778
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Operatore di sottrazione (-) (JavaScript)
Esegue la sottrazione tra i valori di due espressioni o fornisce la negazione unaria di una singola espressione.  
  
## Sintassi  
  
```  
  
result = number1 - number2;  
  
```  
  
## Parametri  
 *result*  
 Qualsiasi variabile numerica.  
  
 `number`  
 Qualsiasi espressione numerica.  
  
 `number1`  
 Qualsiasi espressione numerica.  
  
 `number2`  
 Qualsiasi espressione numerica.  
  
## Note  
 Nella sintassi 1 l'operatore **\-** è l'operatore di sottrazione aritmetica utilizzato per il calcolo della differenza tra due valori numerici.  Nella sintassi 2 l'operatore **\-** viene utilizzato come operatore di negazione unario per indicare il valore negativo di un'espressione.  
  
 Nella sintassi 2, come per tutti gli operatori unari, le espressioni vengono valutate nel modo seguente:  
  
-   Se l'operatore viene applicato a espressioni undefined o `null`, verrà generato un errore di runtime.  
  
-   Gli oggetti vengono convertiti in stringhe.  
  
-   Le stringhe vengono convertite in numeri se possibile.  In caso contrario, verrà generato un errore di runtime.  
  
-   I valori booleani vengono considerati come numeri e precisamente come 0 nel caso di false, come 1 nel caso di true.  
  
 L'operatore viene applicato al numero risultante.  Nella sintassi 2, se il numero risultante è diverso da zero, *result* sarà uguale al numero risultante con segno inverso.  Se invece è zero, *result* sarà zero.  
  
## Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Vedere anche  
 [Operatore di assegnazione di sottrazione \(\-\=\)](../../javascript/reference/subtraction-assignment-operator-decrement-equal-javascript.md)   
 [Precedenza tra gli operatori](../../javascript/operator-subtractprecedence-javascript.md)   
 [Riepilogo degli operatori \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)