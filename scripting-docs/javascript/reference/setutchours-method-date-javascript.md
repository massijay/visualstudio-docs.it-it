---
title: "Metodo setUTCHours (Date) (JavaScript) | Microsoft Docs"
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
  - "setUTCHours"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "date, UTC"
  - "setUTCHours (metodo)"
  - "UTC (ora), impostazione"
ms.assetid: 257e36fd-fb06-4a4d-8634-d66a020a1511
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Metodo setUTCHours (Date) (JavaScript)
Consente di impostare il valore delle ore nell'oggetto `Date` in base al formato UTC \(Universal Coordinated Time, Tempo universale coordinato\).  
  
## Sintassi  
  
```  
  
dateObj.setUTCHours(numHours[, numMin[, numSec[, numMilli]]])   
```  
  
## Parametri  
 `dateObj`  
 Obbligatorio.  Qualsiasi oggetto `Date`.  
  
 `numHours`  
 Obbligatorio.  Valore numerico che rappresenta le ore.  
  
 `numMin`  
 Facoltativo.  Valore numerico corrispondente ai minuti.  Obbligatorio se viene utilizzato `numSec` o `numMilli`.  
  
 `numSec`  
 Facoltativo.  Valore numerico corrispondente ai secondi.  Obbligatorio se viene utilizzato l'argomento `numMilli`.  
  
 `numMilli`  
 Facoltativo.  Valore numerico corrispondente ai millisecondi.  
  
## Note  
 Per tutti i metodi **set** che prevedono argomenti facoltativi, se un argomento facoltativo non viene specificato, viene utilizzato il valore restituito dai corrispondenti metodi **get**.  Se, ad esempio, l'argomento `numMin` non viene specificato, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] utilizza il valore restituito dal metodo `getUTCMinutes`.  
  
 Per impostare il valore delle ore in base all'ora locale, utilizzare il metodo `setHours`.  
  
 Se il valore di un argomento è maggiore del relativo intervallo o è un numero negativo, gli altri valori memorizzati verranno modificati di conseguenza.  Se, ad esempio, la data memorizzata è "5 gen 1996 00.00.00.00" e si chiama il metodo **setUTCHours\(30\)**, la data viene modificata in "6 gen 1996 06.00.00.00".  
  
## Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo del metodo `setUTCHours`.  
  
```javascript  
function SetUTCHoursDemo(nhr, nmin, nsec){     
   var d, s;                        // Declare variables.  
   d = new Date();                  // Create Date object.  
   d.setUTCHours(nhr, nmin, nsec);  // Set UTC hours, minutes, seconds.  
   s = "Current setting is " + d.toUTCString()   
   return(s);                       // Return new setting.  
}  
```  
  
## Requisiti  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Si applica a**: [Oggetto Date](../../javascript/reference/date-object-javascript.md)  
  
## Vedere anche  
 [Metodo getHours \(Date\)](../../javascript/reference/gethours-method-date-javascript.md)   
 [Metodo getUTCHours \(Date\)](../../javascript/reference/getutchours-method-date-javascript.md)   
 [Metodo setHours \(Date\)](../../javascript/reference/sethours-method-date-javascript.md)