---
title: "Istruzione function (JavaScript) | Microsoft Docs"
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
  - "function_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "dichiarazione di funzioni"
  - "dichiarazione di funzioni, sintassi"
  - "function (istruzione)"
  - "new (operatore)"
ms.assetid: cc9cfd43-1305-41c8-ad67-545d20f4fafe
caps.latest.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 20
---
# Istruzione function (JavaScript)
Dichiara una nuova funzione.  
  
## Sintassi  
  
```  
function functionname ([arg1 [, arg2 [,...[, argN]]]]) {  
    statements  
}   
```  
  
## Parametri  
 `functionname`  
 Obbligatorio.  Nome della funzione.  
  
 `arg1...argN`  
 Facoltativo.  Elenco facoltativo delimitato da virgole degli argomenti compresi dalla funzione.  
  
 `statements`  
 Facoltativo.  Una o più istruzioni di [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## Note  
 Utilizzare l'istruzione `function` per dichiarare una funzione da utilizzare successivamente.  Il codice specificato in `statements` viene eseguito soltanto dopo che la funzione viene chiamata da un punto qualsiasi dello script.  
  
 L'istruzione [return](../../javascript/reference/return-statement-javascript.md) viene utilizzata per restituire un valore dalla funzione.  Non è necessario utilizzare un'istruzione `return` dal momento che il valore verrà restituito dal programma una volta raggiunta la fine della funzione.  Se nessuna istruzione `return` viene eseguita nella funzione o se l'istruzione `return` non include alcuna espressione, la funzione restituisce il valore `undefined`.  
  
> [!NOTE]
>  Quando si chiama una funzione, assicurarsi di includere le parentesi ed eventuali argomenti obbligatori.  La chiamata a una funzione senza parentesi restituisce un riferimento alla funzione, ma non i risultati della funzione.  
  
## Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo dell'istruzione `function`.  
  
```javascript  
function myfunction (arg1, arg2) {  
    var r = arg1 * arg2;  
    return(r);  
}  
```  
  
## Esempio  
 Una funzione può essere assegnata a una variabile,  come illustrato nell'esempio seguente.  
  
```javascript  
function AddFive(x) {  
    return x + 5;  
}  
  
function AddTen(x) {  
    return x + 10;  
}  
  
var condition = false;  
  
var MyFunc;  
if (condition) {  
    MyFunc = AddFive;  
}  
else {  
    MyFunc = AddTen;  
}  
  
var result = MyFunc(123);  
// Output: 133  
```  
  
## Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Vedere anche  
 [Operatore new](../../javascript/reference/new-operator-decrementjavascript.md)