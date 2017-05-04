---
title: "Propriet&#224; constructor (Number) | Microsoft Docs"
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
ms.assetid: a348fe53-1b4a-42f5-964b-53d57342c906
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Propriet&#224; constructor (Number)
Specifica la funzione che crea un valore numerico.  
  
## Sintassi  
  
```  
  
number.constructor  
```  
  
## Note  
 L'argomento `number` obbligatorio è il nome di una stringa.  
  
 La proprietà `constructor` è un membro del prototipo di ogni oggetto che dispone di un prototipo.  Include tutti gli oggetti [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] intrinseci tranne gli oggetti `Math` e `Global`.  La proprietà `constructor` include un riferimento alla funzione che costruisce le istanze dell'oggetto specifico.  
  
## Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo della proprietà constructor.  
  
```javascript  
var num = new Number();  
  
if (num.constructor == Number)  
    document.write("Object is a Number.");  
else  
    document.write("Object is not a Number.");  
  
// Output:  
// Object is a Number.  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]