---
title: "Istruzione for...of (JavaScript) | Microsoft Docs"
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
ms.assetid: 7872b0b2-5701-4d72-9b52-ed13991542cc
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Istruzione for...of (JavaScript)
Esegue una o più istruzioni per ogni valore di un iteratore ottenuto da un oggetto iterabile.  
  
## Sintassi  
  
```  
for (variable of object) {  
    statements   
}  
```  
  
## Parametri  
 `variable`  
 Obbligatorio.  Una variabile che può essere qualsiasi valore della proprietà di `object`.  
  
 `object`  
 Obbligatorio.  Un oggetto iterabile, ad esempio `Array`, `Map`, `Set`, o un oggetto che implementa le [interfacce iteratore](http://msdn.microsoft.com/it-it/3692355a-a703-4d43-8fb5-c03b4b7e8db1).  
  
 `statements`  
 Facoltativo.  Una o più istruzioni da eseguire per ogni valore di `object`.  Può essere un'istruzione composta.  
  
## Note  
 All'inizio di ogni iterazione di un ciclo, il valore di `variable` è il successivo valore della proprietà di `object`.  
  
## Esempio  
 Nel codice seguente viene illustrato l'uso dell'istruzione `for...of` in una matrice.  
  
```javascript  
let arr = [ "fred", "tom", "bob" ];  
  
for (let i of arr) {  
    console.log(i);  
}  
  
// Output:  
// fred  
// tom  
// bob  
  
```  
  
## Esempio  
 Nel codice seguente viene illustrato l'uso dell'istruzione `for...of` in un oggetto `Map`.  
  
```javascript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
  
for (var n of m) {  
  console.log(n);  
}  
  
// Output:  
// 1,black  
// 2,red  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## Vedere anche  
 [Istruzione for...in](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)   
 [Istruzione for](../../javascript/reference/for-statement-javascript.md)   
 [Istruzione while](../../javascript/reference/while-statement-javascript.md)