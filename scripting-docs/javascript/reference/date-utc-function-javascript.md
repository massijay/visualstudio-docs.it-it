---
title: "Funzione Date.UTC (JavaScript) | Microsoft Docs"
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
  - "UTC"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "UTC (funzione) [JavaScript]"
  - "date UTC, restituzione"
  - "Date.UTC (funzione) [JavaScript]"
ms.assetid: c0d67ce1-a47e-4dfd-bbf4-21619c406a0f
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# Funzione Date.UTC (JavaScript)
Restituisce il numero di millisecondi che intercorrono tra la mezzanotte dell'1 gennaio 1970, data espressa in formato UTC \(Universal Coordinated Time\) o GMT, e la data specificata.  
  
## Sintassi  
  
```  
Date.UTC(year, month, day[, hours[, minutes[, seconds[,ms]]]])   
```  
  
## Parametri  
 `year`  
 Obbligatorio.  La designazione completa dell'anno è necessaria per garantire che le date a cavallo di due secoli vengano restituite nel modo corretto.  Se per `year` viene specificato un valore compreso tra 0 e 99, il valore dell'argomento `year` verrà interpretato come 1900 \+ `year`.  
  
 `month`  
 Obbligatorio.  Numero intero compreso tra 0 e 11, da gennaio a dicembre, che rappresenta il mese.  
  
 `day`  
 Obbligatorio.  Numero intero compreso tra 1 e 31 che rappresenta il giorno.  
  
 `hours`  
 Facoltativo.  Obbligatorio se si specifica `minutes`.  Numero intero compreso tra 0 e 23, da mezzanotte alle 23.00, che rappresenta l'ora.  
  
 `minutes`  
 Facoltativo.  Obbligatorio se si specifica `seconds`.  Numero intero compreso tra 0 e 59 che rappresenta i minuti.  
  
 `seconds`  
 Facoltativo.  Obbligatorio se si specifica `milliseconds`.  Numero intero compreso tra 0 e 59 che rappresenta i secondi.  
  
 `ms`  
 Facoltativo.  Numero intero compreso tra 0 e 999 che rappresenta i millisecondi.  
  
## Note  
 La funzione `Date.UTC` restituisce il numero di millisecondi tra la mezzanotte dell'1 gennaio 1970 espressa in formato UTC e la data specificata.  Il valore restituito può essere utilizzato nel metodo `setTime` e nel costruttore dell'oggetto `Date`.  Se il valore di un argomento è maggiore del relativo intervallo o è un numero negativo, gli altri valori memorizzati verranno modificati di conseguenza.  Se si specifica 150 secondi, ad esempio, in [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] il numero verrà convertito in due minuti e 30 secondi.  
  
 La funzione `Date.UTC` e il costruttore dell'oggetto `Date` che accetta una data si differenziano per il fatto che la funzione `Date.UTC` presuppone il formato UTC e il costruttore dell'oggetto `Date` presuppone l'ora locale.  
  
## Esempio  
 Nel seguente esempio viene illustrato l'utilizzo della funzione `Date.UTC`.  
  
```javascript  
// Determine the milliseconds per day.  
 var MinMilli = 1000 * 60;  
var HrMilli = MinMilli * 60;  
var DyMilli = HrMilli * 24;  
  
var date = new Date("June 1, 1990");  
var year = date.getFullYear();  
var month = date.getMonth();  
var day = date.getDay();  
  
var newDay = new Date("January 16, 2020");  
var yeartoday = newDay.getUTCFullYear();  
var monthtoday = newDay.getUTCMonth();  
var dayofmonthtoday = newDay.getUTCDate();  
  
// Get the milliseconds since 1/1/1970 UTC.  
var t1 = Date.UTC(year, month - 1, day)  
var t2 = Date.UTC(yeartoday, monthtoday, dayofmonthtoday);  
  
// Determine the difference in days.  
var days = (t2 - t1) / DyMilli;  
  
document.write(days);  
// Output: 10848  
```  
  
## Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Vedere anche  
 [Metodo setTime \(Date\)](../../javascript/reference/settime-method-date-javascript.md)