---
title: "Propriet&#224; description (Error) (JavaScript) | Microsoft Docs"
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
  - "Description"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Description (proprietà)"
  - "gestione errori, descrizione errore"
  - "errori, descrizione"
ms.assetid: ea727f1e-2041-4400-965c-67e6d47a1ff0
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# Propriet&#224; description (Error) (JavaScript)
Restituisce o imposta la stringa descrittiva associata a uno specifico errore.  
  
## Sintassi  
  
```  
  
object  
.description [= stringExpression]  
```  
  
## Parametri  
 *oggetto*  
 Obbligatorio.  Istanza di un oggetto `Error`.  
  
 `stringExpression`  
 Facoltativo.  Espressione di stringa contenente una descrizione dell'errore.  
  
## Note  
 La proprietà **description** contiene la stringa del messaggio di errore associato a uno specifico errore.  Utilizzare il valore contenuto in questa proprietà per avvertire l'utente di un errore.  
  
 Le proprietà **description** e **message** offrono le stesse funzionalità. La proprietà **description** offre compatibilità con le versioni precedenti, mentre **message** è conforme allo standard ECMA.  
  
## Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo della proprietà **description**.  
  
```javascript  
try  
{  
// Cause an error:  
    x = y     
}  
catch(e)  
{  
// Prints "[object Error]":  
    document.write(e)  
    document.write (" ");  
// Prints 5009:  
    document.write((e.number & 0xFFFF))    
    document.write (" ");  
// Prints "'y' is undefined":  
    document.write(e.description);  
    document.write (" ");  
// Prints "'y' is undefined":  
    document.write(e.message)  
}  
```  
  
## Requisiti  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
 **Si applica a**: [Oggetto Error](../../javascript/reference/error-object-javascript.md)  
  
## Vedere anche  
 [Proprietà number \(Error\)](../../javascript/reference/number-property-error-javascript.md)   
 [Proprietà message \(Error\)](../../javascript/reference/message-property-error-javascript.md)   
 [Proprietà name \(Error\)](../../javascript/reference/name-property-error-javascript.md)