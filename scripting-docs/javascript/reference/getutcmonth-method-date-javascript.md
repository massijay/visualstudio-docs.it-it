---
title: "Metodo getUTCMonth (Date) (JavaScript) | Microsoft Docs"
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
  - "getUTCMonth"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "date, UTC"
  - "date UTC, restituzione"
  - "Month (metodo)"
  - "getUTCMonth (metodo)"
ms.assetid: eabae139-4da0-4e4a-a4cb-608e6375fc9e
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Metodo getUTCMonth (Date) (JavaScript)
Ottiene il mese di un oggetto `Date` utilizzo di tempo universale coordinato \(UTC\).  
  
## Sintassi  
  
```  
  
dateObj.getUTCMonth()   
```  
  
#### Parametri  
 Il riferimento richiesto `dateObj` è un oggetto `Date`.  
  
## Valore restituito  
 Restituisce un Integer compreso tra 0 \(gennaio 11\) e \(dicembre\).  
  
## Note  
 Per ottenere il mese in base all'ora locale, è possibile utilizzare il metodo **getMonth**.  
  
## Esempio  
 Nell'esempio seguente viene illustrato come utilizzare il metodo `getUTCMonth`.  
  
```javascript  
var date = new Date("2/2/2002");  
document.write(date.getUTCMonth());  
  
// Output: 1  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Applies To**: [Oggetto Date](../../javascript/reference/date-object-javascript.md)  
  
## Vedere anche  
 [Metodo getMonth \(Date\)](../../javascript/reference/getmonth-method-date-javascript.md)   
 [Metodo setMonth \(Date\)](../../javascript/reference/setmonth-method-date-javascript.md)   
 [Metodo setUTCMonth \(Date\)](../../javascript/reference/setutcmonth-method-date-javascript.md)