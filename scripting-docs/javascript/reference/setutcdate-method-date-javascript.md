---
title: "Metodo setUTCDate (Date) (JavaScript) | Microsoft Docs"
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
  - "setUTCDate"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "date, impostazione"
  - "date, UTC"
  - "setUTCDate (metodo)"
  - "date UTC, impostazione"
ms.assetid: e6c3b876-70fe-4103-b197-6c84c078ce10
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# Metodo setUTCDate (Date) (JavaScript)
Imposta il valore numerico del giorno del mese nell'oggetto `Date` in base al formato UTC \(Universal Coordinated Time\).  
  
## Sintassi  
  
```  
  
dateObj.setUTCDate(numDate)   
```  
  
## Parametri  
 `dateObj`  
 Obbligatorio.  Qualsiasi oggetto `Date`.  
  
 *numDate*  
 Obbligatorio.  Valore numerico corrispondente al giorno del mese.  
  
## Note  
 Per impostare il giorno del mese utilizzando l'ora locale, utilizzare il metodo `setDate`.  
  
 Se il valore di *numDate* è maggiore del numero di giorni del mese memorizzato nell'oggetto **Date** o è un numero negativo, la data verrà impostato su una data uguale a *numDate* meno il numero di giorni del mese memorizzato.  Se, ad esempio, la data memorizzata è 5 gennaio 1996 e si richiama il metodo **setUTCDate\(32\)**, la data verrà modificata in 1 febbraio 1996.  I numeri negativi vengono modificati nello stesso modo.  
  
 È possibile utilizzare il metodo **setUTCFullYear** per impostare l'anno, il mese e il giorno del mese.  
  
## Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo del metodo `setUTCDate`.  
  
```javascript  
function SetUTCDateDemo(newdayofmonth){  
   var d = new Date();           // Create Date object.  
   d.setUTCDate(newdayofmonth);  // Set UTC day of month.  
   var s = "Current setting is ";  
   s += d.toUTCString();   
   return(s);                    // Return new setting.  
}  
```  
  
## Requisiti  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Si applica a**: [Oggetto Date](../../javascript/reference/date-object-javascript.md)  
  
## Vedere anche  
 [Metodo getDate \(Date\)](../../javascript/reference/getdate-method-date-javascript.md)   
 [Metodo getUTCDate \(Date\)](../../javascript/reference/getutcdate-method-date-javascript.md)   
 [Metodo setDate \(Date\)](../../javascript/reference/setdate-method-date-javascript.md)