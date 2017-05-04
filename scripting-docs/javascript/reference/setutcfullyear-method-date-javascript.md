---
title: "Metodo setUTCFullYear (Date) (JavaScript) | Microsoft Docs"
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
  - "setUTCFullYear"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "date, UTC"
  - "setUTCFullYear (metodo)"
  - "date UTC, impostazione"
ms.assetid: e6c51b49-0149-4f9a-aa74-c73c0306f98e
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Metodo setUTCFullYear (Date) (JavaScript)
Imposta il valore dell'anno nell'oggetto `Date` in base al formato UTC \(Universal Coordinated Time\).  
  
## Sintassi  
  
```  
  
dateObj.setUTCFullYear(numYear[, numMonth[, numDate]])   
```  
  
## Parametri  
 `dateObj`  
 Obbligatorio.  Qualsiasi oggetto `Date`.  
  
 `numYear`  
 Obbligatorio.  Valore numerico corrispondente all'anno.  
  
 `numMonth`  
 Facoltativo.  Valore numerico che rappresenta il mese.  Il valore di gennaio è 0 e i valori degli altri mesi sono impostati consecutivamente sui numeri successivi.  Obbligatorio se viene specificato *numDate*.  
  
 *numDate*  
 Facoltativo.  Valore numerico corrispondente al giorno del mese.  
  
## Note  
 Per tutti i metodi **set** che prevedono argomenti facoltativi, se un argomento facoltativo non viene specificato, viene utilizzato il valore restituito dai corrispondenti metodi **get**.  Se, ad esempio, l'argomento `numMonth` non viene specificato, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] utilizza il valore restituito dal metodo `getUTCMonth`.  
  
 Inoltre, se il valore di un argomento è maggiore del relativo intervallo o è un numero negativo, gli altri valori memorizzati verranno modificati di conseguenza.  
  
 Per impostare l'anno utilizzando l'ora locale, utilizza il metodo `setFullYear`.  
  
 L'intervallo di anni supportato dall'oggetto `Date` è compreso approssimativamente tra 285.616 anni prima e 285.616 anni dopo il 1970.  
  
## Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo del metodo `setUTCFullYear`.  
  
```javascript  
var dtFirst = new Date();  
dtFirst.setUTCFullYear(2007);  
  
var dtSecond = new Date();  
// 10 is the value for November.   
dtSecond.setUTCFullYear(2008, 10, 3);   
  
document.write (dtFirst.toUTCString());  
document.write ("<br />");  
document.write (dtSecond.toUTCString());  
```  
  
## Requisiti  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Si applica a**: [Oggetto Date](../../javascript/reference/date-object-javascript.md)  
  
## Vedere anche  
 [Metodo getFullYear \(Date\)](../../javascript/reference/getfullyear-method-date-javascript.md)   
 [Metodo getUTCFullYear \(Date\)](../../javascript/reference/getutcfullyear-method-date-javascript.md)   
 [Metodo setFullYear \(Date\)](../../javascript/reference/setfullyear-method-date-javascript.md)