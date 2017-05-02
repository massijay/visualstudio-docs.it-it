---
title: "Propriet&#224; prototype (Number) | Microsoft Docs"
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
ms.assetid: d5fb87af-fc3a-4469-8dde-d31daf654f94
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Propriet&#224; prototype (Number)
Restituisce un riferimento al prototipo per una classe di numero.  
  
## Sintassi  
  
```  
  
number.prototype  
```  
  
## Note  
 L'argomento `number` è il nome di un numero.  
  
 Utilizzare la proprietà `prototype` per fornire un set di funzionalità di base a una classe di oggetti.  Le nuove istanze di un oggetto "ereditano" il comportamento del prototipo assegnato all'oggetto.  
  
 Per aggiungere, ad esempio, un metodo all'oggetto `Number` che restituisce il numero di cifre \(Integer\), dichiarare la funzione, aggiungerla a `Number.prototype`, quindi utilizzarla.  
  
```javascript  
function number_digits() {  
    var digits = 0;  
    var num = this;  
    while (num) >= 1) {  
        digits++;  
        num /= 10;  
    }  
    return digits;  
}  
  
Number.prototype.digits = number_digits;  
var myNumber = new Number(3456.789);  
document.write(myNumber.digits());  
// Output:  
// 4  
```  
  
 A tutti gli oggetti [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] intrinseci è associata una proprietà `prototype` di sola lettura.  Le proprietà e i metodi possono essere aggiunti al prototipo, ma l'oggetto non può essere assegnato a un prototipo diverso.  Tuttavia, agli oggetti definiti dall'utente può essere assegnato un nuovo prototipo.  
  
 Per ogni oggetto intrinseco descritto in questo riferimento al linguaggio vengono indicati i metodi e le proprietà che fanno parte \(o non fanno parte\) del prototipo corrispondente.  
  
## Requisiti  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]