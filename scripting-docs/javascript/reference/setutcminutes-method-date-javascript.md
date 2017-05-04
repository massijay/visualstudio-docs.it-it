---
title: "Metodo setUTCMinutes (Date) (JavaScript) | Microsoft Docs"
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
  - "setUTCMinutes"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "date, UTC"
  - "minuti"
  - "setUTCMinutes (metodo)"
  - "UTC (ora), impostazione"
ms.assetid: 2415e788-6d28-46dd-a103-0931a1fd1446
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Metodo setUTCMinutes (Date) (JavaScript)
Consente di impostare il valore dei minuti nell'oggetto `Date` utilizzando il formato UTC \(Universal Coordinated Time, Tempo universale coordinato\).  
  
## Sintassi  
  
```  
  
dateObj.setUTCMinutes(numMinutes[, numSeconds[, numMilli]])   
```  
  
## Parametri  
 `dateObj`  
 Obbligatorio.  Qualsiasi oggetto `Date`.  
  
 `numMinutes`  
 Obbligatorio.  Valore numerico corrispondente ai minuti.  Obbligatorio se si utilizza uno degli argomenti seguenti.  
  
 *numSeconds*  
 Facoltativo.  Valore numerico corrispondente ai secondi.  Obbligatorio se si utilizza `numMilli`.  
  
 `numMilli`  
 Facoltativo.  Valore numerico corrispondente ai millisecondi.  
  
## Note  
 Per tutti i metodi **set** che prevedono argomenti facoltativi, se un argomento facoltativo non viene specificato, viene utilizzato il valore restituito dai corrispondenti metodi **get**.  Se, ad esempio, l'argomento *numSeconds* non viene specificato, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] utilizza il valore restituito dal metodo `getUTCSeconds`.  
  
 Per modificare il valore dei minuti in base all'ora locale, utilizzare il metodo `setMinutes`.  
  
 Se il valore di un argomento è maggiore del relativo intervallo o è un numero negativo, gli altri valori memorizzati verranno modificati di conseguenza.  Se, ad esempio, la data memorizzata è "5 gen 1996 00.00.00.00" e si chiama il metodo **setUTCMinutes\(70\)**, la data viene modificata in "5 gen 1996 01.10.00.00".  
  
 È possibile utilizzare il metodo **setUTCHours** per impostare le ore, i minuti, i secondi e i millisecondi.  
  
## Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo del metodo `setUTCMinutes`:  
  
```javascript  
function SetUTCMinutesDemo(nmin, nsec){  
   var d, s;                    // Declare variables.  
   d = new Date();              // Create Date object.  
   d.setUTCMinutes(nmin,nsec);  // Set UTC minutes.  
   s = "Current setting is " + d.toUTCString()   
   return(s);                   // Return new setting.  
}  
```  
  
## Requisiti  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Si applica a**: [Oggetto Date](../../javascript/reference/date-object-javascript.md)  
  
## Vedere anche  
 [Metodo getMinutes \(Date\)](../../javascript/reference/getminutes-method-date-javascript.md)   
 [Metodo getUTCMinutes \(Date\)](../../javascript/reference/getutcminutes-method-date-javascript.md)   
 [Metodo setMinutes \(Date\)](../../javascript/reference/setminutes-method-date-javascript.md)