---
title: "Metodo setHours (Date) (JavaScript) | Microsoft Docs"
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
  - "setHours"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "date, impostazione"
  - "ore"
  - "setHours (metodo)"
ms.assetid: 460f742d-f8d2-4874-9d07-2fb969fef066
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Metodo setHours (Date) (JavaScript)
Consente di impostare il valore delle ore nell'oggetto `Date` utilizzando l'ora locale.  
  
## Sintassi  
  
```  
  
dateObj.setHours(numHours[, numMin[, numSec[, numMilli]]])   
```  
  
## Parametri  
 `dateObj`  
 Obbligatorio.  Qualsiasi oggetto `Date`.  
  
 `numHours`  
 Obbligatorio.  Valore numerico che rappresenta le ore.  
  
 `numMin`  
 Facoltativo.  Valore numerico corrispondente ai minuti.  Obbligatorio se si utilizza uno degli argomenti seguenti.  
  
 `numSec`  
 Facoltativo.  Valore numerico corrispondente ai secondi.  Obbligatorio se viene utilizzato l'argomento seguente.  
  
 `numMilli`  
 Facoltativo.  Valore numerico corrispondente ai millisecondi.  
  
## Note  
 Per tutti i metodi **set** che prevedono argomenti facoltativi, se un argomento facoltativo non viene specificato, viene utilizzato il valore restituito dai corrispondenti metodi **get**.  Se, ad esempio, l'argomento `numMinutes` non viene specificato, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] utilizza il valore restituito dal metodo `getMinutes`.  
  
 Per impostare il valore delle ore in base al formato UTC \(Universal Coordinated Time, Tempo universale coordinato\), utilizzare il metodo `setUTCHours`.  
  
 Se il valore di un argomento è maggiore del relativo intervallo o è un numero negativo, gli altri valori memorizzati verranno modificati di conseguenza.  Se, ad esempio, la data memorizzata è "5 gen 1996 00.00.00" e si chiama il metodo **setHours\(30\)**, la data viene modificata in "6 gen 1996 06.00.00". I numeri negativi vengono modificati nello stesso modo.  
  
## Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo del metodo `setHours`.  
  
```javascript  
function SetHoursDemo(nhr, nmin, nsec){  
   var d, s;                     //Declare variables.  
   d = new Date();               //Create Date object.  
   d.setHours(nhr, nmin, nsec);  //Set hours, minutes, & seconds.  
   s = "Current setting is " + d.toLocaleString()   
   return(s);                    //Return new date setting.  
}  
```  
  
## Requisiti  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Si applica a**: [Oggetto Date](../../javascript/reference/date-object-javascript.md)  
  
## Vedere anche  
 [Metodo getHours \(Date\)](../../javascript/reference/gethours-method-date-javascript.md)   
 [Metodo getUTCHours \(Date\)](../../javascript/reference/getutchours-method-date-javascript.md)   
 [Metodo setUTCHours \(Date\)](../../javascript/reference/setutchours-method-date-javascript.md)