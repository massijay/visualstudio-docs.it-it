---
title: "Propriet&#224; message (Error) (JavaScript) | Microsoft Docs"
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
  - "message"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Message (proprietà)"
ms.assetid: 8cab0392-e0db-4714-827c-47ab04e8b4f2
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# Propriet&#224; message (Error) (JavaScript)
Restituisce una stringa di messaggio di errore.  
  
## Sintassi  
  
```  
  
errorObj.message  
```  
  
## Parametri  
 `errorObj`  
 Obbligatorio.  Istanza dell'oggetto `Error`.  
  
## Note  
 La proprietà `message` restituisce una stringa contenente un messaggio di errore associato a un errore specifico.  
  
 Le proprietà `description` e `message` forniscono la stessa funzionalità.  La proprietà `description` garantisce la compatibilità con le versioni precedenti. La proprietà `message` è conforme allo standard ECMA.  
  
## Esempio  
 Nell'esempio seguente viene generata un'eccezione TypeError e viene visualizzato il nome dell'errore e il relativo messaggio.  
  
```javascript  
try  
{  
    // Cause an error.  
    var x = y;  
}  
catch(e)  
{  
    document.write ("Error Message: " + e.message);  
    document.write ("<br />");  
    document.write ("Error Code: ");  
    document.write (e.number & 0xFFFF)  
    document.write ("<br />");  
    document.write ("Error Name: " + e.name);  
}  
```  
  
## Esempio  
 L'output del codice è il seguente.  
  
```javascript  
Error Message: 'y' is undefined  
Error Code: 5009  
Error Name: TypeError  
```  
  
## Requisiti  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
 **Si applica a**: [Oggetto Error](../../javascript/reference/error-object-javascript.md)  
  
## Vedere anche  
 [Proprietà description \(Error\)](../../javascript/reference/description-property-error-javascript.md)   
 [Proprietà name \(Error\)](../../javascript/reference/name-property-error-javascript.md)