---
title: "Istruzione this (JavaScript) | Microsoft Docs"
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
  - "this_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "costruttori, riferimento all'oggetto corrente"
  - "this (istruzione)"
ms.assetid: 8510a00b-2f14-4700-a276-4d9a523c5112
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Istruzione this (JavaScript)
Fa riferimento all'oggetto corrente.  
  
## Sintassi  
  
```  
this.property  
```  
  
## Note  
 L'argomento obbligatorio `property` è una delle proprietà correnti dell'oggetto  
  
 La parola chiave `this` viene utilizzata nei costruttori di oggetti per fare riferimento all'oggetto corrente.  
  
## Esempio  
 Nell'esempio seguente **this** fa riferimento al nuovo oggetto Car e assegna valori a tre proprietà:  
  
```javascript  
function Car(color, make, model){  
   this.color = color;  
   this.make = make;  
   this.model = model;  
}  
```  
  
 La parola chiave **this** si riferisce solitamente all'oggetto **window** se utilizzata al di fuori dell'ambito di un altro oggetto.  Tuttavia, nei gestori eventi `this` fa riferimento all'elemento DOM che ha generato l'evento.  
  
 Nel codice seguente \(per Internet Explorer 9 e versioni successive\), il gestore eventi visualizza la versione della stringa di un pulsante con un ID "clicker".  
  
```javascript  
document.getElementById("clicker").addEventListener("click", eventHandler, false);  
  
        function eventHandler(ev) {  
            document.write(this.toString());  
        }  
  
// Output (when you click the button): [object HTMLButtonElement]  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Vedere anche  
 [Operatore new](../../javascript/reference/new-operator-decrementjavascript.md)   
 [Utilizzo del metodo bind](../../javascript/advanced/using-the-bind-method-javascript.md)