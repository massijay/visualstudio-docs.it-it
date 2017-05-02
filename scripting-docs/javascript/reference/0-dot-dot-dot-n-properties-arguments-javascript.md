---
title: "Propriet&#224; 0...n (arguments) (JavaScript) | Microsoft Docs"
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
  - "0...n"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "proprietà 0...n"
ms.assetid: 52857c4b-3d56-4500-93ff-4db4729c2578
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Propriet&#224; 0...n (arguments) (JavaScript)
Restituisce il valore effettivo di singoli argomenti da un oggetto **arguments** restituito dalla proprietà **arguments** di una funzione in esecuzione.  
  
## Sintassi  
  
```  
[function.]arguments[[0|1|2|...|n]]  
```  
  
## Parametri  
 *function*  
 Facoltativo.  Nome dell'oggetto `Function` attualmente in esecuzione.  
  
 0, 1, 2, *, n*  
 Obbligatorio.  Numero intero non negativo compreso nell'intervallo tra 0 e *n* dove 0 rappresenta il primo argomento e *n* quello finale.  Il valore dell'argomento finale *n* è **arguments.length\-1**.  
  
## Note  
 I valori restituiti dalle proprietà 0.  .  .  n sono i valori effettivi passati alla funzione in esecuzione.  Nonostante non sia effettivamente una matrice di argomenti, l'accesso ai singoli argomenti che comprendono l'oggetto **arguments** viene effettuato nello stesso modo in cui avviene l'accesso agli elementi di una matrice.  
  
## Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo delle proprietà **0. . .**  ***n*** dell'oggetto **arguments**.  Per comprendere totalmente l'esempio, passare alla funzione uno o più argomenti:  
  
```javascript  
function ArgTest(){  
   var s = "";  
   s += "The individual arguments are: "  
   for (n = 0; n < arguments.length; n++){  
      s += ArgTest.arguments[n];  
      s += " ";  
   }  
   return(s);  
}  
document.write(ArgTest(1, 2, "hello", new Date()));  
```  
  
## Requisiti  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Si applica a**: [Oggetto Arguments](../../javascript/reference/arguments-object-javascript.md)&#124; [Oggetto Function](../../javascript/reference/function-object-javascript.md)  
  
## Vedere anche  
 [Proprietà length \(arguments\)](../../javascript/reference/length-property-arguments-javascript.md)   
 [Proprietà length \(Function\)](../../javascript/reference/length-property-function-javascript.md)