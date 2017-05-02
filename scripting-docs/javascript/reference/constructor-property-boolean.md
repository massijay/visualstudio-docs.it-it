---
title: "Propriet&#224; constructor (Boolean) | Microsoft Docs"
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
ms.assetid: b67ca875-23c6-4687-a5ce-1cdd25d1c923
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Propriet&#224; constructor (Boolean)
Specifica la funzione che crea un valore booleano.  
  
## Sintassi  
  
```  
  
boolean.constructor([[value])  
```  
  
#### Parametri  
 `boolean`  
 Nome del valore booleano.  
  
 `value`  
 Facoltativo.  Specifica il valore booleano.  Può corrispondere ai numeri 1 o 0 o alle stringhe "true" o "false".  
  
## Note  
 La proprietà `constructor` include un riferimento alla funzione che costruisce le istanze dell'oggetto Boolean.  
  
## Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo della proprietà constructor.  
  
```javascript  
var x = new Boolean("true");  
  
if (x.constructor == Boolean)  
    document.write("Object is a Boolelan.");  
  
// Output:  
// Object is a Boolean.  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]