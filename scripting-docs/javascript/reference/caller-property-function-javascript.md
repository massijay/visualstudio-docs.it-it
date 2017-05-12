---
title: "Propriet&#224; caller (Function) (JavaScript) | Microsoft Docs"
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
  - "caller"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "caller (proprietà)"
  - "chiamate di funzione, funzioni in esecuzione"
ms.assetid: ae210853-7160-4102-9cfd-ab489f180ce1
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Propriet&#224; caller (Function) (JavaScript)
Ottiene la funzione che ha chiamato la funzione corrente.  
  
## Sintassi  
  
```  
  
functionName.caller  
```  
  
## Note  
 L'oggetto `functionName` è il nome di una qualsiasi funzione in esecuzione.  
  
 La proprietà `caller` è definita per una funzione solo mentre questa è in esecuzione.  Se la funzione viene chiamata dal livello superiore di un programma [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)], `caller` conterrà `null`.  
  
 Se la proprietà `caller` viene utilizzata in un contesto di stringa, il risultato sarà identico a quello restituito da `functionName`.`toString`, ovvero verrà visualizzato il testo decompilato della funzione.  
  
 Nell'esempio seguente viene illustrato l'utilizzo della proprietà `caller`:  
  
```javascript  
function CallLevel(){  
   if (CallLevel.caller == null)  
      return("CallLevel was called from the top level.");  
   else  
      return("CallLevel was called by another function.");  
}  
  
document.write(CallLevel());  
  
// Output: CallLevel was called from the top level.  
```  
  
## Requisiti  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## Vedere anche  
 [Istruzione function](../../javascript/reference/function-statement-javascript.md)