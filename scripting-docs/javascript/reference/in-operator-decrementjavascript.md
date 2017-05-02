---
title: "Operatore in (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "in_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "in (operatore)"
ms.assetid: dcd8f901-96b8-4c91-848b-b1ec0ab1c11c
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# Operatore in (JavaScript)
Verifica l'esistenza di una proprietà in un oggetto.  
  
## Sintassi  
  
```  
  
result = property in object  
```  
  
## Parametri  
 `result`  
 Obbligatorio.  Qualsiasi variabile.  
  
 `property`  
 Obbligatorio.  Espressione che restituisce un'espressione di stringa.  
  
 `object`  
 Obbligatorio.  Qualsiasi oggetto.  
  
## Note  
 L'operatore `in` determina se un oggetto contiene una proprietà denominata `property`.  Determina anche se la proprietà fa parte della catena di prototipi dell'oggetto.  Per ulteriori informazioni sui prototipi degli oggetti, vedi [Prototipi ed ereditarietà del prototipo](../../javascript/advanced/prototypes-and-prototype-inheritance.md).  
  
## Esempio  
 Nell'esempio seguente viene illustrato come utilizzare l'operatore `in`.  
  
```javascript  
// Create an object that has some properties.  
var myObject = new Object();  
myObject.name = "James";  
myObject.age = "22";  
myObject.phone = "555 0234";  
  
if ("phone" in myObject)  
   document.write ("property is present");  
else  
   document.write ("property is not present");  
  
// Output: property is present  
```  
  
## Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Vedere anche  
 [Precedenza tra gli operatori](../../javascript/operator-subtractprecedence-javascript.md)   
 [Riepilogo degli operatori \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)