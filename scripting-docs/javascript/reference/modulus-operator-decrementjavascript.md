---
title: "Operatore modulo (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "%"
dev_langs: 
  - "JavaScript"
  - "DHTML"
helpviewer_keywords: 
  - "operatore modulo, JavaScript"
  - "% (operatore) [JavaScript]"
  - "Modulo (funzione) [JavaScript]"
ms.assetid: 087d654f-623b-498d-95ff-596d26bf674d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Operatore modulo (JavaScript)
Esegue la divisione tra i valori di due espressioni restituendo il resto.  
  
## Sintassi  
  
```  
  
result = number1 % number2  
```  
  
## Argomenti  
 `result`  
 Qualsiasi variabile.  
  
 `number1`  
 Qualsiasi espressione numerica.  
  
 `number2`  
 Qualsiasi espressione numerica.  
  
## Note  
 L'operatore modulo, o resto, divide l'argomento `number1` per l'argomento `number2` e restituisce il resto come `result`.  Il segno di `result` è uguale a quello di `number1`.  Il valore di `result` è compreso tra 0 e il valore assoluto di `number2`.  
  
 Nel codice seguente viene illustrato come utilizzare l'operatore modulo.  
  
```  
var modResult = 19 % 6.7;  
document.write(modResult);  
  
// Output: 5.6  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Vedere anche  
 [Precedenza tra gli operatori](../../javascript/operator-subtractprecedence-javascript.md)   
 [Riepilogo degli operatori \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)