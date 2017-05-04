---
title: "Istruzione for (JavaScript) | Microsoft Docs"
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
  - "for_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "cicli (strutture), istruzioni for"
ms.assetid: bae0ec40-152e-43f3-969b-3696489ec5c4
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# Istruzione for (JavaScript)
Esegue un blocco di istruzioni fino a quando una condizione specificata non risulta true.  
  
## Sintassi  
  
```  
for ([initialization]; [test]; [increment])  
   statement   
```  
  
## Parametri  
 `initialization`  
 Facoltativo.  Espressione.  Viene eseguita una sola volta prima dell'esecuzione del ciclo.  
  
 `test`  
 Facoltativo.  Espressione booleana.  Se `test` è `true`, `statement` viene eseguito.  Se `test` è `false`, il ciclo viene terminato.  
  
 `increment`  
 Facoltativo.  Espressione.  L'espressione di incremento viene eseguita al termine di ciascuna iterazione.  
  
 `statement`  
 Facoltativo.  Una o più istruzioni da eseguire se `test` è **true**.  Può trattarsi di un'istruzione composta.  
  
## Note  
 Un ciclo `for` viene in genere utilizzato quando è noto il numero di cicli da eseguire.  Un ciclo `for` è utile per scorrere le matrici ed eseguire l'elaborazione sequenziale.  
  
 Poiché il test di un'espressione condizionale avviene prima dell'esecuzione del ciclo, un'istruzione `for` viene eseguita zero o più volte.  
  
 In qualsiasi riga di un blocco di istruzioni del ciclo `for` è possibile utilizzare l'istruzione `break` per uscire dal ciclo oppure l'istruzione `continue` per trasferire il controllo alla successiva iterazione del ciclo.  
  
## Esempio  
 Nell'esempio seguente l'istruzione `for` esegue le istruzioni incluse nel modo seguente:  
  
-   Innanzitutto, viene valutato il valore iniziale della variabile `i`.  
  
-   Quindi, fino a quando il valore di `i` è minore o uguale a 9, vengono eseguite le istruzioni `document.write` e viene rivalutato `i`.  
  
-   Quando `i` è maggiore di 9, la condizione diventa false e il controllo viene trasferito al di fuori del ciclo.  
  
```javascript  
// i is set to 0 at the start and is incremented by 1 at the  
// end of each iteration.  
// The loop terminates when i is not less than or equal to  
// 9 before a loop iteration.  
for (var i = 0; i <= 9; i++) {  
   document.write (i);  
   document.write (" ");  
}  
  
// Output: 0 1 2 3 4 5 6 7 8 9  
```  
  
## Esempio  
 Tutte le espressioni dell'istruzione `for` sono facoltative.  Nell'esempio seguente le istruzioni `for` creano un ciclo infinito e viene utilizzata un'istruzione `break` per uscire dal ciclo.  
  
```javascript  
var j = 0;  
for (;;) {  
    if (j >= 5) {  
        break;  
    }  
    j++;  
    document.write (j + " ");  
}  
  
// Output: 1 2 3 4 5  
```  
  
## Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Vedere anche  
 [Istruzione for...in](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)   
 [Istruzione while](../../javascript/reference/while-statement-javascript.md)