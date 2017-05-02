---
title: "Istruzione continue (JavaScript) | Microsoft Docs"
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
  - "continue_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "continue (istruzione)"
  - "do...while (istruzione)"
  - "cicli (strutture), continue (istruzione)"
ms.assetid: f8a30d9f-e2de-4e1f-8668-4e4cf95f7df9
caps.latest.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 21
---
# Istruzione continue (JavaScript)
Arresta l'iterazione corrente di un ciclo e avvia una nuova iterazione.  
  
## Sintassi  
  
```  
continue [label];  
```  
  
## Note  
 L'argomento facoltativo `label` specifica l'istruzione a cui viene applicato `continue`.  
  
 Puoi utilizzare l'istruzione `continue` solo in un ciclo `while`, `do...while`, **for** o `for...in`.  Quando viene eseguita l'istruzione `continue` l'iterazione corrente del ciclo viene interrotta e il flusso del programma riprende dall'inizio del ciclo.  Ciò influisce sui vari tipi di ciclo come indicato di seguito:  
  
-   Nei cicli `while` e `do...while` viene eseguito un test e se risulta true, il ciclo viene rieseguito.  
  
-   Nei cicli `for` viene eseguita l'espressione di incremento e se l'espressione di test risulta true, il ciclo viene rieseguito.  
  
-   Nei cicli `for...in` viene eseguito uno spostamento al campo successivo della variabile specificata e il ciclo viene rieseguito.  
  
## Esempi  
 In questo esempio, un ciclo viene ripetuto da 1 a 9.  Le istruzioni comprese tra `continue` e la fine del corpo `for` vengono ignorate a causa dell'utilizzo dell'istruzione `continue` con l'espressione `(i < 5)`.  
  
```javascript  
for (var i = 1; i < 10; i++) {  
    if (i < 5) {  
        continue;  
    }  
    document.write (i);  
    document.write (" ");  
}  
  
// Output: 5 6 7 8 9  
```  
  
 Nel codice seguente l'istruzione `continue` fa riferimento al ciclo `for` preceduto dall'etichetta `Inner:`.  Quando `j` è uguale a 24, l'istruzione `continue` provoca il passaggio del ciclo `for` all'iterazione successiva.  I numeri compresi tra 21 e 23 e tra 25 e 30 vengono stampati su ogni riga.  
  
```javascript  
Outer:  
for (var i = 1; i <= 10; i++) {  
    document.write ("<br />");  
    document.write ("i: " + i);  
    document.write (" j: ");  
  
Inner:  
    for (var j = 21; j <= 30; j++) {  
        if (j == 24) {  
             continue Inner;  
        }  
        document.write (j + " ");  
    }  
}  
  
//Output:  
//i: 1 j: 21 22 23 25 26 27 28 29 30   
//i: 2 j: 21 22 23 25 26 27 28 29 30   
//i: 3 j: 21 22 23 25 26 27 28 29 30   
//i: 4 j: 21 22 23 25 26 27 28 29 30   
//i: 5 j: 21 22 23 25 26 27 28 29 30   
//i: 6 j: 21 22 23 25 26 27 28 29 30   
//i: 7 j: 21 22 23 25 26 27 28 29 30   
//i: 8 j: 21 22 23 25 26 27 28 29 30   
//i: 9 j: 21 22 23 25 26 27 28 29 30   
//i: 10 j: 21 22 23 25 26 27 28 29 30  
```  
  
## Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Vedere anche  
 [Istruzione break](../../javascript/reference/break-statement-javascript.md)   
 [Istruzione do...while](../../javascript/reference/do-dot-dot-dot-while-statement-javascript.md)   
 [Istruzione for](../../javascript/reference/for-statement-javascript.md)   
 [Istruzione for...in](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)   
 [Istruzione con etichetta](../../javascript/reference/labeled-statement-javascript.md)   
 [Istruzione while](../../javascript/reference/while-statement-javascript.md)