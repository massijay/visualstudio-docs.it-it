---
title: "Metodo has (Map) (JavaScript) | Microsoft Docs"
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
ms.assetid: 876df854-2941-4db2-92c6-1b497840b169
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Metodo has (Map) (JavaScript)
Restituisce `true` se la mappa contiene l'elemento specificato.  
  
## Sintassi  
  
```javascript  
mapObj.has(key)  
```  
  
#### Parametri  
 `mapObj`  
 Necessario.  Un oggetto `Map`.  
  
 `key`  
 Necessario.  Chiave dell'elemento su cui eseguire il test.  
  
## Valore proprietà\/Valore restituito  
 `true` se la mappa contiene l'elemento specificato.  
  
## Esempio  
 Di seguito viene illustrato come aggiungere un membro a un'oggetto `Map` e quindi controllare se la mappa lo contiene.  
  
```javascript  
var m = new Map();  
m.set(2, "red");  
  
document.write(m.has(2));  
  
// Output:  
// true  
```  
  
## Requisiti  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]