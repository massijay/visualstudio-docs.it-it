---
title: "Istruzione return (JavaScript) | Microsoft Docs"
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
  - "return_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "function (istruzione)"
  - "return (istruzione)"
  - "return (istruzione), uscita da funzioni in script"
  - "return (istruzione), sintassi"
  - "chiusura dell'esecuzione"
ms.assetid: a9130d90-11fb-43f5-a819-7e5435f74c05
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Istruzione return (JavaScript)
Consente di uscire dalla funzione corrente e restituisce un valore di quella funzione.  
  
## Sintassi  
  
```  
  
return[(][expression][)];   
```  
  
## Note  
 L'argomento *expression* facoltativo è il valore che la funzione deve restituire.  Se omesso, non verrà restituito alcun valore.  
  
 Utilizzare l'istruzione `return` per interrompere l'esecuzione di una funzione e restituire il valore di *expression*.  Se si omette *expression* oppure nella funzione non viene eseguita alcuna istruzione `return`, all'espressione che ha richiamato la funzione corrente verrà assegnato il valore undefined.  
  
## Esempio  
 Nel codice seguente viene illustrato l'utilizzo dell'istruzione `return`.  
  
```javascript  
function myfunction(arg1, arg2){  
   var r;  
   r = arg1 * arg2;  
   return(r);  
}  
```  
  
## Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo dell'istruzione `return` per restituire una funzione.  
  
```javascript  
function doWork() {  
    return function calculate(y) { return y + 1; };  
}  
  
var func = doWork();  
var x = func(5);  
document.write(x);  
  
// Output: 6  
```  
  
## Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Vedere anche  
 [Istruzione function](../../javascript/reference/function-statement-javascript.md)