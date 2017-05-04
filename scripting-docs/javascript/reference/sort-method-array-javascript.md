---
title: "Metodo sort (Array) (JavaScript) | Microsoft Docs"
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
  - "sort"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Sort (metodo)"
ms.assetid: 9bd8b54a-c838-4806-85c8-62eebe6bc48c
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# Metodo sort (Array) (JavaScript)
Ordina un `Array`.  
  
## Sintassi  
  
```  
  
arrayobj.sort(sortFunction)   
```  
  
## Parametri  
 `arrayObj`  
 Necessario.  Qualsiasi oggetto `Array`.  
  
 `sortFunction`  
 Opzionale.  Il nome della funzione utilizzata per determinare l'ordine degli elementi.  Se omessa, gli elementi vengono disposti nell'ordine dei caratteri ASCII crescente.  
  
## Valore restituito  
 Matrice ordinata.  
  
## Note  
 Il metodo `sort` ordina l'oggetto `Array` sul posto; non viene creato un nuovo oggetto `Array` durante l'esecuzione.  
  
 Se per l'argomento `sortFunction` viene specificata una funzione, essa dovrà restituire uno dei seguenti valori:  
  
-   Un valore negativo se il primo argomento passato è minore del secondo argomento.  
  
-   Zero se i due argomenti sono equivalenti.  
  
-   Un valore positivo se il primo argomento è maggiore del secondo.  
  
## Esempio  
 Nell'esempio seguente viene illustrato come utilizzare il metodo `sort`.  
  
```javascript  
var a = new Array(4, 11, 2, 10, 3, 1);  
  
var b = a.sort();  
document.write(b);  
document.write("<br/>");  
  
// This is ASCII character order.  
// Output: 1,10,11,2,3,4)  
  
// Sort the array elements with a function that compares array elements.  
b = a.sort(CompareForSort);  
document.write(b);  
document.write("<br/>");  
// Output: 1,2,3,4,10,11.  
  
// Sorts array elements in ascending order numerically.  
function CompareForSort(first, second)  
{  
    if (first == second)  
        return 0;  
    if (first < second)  
        return -1;  
    else  
        return 1;   
}  
```  
  
## Requisiti  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]