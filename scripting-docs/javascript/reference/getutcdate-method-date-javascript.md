---
title: "Metodo getUTCDate (Date) (JavaScript) | Microsoft Docs"
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
  - "getUTCDate"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Date (oggetto)"
  - "date, UTC"
  - "date UTC, restituzione"
  - "getUTCDate (metodo)"
ms.assetid: 9e4c763f-c94c-44c9-9684-cb632d75b62e
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Metodo getUTCDate (Date) (JavaScript)
Ottiene il giorno del mese, secondo l'ora UTC.  
  
## Sintassi  
  
```  
  
dateObj.getUTCDate()   
```  
  
#### Parametri  
 Il riferimento di `dateObj` obbligatorio è un oggetto `Date`.  
  
## Valore restituito  
 Restituisce un intero compreso tra 1 e 31 che rappresenta il giorno del mese.  
  
## Note  
 Per ottenere il giorno del mese utilizzando l'ora locale, utilizzare il metodo `getDate`.  
  
## Esempio  
 Nell'esempio seguente viene illustrato come utilizzare il metodo `getUTCDate`.  
  
```javascript  
var date = new Date("1/23/2001");  
document.write(date.getUTCDate());  
  
// Output: 23  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Si applica a**: [Oggetto Date](../../javascript/reference/date-object-javascript.md)  
  
## Vedere anche  
 [Metodo getDate \(Date\)](../../javascript/reference/getdate-method-date-javascript.md)   
 [Metodo setDate \(Date\)](../../javascript/reference/setdate-method-date-javascript.md)   
 [Metodo setUTCDate \(Date\)](../../javascript/reference/setutcdate-method-date-javascript.md)