---
title: "Propriet&#224; constructor (Date) | Microsoft Docs"
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
ms.assetid: 5db153a1-788b-4a61-bfc8-2d2ec38f36ea
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Propriet&#224; constructor (Date)
Specifica la funzione che crea una data.  
  
## Sintassi  
  
```  
  
date.constructor  
```  
  
## Note  
 L'argomento `date` obbligatorio è il nome di un oggetto data.  
  
 La proprietà `constructor` è un membro del prototipo di ogni oggetto che dispone di un prototipo.  La proprietà `constructor` include un riferimento alla funzione che costruisce le istanze dell'oggetto specifico.  
  
## Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo della proprietà constructor.  
  
```javascript  
var x = new Date("Hi");  
  
if (x.constructor == Date)  
    document.write("Object is a date.");  
  
// Output:  
// Object is a date.  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]