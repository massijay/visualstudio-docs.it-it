---
title: "Metodo getMonth (Date) (JavaScript) | Microsoft Docs"
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
  - "getMonth"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Date (oggetto)"
  - "date, valore mese"
  - "Month (metodo)"
  - "GetMonth (metodo)"
ms.assetid: c20dd8ba-1d78-42f1-8717-ed3dfd2362dd
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# Metodo getMonth (Date) (JavaScript)
Ottiene il mese in base all'ora locale.  
  
## Sintassi  
  
```  
  
dateObj.getMonth()   
```  
  
#### Parametri  
 Il riferimento di `dateObj` obbligatorio è un oggetto `Date`.  
  
## Valore restituito  
 Il metodo `getMonth` restituisce un intero compreso tra 0 \(gennaio\) e 11 \(dicembre\).  Per un oggetto `Date` costruito con "Gen 5, 1996", `getMonth` restituisce 0.  
  
## Note  
 Per ottenere il valore del mese in base al formato UTC \(Universal Coordinated Time\), utilizza il metodo `getUTCMonth`.  
  
## Esempio  
 Nell'esempio seguente viene illustrato come utilizzare il metodo `getMonth`.  
  
```javascript  
var date = new Date("1/1/2001");  
document.write(date.getMonth());  
  
// Output: 0  
```  
  
## Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Si applica a**: [Oggetto Date](../../javascript/reference/date-object-javascript.md)  
  
## Vedere anche  
 [Metodo getUTCMonth \(Date\)](../../javascript/reference/getutcmonth-method-date-javascript.md)   
 [Metodo setMonth \(Date\)](../../javascript/reference/setmonth-method-date-javascript.md)   
 [Metodo setUTCMonth \(Date\)](../../javascript/reference/setutcmonth-method-date-javascript.md)