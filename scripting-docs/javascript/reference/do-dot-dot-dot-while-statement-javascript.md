---
title: "Istruzione do...while (JavaScript) | Microsoft Docs"
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
  - "do_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "do...while (istruzione)"
  - "chiusura di cicli"
  - "strutture di ciclo, do e do-while"
ms.assetid: 8b7782ba-fbad-48cd-9639-193566da6ae5
caps.latest.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 20
---
# Istruzione do...while (JavaScript)
Esegue un blocco di istruzioni una volta, quindi ripete l'esecuzione del ciclo fino a quando un'espressione di condizione non restituisce `false`.  
  
## Sintassi  
  
```  
do {  
    statement  
}  
while (expression) ;   
```  
  
## Parametri  
 `statement`  
 Necessario.  Istruzione da eseguire se `expression` è `true`.  Può trattarsi di un'istruzione composta.  
  
 `expression`  
 Necessario.  Espressione che restituisce il valore booleano `true` o `false`.  Se `expression` è `true`, il ciclo viene eseguito di nuovo.  Se `expression` è `false`, il ciclo viene terminato.  
  
## Note  
 A differenza dell'istruzione `while`, un ciclo `do...while` viene eseguito una volta prima della valutazione dell'espressione condizionale.  
  
 In qualsiasi riga di un blocco `do…while` è possibile utilizzare l'istruzione `break` per fare in modo che il flusso di programma esca dal ciclo oppure è possibile utilizzare l'istruzione `continue` per passare direttamente all'espressione `while`.  
  
## Esempio  
 Nell'esempio seguente le istruzioni del ciclo `do...while` vengono eseguite finché la variabile `i` è minore di 10.  
  
```javascript  
var i = 0;  
do {  
    document.write(i + " ");  
    i++;  
} while (i < 10);  
  
// Output: 0 1 2 3 4 5 6 7 8 9   
```  
  
## Esempio  
 Nell'esempio seguente, le istruzioni del ciclo vengono eseguite una volta anche se la condizione non è soddisfatta.  
  
```javascript  
var i = 10;  
do {  
    document.write(i + " ");  
    i++;  
} while (i < 10);  
  
// Output: 10  
```  
  
## Requisiti  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## Vedere anche  
 [Istruzione break](../../javascript/reference/break-statement-javascript.md)   
 [Istruzione continue](../../javascript/reference/continue-statement-javascript.md)   
 [Istruzione for](../../javascript/reference/for-statement-javascript.md)   
 [Istruzione for...in](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)   
 [Istruzione while](../../javascript/reference/while-statement-javascript.md)   
 [Istruzione con etichetta](../../javascript/reference/labeled-statement-javascript.md)