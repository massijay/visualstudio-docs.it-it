---
title: "Metodo getUTCFullYear (Date) (JavaScript) | Microsoft Docs"
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
  - "getUTCFullYear"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "getUTCFullYear (metodo)"
  - "Date (oggetto)"
  - "UTCFullYear (metodo)"
  - "date, UTC"
  - "date UTC, restituzione"
  - "Full Year (metodo)"
  - "date UTC, recupero"
ms.assetid: f11e5363-ef8a-48dd-9d56-4ee7290c7c48
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Metodo getUTCFullYear (Date) (JavaScript)
Ottiene l'anno secondo l'ora UTC.  
  
## Sintassi  
  
```  
  
dateObj.getUTCFullYear()   
```  
  
#### Parametri  
 Il riferimento di `dateObj` obbligatorio è un oggetto `Date`.  
  
## Valore restituito  
 Restituisce l'anno come numero a quattro cifre.  Gli anni specificati con due cifre nel costruttore `Date` o in `setFullYear` vengono considerati appartenenti al XX secolo, quindi dato "5\/14\/12", `getUTCFullYear` restituirà "1912".  
  
## Note  
 Per ottenere l'anno utilizzando l'ora locale, è possibile utilizzare il metodo `getFullYear`.  
  
## Esempio  
 Nell'esempio seguente viene illustrato come utilizzare il metodo `getUTCFullYear`.  
  
```javascript  
var date = new Date("1/9/36");  
document.write(date.getUTCFullYear());  
  
// Output: 1936  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Si applica a**: [Oggetto Date](../../javascript/reference/date-object-javascript.md)  
  
## Vedere anche  
 [Metodo getFullYear \(Date\)](../../javascript/reference/getfullyear-method-date-javascript.md)   
 [Metodo setFullYear \(Date\)](../../javascript/reference/setfullyear-method-date-javascript.md)   
 [Metodo setUTCFullYear \(Date\)](../../javascript/reference/setutcfullyear-method-date-javascript.md)