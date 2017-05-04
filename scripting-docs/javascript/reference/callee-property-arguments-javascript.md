---
title: "Propriet&#224; callee (arguments) (JavaScript) | Microsoft Docs"
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
  - "callee"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "callee (proprietà)"
ms.assetid: ad9d4d21-73f0-44f6-8bec-502f3456cd23
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Propriet&#224; callee (arguments) (JavaScript)
Restituisce l'oggetto `Function` in esecuzione, ovvero il testo del corpo dell'oggetto `Function` specificato.  
  
## Sintassi  
  
```  
[function.]arguments.callee  
```  
  
## Note  
 L'argomento *function* facoltativo è il nome dell'oggetto `Function` attualmente in esecuzione.  
  
 La proprietà `callee` è un membro dell'oggetto **arguments** che diventa disponibile solo quando la funzione associata è in esecuzione.  
  
 Il valore iniziale della proprietà `callee` è l'oggetto `Function` in esecuzione.  In questo modo sono consentite funzioni anonime ricorsive.  
  
## Esempio  
  
```javascript  
function factorial(n){  
  if (n <= 0)  
     return 1;  
  else  
     return n * arguments.callee(n - 1)  
}  
document.write(factorial(4));  
```  
  
## Requisiti  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Si applica a**: [Oggetto Arguments](../../javascript/reference/arguments-object-javascript.md)&#124; [Oggetto Function](../../javascript/reference/function-object-javascript.md)  
  
## Vedere anche  
 [Proprietà caller \(Function\)](../../javascript/reference/caller-property-function-javascript.md)