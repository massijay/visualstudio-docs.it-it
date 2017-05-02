---
title: "Metodo getFullYear (Date) (JavaScript) | Microsoft Docs"
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
  - "getFullYear"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "date, restituzione anno"
  - "Date (oggetto)"
  - "getFullYear (metodo)"
ms.assetid: f9ec1262-02e9-4791-90b5-48f33b1dc4bc
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# Metodo getFullYear (Date) (JavaScript)
Ottiene l'anno in base all'ora locale.  
  
## Sintassi  
  
```  
  
dateObj.getFullYear()   
```  
  
#### Parametri  
 Il riferimento di `dateObj` obbligatorio è un oggetto `Date`.  
  
## Valore restituito  
 Anno, come numero a quattro cifre.  L'anno 1976, ad esempio, viene restituito in forma di numero a quattro cifre.  Gli anni specificati con due cifre nel costruttore `Date` o in `setFullYear` vengono considerati appartenenti al XX secolo, quindi dato "5\/14\/12", `getFullYear` restituirà "1912".  
  
## Note  
 Per ottenere l'anno in base al formato UTC \(Universal Coordinated Time, Tempo universale coordinato\), utilizzare il metodo `getUTCFullYear`.  
  
## Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo del metodo **getFullYear**.  
  
```javascript  
var date = new Date("1/1/01");  
document.write(date.getFullYear());  
  
// Output: 1901  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Si applica a**: [Oggetto Date](../../javascript/reference/date-object-javascript.md)  
  
## Vedere anche  
 [Metodo getUTCFullYear \(Date\)](../../javascript/reference/getutcfullyear-method-date-javascript.md)   
 [Metodo setFullYear \(Date\)](../../javascript/reference/setfullyear-method-date-javascript.md)   
 [Metodo setUTCFullYear \(Date\)](../../javascript/reference/setutcfullyear-method-date-javascript.md)