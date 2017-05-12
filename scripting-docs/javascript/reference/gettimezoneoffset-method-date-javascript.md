---
title: "Metodo getTimezoneOffset (Date) (JavaScript) | Microsoft Docs"
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
  - "getTimeZoneOffset"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "getTimezoneOffset (metodo)"
  - "fusi orari [Visual Studio]"
ms.assetid: 58ee22b0-4688-45bd-a337-cc23119b09ce
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# Metodo getTimezoneOffset (Date) (JavaScript)
Ottiene la differenza, espressa in minuti, tra l'ora nel computer locale e l'ora UTC \(Universal Coordinated Time\).  
  
## Sintassi  
  
```  
  
dateObj.getTimezoneOffset()   
```  
  
#### Parametri  
 Il riferimento di `dateObj` obbligatorio è un oggetto `Date`.  
  
## Valore restituito  
 Restituisce il numero di minuti tra l'ora nel computer corrente \(il computer client o, se questo metodo viene chiamato da uno script server, il server\) e l'ora UTC.  Il numero è positivo se l'ora locale del computer corrente è posteriore all'ora UTC \(ad esempio, l'ora legale Pacifico\) e negativo se l'ora locale del computer corrente è antecedente all'ora UTC \(ad esempio il Giappone\).  Se un server a New York viene contattato da un client a Los Angeles il 1° dicembre, il metodo `getTimezoneOffset` restituisce il numero 480 se eseguito nel client oppure 300 se eseguito nel server.  
  
## Note  
  
## Esempio  
 Nell'esempio seguente viene illustrato come utilizzare il metodo `getTimezoneOffset`.  
  
```javascript  
var date =  new Date();  
var minutes = date.getTimezoneOffset();  
  
if (minutes < 0)  
    document.write(minutes / 60 + " hours after UTC");  
else  
    document.write(minutes / 60 + " hours before UTC");  
  
// Output (for example, where local time is PST):   
7 hours before UTC  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Si applica a**: [Oggetto Date](../../javascript/reference/date-object-javascript.md)  
  
## Vedere anche  
 [Metodo getTime \(Date\)](../../javascript/reference/gettime-method-date-javascript.md)