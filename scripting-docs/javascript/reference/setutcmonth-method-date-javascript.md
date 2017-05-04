---
title: "Metodo setUTCMonth (Date) (JavaScript) | Microsoft Docs"
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
  - "setUTCMonth"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "date, UTC"
  - "Month (metodo)"
  - "setUTCMonth (metodo)"
  - "date UTC, impostazione"
ms.assetid: cdac5f64-c4fd-44cc-ba3a-9a8dd3dd3fad
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Metodo setUTCMonth (Date) (JavaScript)
Consente di impostare il valore del mese nell'oggetto `Date` utilizzando il formato UTC \(Universal Coordinated Time, Tempo universale coordinato\).  
  
## Sintassi  
  
```  
  
dateObj.setUTCMonth(numMonth[, dateVal])   
```  
  
## Parametri  
 `dateObj`  
 Obbligatorio.  Qualsiasi oggetto `Date`.  
  
 `numMonth`  
 Obbligatorio.  Valore numerico che rappresenta il mese.  Il valore di gennaio è 0 e i valori degli altri mesi sono impostati consecutivamente sui numeri successivi.  
  
 `dateVal`  
 Facoltativo.  Valore numerico corrispondente al giorno del mese.  Se omesso, verrà utilizzato il valore restituito da una chiamata al metodo `getUTCDate`.  
  
## Note  
 Per impostare il valore del mese in base all'ora locale, utilizzare il metodo `setMonth`.  
  
 Se il valore di `numMonth` è maggiore di 11 \(gennaio corrisponde a 0\) o è un numero negativo, il valore dell'anno memorizzato verrà incrementato o diminuito in modo appropriato.  Se, ad esempio, la data memorizzata è "5 gen 1996 00.00.00.00" e si chiama il metodo **setUTCMonth\(14\)**, la data verrà modificata in "5 mar 1997 00.00.00.00".  
  
 È possibile utilizzare il metodo **setUTCFullYear** per impostare l'anno, il mese e il giorno del mese.  
  
## Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo del metodo `setUTCMonth`.  
  
```javascript  
function SetUTCMonthDemo(newmonth){  
   var d, s;                       // Declare variables.  
   d = new Date();                 // Create Date object.  
   d.setUTCMonth(newmonth);        // Set UTC month.  
   s = "Current setting is ";  
   s += d.toUTCString();   
   return(s);                      // Return new setting.  
}  
```  
  
## Requisiti  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Si applica a**: [Oggetto Date](../../javascript/reference/date-object-javascript.md)  
  
## Vedere anche  
 [Metodo getMonth \(Date\)](../../javascript/reference/getmonth-method-date-javascript.md)   
 [Metodo getUTCMonth \(Date\)](../../javascript/reference/getutcmonth-method-date-javascript.md)   
 [Metodo setMonth \(Date\)](../../javascript/reference/setmonth-method-date-javascript.md)