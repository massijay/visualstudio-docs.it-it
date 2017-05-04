---
title: "Propriet&#224; constructor (String) | Microsoft Docs"
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
ms.assetid: ef0e9c82-4651-4404-87b1-d00cad38c6f9
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Propriet&#224; constructor (String)
Specifica la funzione che crea una stringa.  
  
## Sintassi  
  
```  
  
string.constructor  
```  
  
## Note  
 L'argomento `string` obbligatorio è il nome di una stringa.  
  
 La proprietà `constructor` è un membro del prototipo di ogni oggetto che dispone di un prototipo.  Include tutti gli oggetti [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] intrinseci tranne gli oggetti `Math` e `Global`.  La proprietà `constructor` include un riferimento alla funzione che costruisce le istanze dell'oggetto specifico.  
  
## Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo della proprietà constructor.  
  
```javascript  
var x = new String();  
  
if (x.constructor == String)  
    document.write("Object is a String.");  
else  
    document.write("Object is not a String.");  
  
// Output:  
// Object is a String.  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]