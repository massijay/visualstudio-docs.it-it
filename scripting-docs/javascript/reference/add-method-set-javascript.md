---
title: "Metodo add (Set) (JavaScript) | Microsoft Docs"
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
ms.assetid: b4eea447-fd5b-4380-978e-1b95f6dbc438
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Metodo add (Set) (JavaScript)
Aggiunge un nuovo elemento a un set.  
  
## Sintassi  
  
```javascript  
setObj.add(value)  
```  
  
#### Parametri  
 `setObj`  
 Necessario.  Oggetto `Set`.  
  
 `value`  
 Necessario.  Nuovo elemento dell'oggetto `Set`.  
  
## Note  
 Il nuovo elemento può essere di qualsiasi tipo e deve essere univoco.  Se si aggiunge un elemento non univoco a `Set`, il nuovo elemento non verrà aggiunto alla raccolta.  
  
## Esempio  
 Nell'esempio seguente viene illustrato come aggiungere membri a un oggetto Set e quindi recuperarli.  
  
```javascript  
var s = new Set();  
s.add("Thomas Jefferson");  
s.add(1776);  
s.add("founding father");  
  
s.forEach(function (item) {  
    document.write(item.toString() + ", ");  
});  
  
// Output:  
// Thomas Jefferson, 1776, founding father,  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]