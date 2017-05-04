---
title: "Istruzione break (JavaScript) | Microsoft Docs"
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
  - "break_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "break (istruzione)"
  - "do...while (istruzione)"
ms.assetid: 5be0f2a8-5fe7-4a6c-89af-ca20a925ce87
caps.latest.revision: 23
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 23
---
# Istruzione break (JavaScript)
Interrompe il ciclo corrente o, se utilizzata insieme a `label`, l'istruzione associata.  
  
## Sintassi  
  
```  
break [label];  
```  
  
## Note  
 L'argomento `label` facoltativo specifica l'etichetta dell'istruzione interrotta.  
  
 L'istruzione `break` viene in genere utilizzata in istruzioni `switch` e in cicli `while`, `for`, `for...in` o `do...while`.  L'argomento `label` viene più comunemente utilizzato in istruzioni `switch`, ma può essere utilizzato in qualsiasi istruzione, sia semplice sia composita.  
  
 L'esecuzione dell'istruzione `break` chiude il ciclo o l'istruzione corrente e avvia l'esecuzione degli script con l'istruzione immediatamente successiva.  
  
## Esempi  
 In questo esempio il contatore viene configurato per il conteggio da 1 a 99. L'istruzione `break`, tuttavia, termina il ciclo dopo 14 conteggi.  
  
```javascript  
for (var i = 1; i < 100; i++) {  
    if (i == 15) {  
        break;  
    }  
    document.write (i);  
    document.write (" ");  
}  
  
// Output: 1234567891011121314  
```  
  
 Nel codice seguente l'istruzione `break` fa riferimento al ciclo `for` preceduto dall'istruzione `Inner:`.  Quando `j` è uguale a 24, l'istruzione `break` provoca l'uscita del flusso di programma dal ciclo.  I numeri compresi tra 21 e 23 vengono stampati su ogni riga.  
  
```javascript  
Outer:  
for (var i = 1; i <= 10; i++) {  
    document.write ("<br />");  
    document.write ("i: " + i);  
    document.write (" j: ");  
Inner:  
    for (var j = 21; j <= 30; j++) {  
        if (j == 24) {  
            break Inner;  
        }  
        document.write (j + " ");  
    }  
}  
  
// Output:   
// i: 1 j: 21 22 23   
// i: 2 j: 21 22 23   
// i: 3 j: 21 22 23   
// i: 4 j: 21 22 23   
// i: 5 j: 21 22 23   
// i: 6 j: 21 22 23   
// i: 7 j: 21 22 23   
// i: 8 j: 21 22 23   
// i: 9 j: 21 22 23   
// i: 10 j: 21 22 23  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Vedere anche  
 [Istruzione continue](../../javascript/reference/continue-statement-javascript.md)   
 [Istruzione do...while](../../javascript/reference/do-dot-dot-dot-while-statement-javascript.md)   
 [Istruzione for](../../javascript/reference/for-statement-javascript.md)   
 [Istruzione for...in](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)   
 [Istruzione con etichetta](../../javascript/reference/labeled-statement-javascript.md)   
 [Istruzione while](../../javascript/reference/while-statement-javascript.md)