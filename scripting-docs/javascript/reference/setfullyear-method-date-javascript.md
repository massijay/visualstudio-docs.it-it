---
title: "Metodo setFullYear (Date) (JavaScript) | Microsoft Docs"
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
  - "setFullYear"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Year (metodo)"
  - "setFullYear (metodo)"
  - "date, impostazione"
ms.assetid: 635e4f5a-0210-4c01-8152-b0da4146f6ff
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# Metodo setFullYear (Date) (JavaScript)
Imposta l'anno dell'oggetto `Date` utilizzando l'ora locale.  
  
## Sintassi  
  
```  
  
dateObj.setFullYear(numYear[, numMonth[, numDate]])   
```  
  
## Parametri  
 `dateObj`  
 Obbligatorio.  Qualsiasi oggetto `Date`.  
  
 `numYear`  
 Obbligatorio.  Un valore numerico per l'anno.  
  
 `numMonth`  
 Parametro facoltativo.  Un valore numerico in base zero per il mese \(0 per gennaio 11, per dicembre\).  È possibile specificare se `numDate` è specificato.  
  
 `numDate`  
 Parametro facoltativo.  Un valore numerico uguale per il giorno del mese.  
  
## Note  
 Per tutti i metodi **set** che prevedono argomenti facoltativi, se un argomento facoltativo non viene specificato, verrà utilizzato il valore restituito dai corrispondenti metodi **get**.  Ad esempio, se l'argomento `numMonth` è facoltativo, ma non specificato, utilizzare che [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] il valore restituito dal metodo **getMonth**.  
  
 Inoltre, se il valore di un argomento è maggiore della porzione del calendario o è negativo, i rotoli data avanti o indietro in base alle proprie esigenze.  
  
 Per impostare l'anno utilizzo di tempo universale coordinato \(UTC\), utilizzare il metodo `setUTCFullYear`.  
  
 L'intervallo degli anni di supporto dell'oggetto data viene prima e dopo del 1970 di circa 285.616 anni.  
  
## Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo del metodo `setFullYear`.  
  
```javascript  
var date1 = new Date("1/1/2001");  
date1.setFullYear(2007);  
  
var date2 = new Date("1/1/2001");  
date2.setFullYear(2008, 10, 3);   
  
document.write (date1.toLocaleString());  
document.write ("<br />");  
document.write (date2.toLocaleString());  
  
// Output:  
// Monday, January 01, 2007 12:00:00 AM  
// Monday, November 03, 2008 12:00:00 AM  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Applies To**: [Oggetto Date](../../javascript/reference/date-object-javascript.md)  
  
## Vedere anche  
 [Metodo getFullYear \(Date\)](../../javascript/reference/getfullyear-method-date-javascript.md)   
 [Metodo getUTCFullYear \(Date\)](../../javascript/reference/getutcfullyear-method-date-javascript.md)   
 [Metodo setUTCFullYear \(Date\)](../../javascript/reference/setutcfullyear-method-date-javascript.md)