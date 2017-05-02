---
title: "Metodo getUTCMilliseconds (Date) (JavaScript) | Microsoft Docs"
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
  - "getUTCMilliseconds"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "millisecondi"
  - "ora UTC, restituzione"
  - "getUTCMilliseconds (metodo)"
ms.assetid: 7491d387-7b6a-40df-89e5-55c64795ef70
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Metodo getUTCMilliseconds (Date) (JavaScript)
Ottiene i millisecondi di un oggetto `Date` utilizzo di tempo universale coordinato \(UTC\).  
  
## Sintassi  
  
```  
  
dateObj.getUTCMilliseconds()   
```  
  
#### Parametri  
 Il riferimento richiesto `dateObj` è un oggetto `Date`.  
  
## Valore restituito  
 Restituisce un valore millisecondi che può variare da 0\-999.  
  
## Note  
 Per ottenere il numero di millisecondi all'ora locale, utilizzare il metodo `getMilliseconds`.  
  
## Esempio  
 Nell'esempio riportato di seguito viene illustrato l'utilizzo del metodo `getUTCMilliseconds`.  
  
```javascript  
var date = new Date("1/1/2001");  
document.write(date.getUTCMilliseconds());  
document.write("<br/>");  
  
date.setMilliseconds(34);  
document.writedate.getUTCMilliseconds());  
  
// Output:  
// 0   
// 34   
```  
  
## Requisiti  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Applies To**: [Oggetto Date](../../javascript/reference/date-object-javascript.md)  
  
## Vedere anche  
 [Metodo getMilliseconds \(Date\)](../../javascript/reference/getmilliseconds-method-date-javascript.md)   
 [Metodo setMilliseconds \(Date\)](../../javascript/reference/setmilliseconds-method-date-javascript.md)   
 [Metodo setUTCMilliseconds \(Date\)](../../javascript/reference/setutcmilliseconds-method-date-javascript.md)