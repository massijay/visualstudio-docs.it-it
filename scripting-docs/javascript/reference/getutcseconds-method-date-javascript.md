---
title: "Metodo getUTCSeconds (Date) (JavaScript) | Microsoft Docs"
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
  - "getUTCSeconds"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "ora UTC, restituzione"
  - "seconds (metodo)"
  - "getUTCSeconds (metodo)"
ms.assetid: 2d8ea7dc-79f8-4a9b-b2ab-732db2bcd5fd
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Metodo getUTCSeconds (Date) (JavaScript)
Ottiene i secondi di un oggetto `Date` utilizzo di tempo universale coordinato \(UTC\).  
  
## Sintassi  
  
```  
  
dateObj.getUTCSeconds()   
```  
  
#### Parametri  
 Il riferimento richiesto `dateObj` è un oggetto `Date`.  
  
## Valore restituito  
 Restituisce un Integer compreso tra 0 e 59.  Zero viene restituito quando il tempo è minore di secondo nel minuto corrente.  Se un oggetto `Date` è stato creato senza specificare il tempo, il valore dei secondi UTC è 0.  
  
## Note  
 Per ottenere il numero di secondi in base all'ora locale, è possibile utilizzare il metodo `getSeconds`.  
  
## Esempio  
 Nell'esempio seguente viene illustrato come utilizzare il metodo `getUTCSeconds`.  
  
```javascript  
var date = new Date("1/1/2001");  
document.write(date. getUTCSeconds());  
  
// Output: 0  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Applies To**: [Oggetto Date](../../javascript/reference/date-object-javascript.md)  
  
## Vedere anche  
 [Metodo getSeconds \(Date\)](../../javascript/reference/getseconds-method-date-javascript.md)   
 [Metodo setSeconds \(Date\)](../../javascript/reference/setseconds-method-date-javascript.md)   
 [Metodo setUTCSeconds \(Date\)](../../javascript/reference/setutcseconds-method-date-javascript.md)