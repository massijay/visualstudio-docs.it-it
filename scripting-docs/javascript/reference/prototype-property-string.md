---
title: "Propriet&#224; prototype (String) | Microsoft Docs"
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
ms.assetid: 437ce478-9c45-45f7-8952-bd71856cfcd8
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Propriet&#224; prototype (String)
Restituisce un riferimento al prototipo per una classe di stringa.  
  
## Sintassi  
  
```  
  
string.prototype  
```  
  
## Note  
 L'argomento `string` è il nome di una stringa.  
  
 Utilizzare la proprietà `prototype` per fornire un set di funzionalità di base a una classe di oggetti.  Le nuove istanze di un oggetto "ereditano" il comportamento del prototipo assegnato all'oggetto.  
  
 Per aggiungere, ad esempio, un metodo all'oggetto `String` che restituisce il valore dell'ultimo elemento della stringa, dichiarare la funzione, aggiungerla a `String.prototype`, quindi utilizzarla.  
  
```javascript  
function string_last( ){  
    return this.charAt(this.length - 1);  
}  
String.prototype.last = string_last;  
var myString = new String("every good boy does fine");  
document.write(myString.last());  
  
// Output:  
// e  
```  
  
 A tutti gli oggetti [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] intrinseci è associata una proprietà `prototype` di sola lettura.  Le proprietà e i metodi possono essere aggiunti al prototipo, ma l'oggetto non può essere assegnato a un prototipo diverso.  Tuttavia, agli oggetti definiti dall'utente può essere assegnato un nuovo prototipo.  
  
 Per ogni oggetto intrinseco descritto in questo riferimento al linguaggio vengono indicati i metodi e le proprietà che fanno parte \(o non fanno parte\) del prototipo corrispondente.  
  
## Requisiti  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]