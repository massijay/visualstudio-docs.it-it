---
title: "Costante undefined (JavaScript) | Microsoft Docs"
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
  - "undefined"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "undefined (proprietà)"
ms.assetid: 2a689d7d-00b0-48fb-9c95-5c2867bde006
caps.latest.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 20
---
# Costante undefined (JavaScript)
Valore che non è mai stato definito, quale una variabile che non è stata inizializzata.  
  
## Sintassi  
  
```  
undefined  
```  
  
## Note  
 La costante `undefined` è un membro dell'oggetto `Global` e diventa disponibile quando viene inizializzato il motore di script.  Quando una variabile viene dichiarata ma non inizializzata, il valore restituito è **undefined**.  
  
 Se una variabile non è stata dichiarata, non è possibile confrontarla con il valore `undefined`, ma è possibile confrontarne il tipo con la stringa "undefined".  
  
 La costante `undefined` risulta utile durante la verifica o l'impostazione esplicita di una variabile come non definita.  
  
## Esempio  
 Nell'esempio seguente viene illustrato come utilizzare la costante `undefined`.  
  
```javascript  
// A variable that has not been initialized.  
var declared;  
  
if (declared == undefined)  
    document.write("declared has not been given a value <br/>");  
else  
    document.write("declared has been given a value <br/>");  
  
document.write("typeof declared is " + typeof(declared) + "<br/>");  
  
// An undeclared variable cannot be compared to undefined,  
// so the next line would generate an error.  
// if (notDeclared == undefined);  
  
document.write("typeof notDeclared is " + typeof(notDeclared));  
  
// Output:  
// declared has not been given a value  
// typeof declared is undefined  
// typeof notDeclared is undefined  
```  
  
## Requisiti  
 La proprietà `undefined` è stata introdotta in [!INCLUDE[jsv55text](../../javascript/reference/includes/jsv55text-md.md)] ed è stata resa di sola lettura in [!INCLUDE[jsv9textspecific](../../javascript/reference/includes/jsv9textspecific-md.md)].  
  
 **Si applica a**: [Oggetto Global](../../javascript/reference/global-object-javascript.md)  
  
## Vedere anche  
 [Operatore typeof](../../javascript/reference/typeof-operator-decrementjavascript.md)