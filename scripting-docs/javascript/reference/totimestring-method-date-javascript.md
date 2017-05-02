---
title: "Metodo toTimeString (Date) (JavaScript) | Microsoft Docs"
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
  - "toTimeString"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toTimeString (metodo)"
ms.assetid: a4a8c0f2-55a9-4e84-94c3-f0a547fb04b5
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Metodo toTimeString (Date) (JavaScript)
Restituisce un'ora come valore stringa.  
  
## Sintassi  
  
```  
  
objDate. toTimeString( )  
```  
  
## Note  
 Il riferimento di `objDate` obbligatorio è un oggetto `Date`.  
  
 Il metodo `toTimeString` restituisce un valore stringa contenente l'ora nel fuso orario corrente.  
  
## Esempio  
 Nell'esempio seguente l'ora è impostata su 2000 millisecondi dopo la mezzanotte dell'1 gennaio 1970 in formato UTC e viene scritta.  
  
```javascript  
var aDate = new Date();  
     aDate.setTime(2000);  
     document.write(aDate.toTimeString());  
  
// Output depends on the time in the current time zone.  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## Vedere anche  
 [Metodo toDateString \(Date\)](../../javascript/reference/todatestring-method-date-javascript.md)   
 [Metodo toLocaleTimeString \(Date\)](../../javascript/reference/tolocaletimestring-method-date-javascript.md)