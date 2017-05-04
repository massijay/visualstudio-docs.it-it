---
title: "Propriet&#224; prototype (Date) | Microsoft Docs"
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
ms.assetid: 44f9c637-7da7-4833-906d-358506f32ced
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Propriet&#224; prototype (Date)
Restituisce un riferimento al prototipo per una data.  
  
## Sintassi  
  
```  
  
date.prototype  
```  
  
## Note  
 L'argomento `date` è il nome di un oggetto.  
  
 Utilizzare la proprietà `prototype` per fornire un set di funzionalità di base a un oggetto Date.  Le nuove istanze di un oggetto "ereditano" il comportamento del prototipo assegnato all'oggetto.  
  
 Per aggiungere, ad esempio, un metodo all'oggetto `Date` che restituisce il valore dell'elemento più grande della matrice, dichiarare la funzione, aggiungerla a `Date.prototype`, quindi utilizzarla.  
  
```javascript  
function max( ){  
    var max = new Date();  
    max.setFullYear(2200, 01, 01);  
    return max;  
}  
Date.prototype.maxDate = max;  
var myDate = new Date();  
  
if (myDate < myDate.maxDate())  
    document.write("today isn't the max");  
else if (myDate == myDate.maxDate())  
    document.write("today is the max");   
  
// Output:  
// today isn't the max  
  
```  
  
 A tutti gli oggetti [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] intrinseci è associata una proprietà `prototype` di sola lettura.  Le proprietà e i metodi possono essere aggiunti al prototipo, ma l'oggetto non può essere assegnato a un prototipo diverso.  Tuttavia, agli oggetti definiti dall'utente può essere assegnato un nuovo prototipo.  
  
## Requisiti  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]