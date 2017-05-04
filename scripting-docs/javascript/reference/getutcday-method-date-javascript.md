---
title: "Metodo getUTCDay (Date) (JavaScript) | Microsoft Docs"
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
  - "getUTCDay"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Date (oggetto)"
  - "date, UTC"
  - "date UTC, restituzione"
  - "getUTCDay (metodo)"
ms.assetid: 2fceb5b0-6f77-4919-82c3-0877fd55bacb
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# Metodo getUTCDay (Date) (JavaScript)
Ottiene il giorno della settimana, secondo l'ora UTC.  
  
## Sintassi  
  
```  
  
dateObj.getUTCDay()   
```  
  
#### Parametri  
 Il riferimento di `dateObj` obbligatorio è un oggetto `Date`.  
  
## Valore restituito  
 Restituisce un intero compreso tra 0 \(domenica\) e 6 \(sabato\) che rappresenta il giorno della settimana.  
  
## Note  
 Per ottenere il giorno della settimana utilizzando l'ora locale, utilizza il metodo `getDate`.  
  
## Esempio  
 Nell'esempio seguente viene illustrato come utilizzare il metodo `getUTCDay`.  
  
```javascript  
var date = new Date("2/6/2001");  
var day = date.getUTCDay();  
document.write(day);  
  
// Output: 2  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Si applica a**: [Oggetto Date](../../javascript/reference/date-object-javascript.md)  
  
## Vedere anche  
 [Metodo getDay \(Date\)](../../javascript/reference/getday-method-date-javascript.md)