---
title: "Propriet&#224; constructor (Array) | Microsoft Docs"
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
ms.assetid: b78d517b-cb56-4866-b30f-ef8121a27843
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Propriet&#224; constructor (Array)
Specifica la funzione che crea una matrice.  
  
## Sintassi  
  
```  
  
array.constructor  
```  
  
## Note  
 L'argomento `array` obbligatorio è il nome di una matrice.  
  
 La proprietà `constructor` è un membro del prototipo di ogni oggetto che dispone di un prototipo.  Include tutti gli oggetti [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] intrinseci tranne gli oggetti `Math` e `Global`.  La proprietà `constructor` include un riferimento alla funzione che costruisce le istanze dell'oggetto specifico.  
  
## Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo della proprietà constructor.  
  
```javascript  
var x = new Array();  
  
if (x.constructor == Array)  
    document.write("Object is an Array.");  
else  
    document.write("Object is not an Array.");  
  
// Output:  
// Object is an Array.  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]