---
title: "Metodo getUTCMinutes (Date) (JavaScript) | Microsoft Docs"
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
  - "getUTCMinutes"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "minuti"
  - "ora UTC, restituzione"
  - "getUTCMinutes (metodo)"
ms.assetid: b6d92543-b285-4e46-8f47-bba36e53fabd
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Metodo getUTCMinutes (Date) (JavaScript)
Ottiene i minuti di un oggetto `Date` utilizzo di tempo universale coordinato \(UTC\).  
  
## Sintassi  
  
```  
  
dateObj.getUTCMinutes()   
```  
  
#### Parametri  
 Il riferimento richiesto `dateObj` è un oggetto `Date`.  
  
## Valore restituito  
 Restituisce un Integer compreso tra 0 e 59.  Zero viene restituito il tempo è minore di un minuto all'ora.  Se un oggetto `Date` è stato creato senza specificare il tempo, il valore dei minuti UTC è 0.  Tuttavia, in altri fusi orari sia diverso.  
  
## Note  
 Per ottenere il numero di minuti memorizzato in base all'ora locale, è possibile utilizzare il metodo `getMinutes`.  
  
## Esempio  
 Nell'esempio riportato di seguito viene illustrato l'utilizzo del metodo `getUTCMinutes`.  
  
```javascript  
var date = new Date("1/1/2001");  
document.write(date.getUTCMinutes());  
document.write("<br/>");  
  
date.setMinutes(5);  
document.write(date.getUTCMinutes());  
  
// Output:   
// 0  
// 5  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Applies To**: [Oggetto Date](../../javascript/reference/date-object-javascript.md)  
  
## Vedere anche  
 [Metodo getMinutes \(Date\)](../../javascript/reference/getminutes-method-date-javascript.md)   
 [Metodo setMinutes \(Date\)](../../javascript/reference/setminutes-method-date-javascript.md)   
 [Metodo setUTCMinutes \(Date\)](../../javascript/reference/setutcminutes-method-date-javascript.md)