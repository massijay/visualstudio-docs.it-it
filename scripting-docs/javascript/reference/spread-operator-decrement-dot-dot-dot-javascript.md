---
title: "Operatore spread (...) (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 10263a4c-bd27-4d87-9917-fb4b6bf373db
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Operatore spread (...) (JavaScript)
Consente di inizializzare parti di un valore letterale della matrice da un'espressione iterabile \(come un altro valore letterale della matrice\) oppure di espandere un'espressione in più argomenti \(in chiamate di funzione\).  
  
## Sintassi  
  
```  
var array = [[arg0ToN ,] ...iterable [, arg0ToN]]  
func([args ,] ...iterable [, args | ...iterable])  
  
```  
  
## Parametri  
 `iterable`  
 Obbligatorio.  Oggetto iterabile.  
  
 `arg0ToN`  
 Facoltativo.  Uno o più elementi di un valore letterale della matrice.  
  
 `args`  
 Facoltativo.  Uno o più argomenti di una funzione.  
  
## Note  
 Per altre informazioni sugli iteratori, vedere [Iteratori e generatori](../../javascript/advanced/iterators-and-generators-javascript.md).  Per altre informazioni sull'uso dell'operatore spread come parametro rest, vedere [Funzioni](../../javascript/functions-javascript.md).  
  
## Esempio  
 Nell'esempio di codice seguente vengono illustrate le differenze tra dell'operatore spread e il metodo `concat`.  
  
```javascript  
var a, b, c, d, e;  
a = [1,2,3];  
b = "dog";  
c = [42, "cat"];  
  
// Using the concat method.  
d = a.concat(b, c);  
  
// Using the spread operator.  
e = [...a, b, ...c];  
  
console.log(d);  
console.log(e);  
  
// Output:  
// 1, 2, 3, "dog", 42, "cat"  
// 1, 2, 3, "dog", 42, "cat"  
```  
  
## Esempio  
 Nell'esempio di codice seguente viene illustrato l'uso dell'operatore spread in una chiamata di funzione.  In questo esempio due valori letterali della matrice vengono passati alla funzione tramite l'operatore spread e le due matrici vengono espanse in più argomenti.  
  
```javascript  
function f(a, b, c, x, y, z) {  
  return a + b + c + x + y + z;  
}  
  
var args = [1, 2, 3];  
console.log(f(...args, 4, ...[5, 6]));  
  
// Output:  
// 21  
  
```  
  
## Esempio  
 Con gli operatori spread è possibile semplificare il codice per il quale in precedenza era necessario usare `apply`.  
  
```javascript  
function f(x, y, z) {  
    return x + y + z;  
}  
  
var args = [1, 2, 3];  
  
// Old method  
func.apply(this, args);  
// New method  
func(...args);  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## Vedere anche  
 [Precedenza tra gli operatori](../../javascript/operator-subtractprecedence-javascript.md)   
 [Riepilogo degli operatori \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)