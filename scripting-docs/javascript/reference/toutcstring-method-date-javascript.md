---
title: "Metodo toUTCString (Date) (JavaScript) | Microsoft Docs"
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
  - "toUTCString"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toUTCString (metodo)"
  - "date UTC, conversione in stringhe"
ms.assetid: eb0983ed-7884-42fa-a2cc-de92b3111207
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Metodo toUTCString (Date) (JavaScript)
Restituisce una data convertita in una stringa utilizzando il formato UTC \(Tempo universale coordinato, Universal Coordinated Time\).  
  
## Sintassi  
  
```  
  
dateObj.toUTCString()   
```  
  
## Note  
 Il riferimento `dateObj` obbligatorio è un oggetto `Date`.  
  
 Mediante il metodo `toUTCString` viene restituito un oggetto `String` contenente la data formattata in base alla convenzione UTC e in un formato di agevole lettura.  
  
## Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo del metodo `toUTCString`.  
  
```javascript  
function toUTCStrDemo(){  
   var d, s;                   //Declare variables.  
   d = new Date();             //Create Date object.  
   s = "Current setting is ";  
   s += d.toUTCString();       //Convert to UTC string.  
   return(s);                  //Return UTC string.  
}  
```  
  
## Requisiti  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Si applica a**: [Oggetto Date](../../javascript/reference/date-object-javascript.md)  
  
## Vedere anche  
 [Metodo toGMTString \(Date\)](../../javascript/reference/togmtstring-method-date-javascript.md)