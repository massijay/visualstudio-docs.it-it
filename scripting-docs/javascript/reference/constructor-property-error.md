---
title: "Propriet&#224; constructor (Error) | Microsoft Docs"
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
ms.assetid: 18aea278-2bd5-457b-83a5-d8d8f1226e0c
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Propriet&#224; constructor (Error)
Specifica la funzione che crea un errore.  
  
## Sintassi  
  
```  
  
error.constructor  
```  
  
## Note  
 L'argomento `error` obbligatorio è il nome di un oggetto errore.  
  
 La proprietà `constructor` è un membro del prototipo di ogni oggetto che dispone di un prototipo.  La proprietà `constructor` include un riferimento alla funzione che costruisce le istanze dell'oggetto specifico.  
  
## Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo della proprietà constructor.  
  
```javascript  
var x = new Error("This is an error");  
  
if (x.constructor == Error)  
    document.write("Object is an error.");  
  
// Output:  
// Object is an error.  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]