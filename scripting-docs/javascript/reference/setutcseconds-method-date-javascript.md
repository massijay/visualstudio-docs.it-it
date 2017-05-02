---
title: "Metodo setUTCSeconds (Date) (JavaScript) | Microsoft Docs"
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
  - "setUTCSeconds"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "date, UTC"
  - "seconds (metodo)"
  - "setUTCSeconds (metodo)"
  - "UTC (ora), impostazione"
ms.assetid: e035e282-b39d-4d1d-8771-c17542fd6493
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Metodo setUTCSeconds (Date) (JavaScript)
Consente di impostare il valore dei secondi nell'oggetto `Date` utilizzando il formato UTC \(Tempo universale coordinato, Universal Coordinated Time\).  
  
## Sintassi  
  
```  
  
dateObj.setUTCSeconds(numSeconds[, numMilli])   
```  
  
## Parametri  
 `dateObj`  
 Obbligatorio.  Qualsiasi oggetto `Date`.  
  
 *numSeconds*  
 Obbligatorio.  Valore numerico corrispondente ai secondi.  
  
 `numMilli`  
 Facoltativo.  Valore numerico corrispondente ai millisecondi.  
  
## Note  
 Per tutti i metodi **set** che prevedono argomenti facoltativi, se un argomento facoltativo non viene specificato, viene utilizzato il valore restituito dai corrispondenti metodi **get**.  Se, ad esempio, l'argomento `numMilli` non viene specificato, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] utilizza il valore restituito dal metodo `getUTCMilliseconds`.  
  
 Per impostare il valore dei secondi in base all'ora locale, utilizza il metodo `setSeconds`.  
  
 Se il valore di un argomento è maggiore del relativo intervallo o è un numero negativo, gli altri valori memorizzati verranno modificati di conseguenza.  Se, ad esempio, la data memorizzata è "5 gen 1996 00.00.00.00" e si richiama il metodo **setSeconds\(150\)**, la data verrà modificata in "5 gen 1996 00.02.30.00".  
  
 È possibile utilizzare il metodo **setUTCHours** per impostare le ore, i minuti, i secondi e i millisecondi.  
  
## Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo del metodo `setUTCSeconds`.  
  
```javascript  
function SetUTCSecondsDemo(nsec){  
// Create Date object.  
    var d = new Date();       
// Set UTC seconds.  
    d.setUTCSeconds(nsec);    
    var s = "Current setting is ";  
    s += d.toUTCString();  
// Return new setting.  
    return(s);                
}  
```  
  
## Requisiti  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Si applica a**: [Oggetto Date](../../javascript/reference/date-object-javascript.md)  
  
## Vedere anche  
 [Metodo getSeconds \(Date\)](../../javascript/reference/getseconds-method-date-javascript.md)   
 [Metodo getUTCSeconds \(Date\)](../../javascript/reference/getutcseconds-method-date-javascript.md)   
 [Metodo setSeconds \(Date\)](../../javascript/reference/setseconds-method-date-javascript.md)