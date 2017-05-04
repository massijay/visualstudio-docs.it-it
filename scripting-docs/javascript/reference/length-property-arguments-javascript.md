---
title: "Propriet&#224; length (arguments) (JavaScript) | Microsoft Docs"
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
  - "length Property"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Length (proprietà)"
  - "length (proprietà) (argomenti)"
ms.assetid: 3cf36823-15bc-489b-a951-24c4923d9dba
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Propriet&#224; length (arguments) (JavaScript)
Restituisce il numero effettivo di argomenti passati a una funzione dal chiamante.  
  
## Sintassi  
  
```  
[function.]arguments.length  
```  
  
## Note  
 L'argomento *function* facoltativo è il nome dell'oggetto `Function` attualmente in esecuzione.  
  
 La proprietà **length** dell'oggetto **arguments** viene inizializzata dal motore di script per il numero effettivo di argomenti passati a un oggetto `Function` all'avvio dell'esecuzione di tale funzione.  
  
## Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo della proprietà **length** dell'oggetto **arguments**.  Per comprendere totalmente l'esempio, passare alla funzione più argomenti rispetto ai 2 previsti:  
  
```javascript  
function ArgTest(a, b){  
   var s = "";  
  
   s += "Expected Arguments: " + ArgTest.length;  
   s += "<br />";  
   s += "Passed Arguments: " + arguments.length;  
  
   document.write (s);  
}  
```  
  
## Requisiti  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Si applica a**: [Oggetto Arguments](../../javascript/reference/arguments-object-javascript.md)&#124; [Oggetto Function](../../javascript/reference/function-object-javascript.md)  
  
## Vedere anche  
 [Proprietà arguments \(Function\)](../../javascript/reference/arguments-property-function-javascript.md)   
 [Proprietà length \(Array\)](../../javascript/reference/length-property-array-javascript.md)   
 [Proprietà length \(String\)](../../javascript/reference/length-property-string-javascript.md)