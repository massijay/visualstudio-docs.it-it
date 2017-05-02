---
title: "Metodo setMonth (Date) (JavaScript) | Microsoft Docs"
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
  - "setMonth"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Month (metodo)"
  - "setMonth (metodo)"
ms.assetid: 4f5be295-d536-46c0-b3a4-ad06457efe82
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# Metodo setMonth (Date) (JavaScript)
Imposta il valore del mese nell'oggetto `Date` utilizzando l'ora locale.  
  
## Sintassi  
  
```  
  
dateObj. setMonth(numMonth[, dateVal])   
```  
  
## Parametri  
 `dateObj`  
 Obbligatorio.  Qualsiasi oggetto `Date`.  
  
 `numMonth`  
 Obbligatorio.  Valore numerico che rappresenta il mese.  Il valore di gennaio è 0 e i valori degli altri mesi sono impostati consecutivamente sui numeri successivi.  
  
 `dateVal`  
 Facoltativo.  Valore numerico corrispondente al giorno del mese.  Se omesso, verrà utilizzato il valore restituito da una chiamata al metodo `getDate`.  
  
## Note  
 Per impostare il valore del mese in base al formato UTC \(Universal Coordinated Time, Tempo universale coordinato\), utilizzare il metodo `setUTCMonth`.  
  
 Se il valore di `numMonth` è maggiore di 11 \(gennaio corrisponde a 0\) o è un numero negativo, l'anno memorizzato verrà modificato di conseguenza.  Se, ad esempio, la data memorizzata è "5 gen 1996" e si chiama il metodo **setMonth\(14\)**, la data verrà modificata in "5 mar 1997".  
  
 È possibile utilizzare il metodo **setFullYear** per impostare l'anno, il mese e il giorno del mese.  
  
## Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo del metodo `setMonth`.  
  
```javascript  
date = new Date('1/1/1990');  
date.setMonth(14);  
document.write(date);  
  
// Output: Fri Mar 1 00:00:00 PST 1991  
// Note that the time zone corresponds to the time zone on the local computer.  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Si applica a**: [Oggetto Date](../../javascript/reference/date-object-javascript.md)  
  
## Vedere anche  
 [Metodo getMonth \(Date\)](../../javascript/reference/getmonth-method-date-javascript.md)   
 [Metodo getUTCMonth \(Date\)](../../javascript/reference/getutcmonth-method-date-javascript.md)   
 [Metodo setUTCMonth \(Date\)](../../javascript/reference/setutcmonth-method-date-javascript.md)