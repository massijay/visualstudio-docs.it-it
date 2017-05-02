---
title: "Metodo setSeconds (Date) (JavaScript) | Microsoft Docs"
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
  - "setSeconds"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "seconds (metodo)"
  - "setSeconds (metodo)"
ms.assetid: 986ffa54-1db6-4af2-ab8b-8353f64f0b57
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# Metodo setSeconds (Date) (JavaScript)
Consente di impostare il valore dei secondi nell'oggetto `Date` utilizzando l'ora locale.  
  
## Sintassi  
  
```  
  
dateObj  
.setSeconds(  
numSeconds[, numMilli])   
```  
  
## Parametri  
 `dateObj`  
 Obbligatorio.  Qualsiasi oggetto `Date`.  
  
 *numSeconds*  
 Obbligatorio.  Valore numerico corrispondente ai secondi.  
  
 `numMilli`  
 Facoltativo.  Valore numerico corrispondente ai millisecondi.  
  
## Note  
 Per tutti i metodi **set** che prevedono argomenti facoltativi, se un argomento facoltativo non viene specificato, viene utilizzato il valore restituito dai corrispondenti metodi **get**.  Se, ad esempio, l'argomento `numMilli` non viene specificato, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] utilizza il valore restituito dal metodo **getMilliseconds**.  
  
 Per impostare il valore dei secondi utilizzando il formato UTC \(Universal Coordinated Time, Tempo universale coordinato\), impiegare il metodo `setUTCSeconds`.  
  
 Se il valore di un argomento è maggiore del relativo intervallo o è un numero negativo, gli altri valori memorizzati verranno modificati di conseguenza.  Se, ad esempio, la data memorizzata è "5 gen 1996 00.00.00" e si chiama il metodo **setSeconds\(150\)**, la data verrà modificata in "5 gen 1996 00.02.30".  
  
 È possibile utilizzare il metodo `setHours` per impostare le ore, i minuti, i secondi e i millisecondi.  
  
## Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo del metodo `setSeconds`.  
  
```javascript  
function SetSecondsDemo(nsec){  
   var d = new Date();         //Create Date object.  
   d.setSeconds(nsec);         //Set seconds.  
   var s = "Current setting is ";  
   s += d.toLocaleString();  
   return(s);                  //Return new setting.  
}  
```  
  
## Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Si applica a**: [Oggetto Date](../../javascript/reference/date-object-javascript.md)  
  
## Vedere anche  
 [Metodo getSeconds \(Date\)](../../javascript/reference/getseconds-method-date-javascript.md)   
 [Metodo getUTCSeconds \(Date\)](../../javascript/reference/getutcseconds-method-date-javascript.md)   
 [Metodo setUTCSeconds \(Date\)](../../javascript/reference/setutcseconds-method-date-javascript.md)