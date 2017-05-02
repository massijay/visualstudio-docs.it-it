---
title: "Funzione Date.parse (JavaScript) | Microsoft Docs"
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
  - "parse"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Date.parse (funzione) [JavaScript]"
  - "parse (funzione) [JavaScript]"
ms.assetid: ed737e50-6398-4462-8779-2af3c03f8325
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# Funzione Date.parse (JavaScript)
Analizza una stringa contenente una data e restituisce il numero di millisecondi compresi tra tale data e la mezzanotte dell'1 gennaio 1970.  
  
## Sintassi  
  
```  
Date.parse(dateVal)   
```  
  
## Note  
 L'argomento obbligatorio `dateVal` è una stringa contenente una data o un valore VT\_DATE recuperato da un oggetto ActiveX o da un altro oggetto.  Per informazioni sulle stringhe di data che la funzione `Date.parse` può analizzare, vedere [Stringhe di data e ora](../../javascript/date-and-time-strings-javascript.md).  
  
 La funzione `Date.parse` restituisce un valore intero che rappresenta il numero di millisecondi compresi tra la mezzanotte dell'1 gennaio 1970 e la data specificata in `dateVal`.  
  
## Esempio  
 Nel seguente esempio viene illustrato l'utilizzo della funzione `Date.parse`:  
  
```javascript  
var dateString = "November 1, 1997 10:15 AM";  
var mSec = Date.parse(dateString);  
document.write(mSec);  
// Output: 878404500000  
```  
  
## Esempio  
 L'esempio seguente restituisce la differenza tra la data specificata e 1\/1\/1970.  
  
```javascript  
var minMilli = 1000 * 60;  
var hrMilli = minMilli * 60;  
var dyMilli = hrMilli * 24;  
  
var testDate = new Date("June 1, 1990");  
var ms = Date.parse(testDate);  
var days = Math.round(ms / dyMilli);  
  
var dateStr = "";  
dateStr += "There are " + days + " days ";  
dateStr += "between 01/01/1970 and " + testDate;  
document.write(dateStr);  
  
// Output: There are 7456 days between 01/01/1970 and Fri Jun 1 00:00:00 PDT 1990  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Vedere anche  
 [Metodo getDate \(Date\)](../../javascript/reference/getdate-method-date-javascript.md)