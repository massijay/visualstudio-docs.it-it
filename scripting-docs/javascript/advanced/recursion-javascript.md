---
title: "Ricorsione (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "funzioni, chiamate di funzioni ricorsive"
  - "routine ricorsive"
  - "chiamate di funzione, ricorsive"
ms.assetid: 885855a6-3838-457d-9eb4-cce1ccaa5a8d
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# Ricorsione (JavaScript)
La ricorsione è un'importante tecnica di programmazione nella quale una funzione chiama se stessa.  
  
## Esempio di ricorsione  
 Un esempio è il calcolo di fattoriali.  Il fattoriale di un numero *n* viene calcolato moltiplicando 1 \* 2 \* 3 \*…  *n*.  Nell'esempio seguente viene illustrato come calcolare i fattoriali in modo iterativo, ovvero, utilizzando un ciclo `while` in cui viene calcolato il risultato.  
  
```javascript  
function factorial(num)  
{  
    // If the number is less than 0, reject it.  
    if (num < 0) {  
        return -1;  
    }  
    // If the number is 0, its factorial is 1.  
    else if (num == 0) {  
        return 1;  
    }  
    var tmp = num;  
    while (num-- > 2) {  
        tmp *= num;  
    }  
    return tmp;  
}  
  
var result = factorial(8);  
document.write(result);  
  
// Output: 40320  
```  
  
 Puoi applicare la ricorsione all'esempio molto semplicemente.  Anziché utilizzare un ciclo `while` per calcolare il valore, puoi semplicemente chiamare di nuovo `factorial`, passando il successivo valore più basso.  La ricorsione termina quando il valore è 1.  
  
```javascript  
function factorial(num)  
{  
    // If the number is less than 0, reject it.  
    if (num < 0) {  
        return -1;  
    }  
    // If the number is 0, its factorial is 1.  
    else if (num == 0) {  
        return 1;  
    }  
    // Otherwise, call this recursive procedure again.  
    else {  
        return (num * factorial(num - 1));  
    }  
}  
  
var result = factorial(8);  
document.write(result);  
  
// Output: 40320  
```