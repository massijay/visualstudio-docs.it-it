---
title: "Metodo valueOf (Number) | Microsoft Docs"
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
ms.assetid: 0242a9ce-d41a-4c9b-af59-e8df32bbd913
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Metodo valueOf (Number)
Restituisce il valore primitivo del numero specificato.  
  
## Sintassi  
  
```  
  
number.valueOf()  
```  
  
#### Parametri  
 Il metodo non ha parametri.  
  
## Valore restituito  
 Restituisce il numero.  
  
## Note  
 Nell'esempio seguente l'oggetto numero di cui è stata creata un'istanza è uguale al valore restituito del metodo.  
  
```javascript  
var num = 1234;  
var s = num.valueOf();  
  
if (num === s)  
document.write("same");  
else  
document.write("different");  
  
// Output:  
// same  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]