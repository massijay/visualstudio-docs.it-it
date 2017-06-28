---
title: "Propriet&#224; prototype (Object) (JavaScript) | Microsoft Docs"
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
  - "Prototype"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "ereditarietà, oggetti"
  - "prototype (proprietà)"
ms.assetid: 9fc434a1-5995-4fcb-a4e8-00e7f615aaa2
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Propriet&#224; prototype (Object) (JavaScript)
Restituisce un riferimento al prototipo per una classe di oggetti.  
  
## Sintassi  
  
```  
  
objectName.prototype  
```  
  
## Note  
 L'argomento `objectName` è il nome di un oggetto.  
  
 Utilizzare la proprietà `prototype` per fornire un set di funzionalità di base a una classe di oggetti.  Le nuove istanze di un oggetto "ereditano" il comportamento del prototipo assegnato all'oggetto.  
  
 Per aggiungere, ad esempio, un metodo all'oggetto `Array` che restituisce il valore dell'elemento più grande della matrice, dichiarare la funzione, aggiungerla a `Array.prototype`, quindi utilizzarla.  
  
```javascript  
function array_max( ){  
    var i, max = this[0];  
    for (i = 1; i < this.length; i++)  
    {  
    if (max < this[i])  
    max = this[i];  
    }  
    return max;  
}  
Array.prototype.max = array_max;  
var myArray = new Array(7, 1, 3, 11, 25, 9  
);  
document.write(myArray.max());  
  
// Output:  
// 25  
  
```  
  
 A tutti gli oggetti [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] intrinseci è associata una proprietà `prototype` di sola lettura.  Le proprietà e i metodi possono essere aggiunti al prototipo, ma l'oggetto non può essere assegnato a un prototipo diverso.  Tuttavia, agli oggetti definiti dall'utente può essere assegnato un nuovo prototipo.  
  
 Per ogni oggetto intrinseco descritto in questo riferimento al linguaggio vengono indicati i metodi e le proprietà che fanno parte \(o non fanno parte\) del prototipo corrispondente.  
  
## Requisiti  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## Vedere anche  
 [Proprietà constructor \(Object\)](../../javascript/reference/constructor-property-object-javascript.md)