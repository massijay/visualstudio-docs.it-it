---
title: "Metodo getDate (Date) (JavaScript) | Microsoft Docs"
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
  - "getDate"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Date (oggetto)"
  - "date, restituzione giorno del mese"
  - "getDate (metodo)"
ms.assetid: 67e7f07c-dd46-4b42-82d6-e53e4bd33703
caps.latest.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 20
---
# Metodo getDate (Date) (JavaScript)
Ottiene il giorno del mese sulla base dell'ora locale.  
  
## Sintassi  
  
```  
  
dateObj.getDate()   
```  
  
#### Parametri  
 Il riferimento di `dateObj` obbligatorio è un oggetto `Date`.  
  
## Valore restituito  
 Intero compreso tra 1 e 31 che rappresenta il giorno del mese.  
  
## Note  
 Per ottenere il giorno del mese in base al formato UTC \(Universal Coordinated Time, Tempo universale coordinato\), utilizza il metodo `getUTCDate`.  
  
## Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo del metodo `getDate`.  
  
```javascript  
var date = new Date("Jan 01, 2001");  
var str = "Today's date is: ";  
   str += (date.getMonth() + 1) + "/";  
   str += date.getDate() + "/";  
   str += date.getFullYear();  
document.write(str);  
  
// Output: Today's date is: 1/1/2001  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Si applica a**: [Oggetto Date](../../javascript/reference/date-object-javascript.md)  
  
## Vedere anche  
 [Metodo getUTCDate \(Date\)](../../javascript/reference/getutcdate-method-date-javascript.md)   
 [Metodo setDate \(Date\)](../../javascript/reference/setdate-method-date-javascript.md)   
 [Metodo setUTCDate \(Date\)](../../javascript/reference/setutcdate-method-date-javascript.md)