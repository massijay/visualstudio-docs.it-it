---
title: "Metodo getSeconds (Date) (JavaScript) | Microsoft Docs"
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
  - "getSeconds"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "seconds (metodo)"
  - "GetSeconds (metodo)"
ms.assetid: 97b10674-af0b-4681-a846-38f972196501
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Metodo getSeconds (Date) (JavaScript)
Ottiene i secondi di un oggetto `Date`, utilizzando l'ora locale.  
  
## Sintassi  
  
```  
  
dateObj.getSeconds()   
```  
  
#### Parametri  
 Il riferimento richiesto `dateObj` è un oggetto `Date`.  
  
## Valore restituito  
 Restituisce un Integer compreso tra 0 e 59.  Zero viene restituito quando il tempo è minore di secondo nel minuto corrente.  Se un oggetto `Date` è stato creato senza specificare il tempo, il valore dei secondi è 0.  
  
## Note  
 Per ottenere il valore dei secondi utilizzando tempo universale coordinato \(UTC\), utilizzare il metodo `getUTCSeconds`.  
  
## Esempio  
 Nell'esempio seguente viene illustrato come utilizzare il metodo `getSeconds`.  
  
```javascript  
var date = new Date("1/1/2001");  
document.write(date.getSeconds());  
document.write("<br/>");  
  
date.setSeconds(5);  
document.write(date.getSeconds());  
  
// Output:  
// 0  
// 5  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **si applica a**: [Oggetto Date](../../javascript/reference/date-object-javascript.md)  
  
## Vedere anche  
 [Metodo getUTCSeconds \(Date\)](../../javascript/reference/getutcseconds-method-date-javascript.md)   
 [Metodo setSeconds \(Date\)](../../javascript/reference/setseconds-method-date-javascript.md)   
 [Metodo setUTCSeconds \(Date\)](../../javascript/reference/setutcseconds-method-date-javascript.md)