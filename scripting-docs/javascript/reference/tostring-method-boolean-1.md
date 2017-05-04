---
title: "Metodo toString (Boolean) | Microsoft Docs"
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
ms.assetid: c46b43c0-6946-407a-b0e0-49cba90e226a
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Metodo toString (Boolean)
Restituisce una rappresentazione in forma di stringa di un oggetto.  
  
## Sintassi  
  
```  
  
boolean.toString()  
```  
  
## Parametri  
 `boolean`  
 Obbligatorio.  Oggetto di cui ottenere una rappresentazione in forma di stringa.  
  
## Valore restituito  
 Se il valore Boolean è `true`, viene restituito "true".  In caso contrario, viene restituito "false".  
  
## Note  
  
## Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo del metodo **toString**.  
  
```javascript  
var s = new Boolean(0);  
document.write(s.toString());  
  
// Output: false;  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]