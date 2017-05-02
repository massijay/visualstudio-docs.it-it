---
title: "Metodo getTime (Date) (JavaScript) | Microsoft Docs"
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
  - "getTime"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "GetTime (metodo)"
  - "time (metodo)"
ms.assetid: f0da1d4e-337c-497d-9205-093defbc6d3d
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Metodo getTime (Date) (JavaScript)
Ottiene il valore di ora in millisecondi.  
  
## Sintassi  
  
```  
  
dateObj.getTime()   
```  
  
#### Parametri  
 Il riferimento di `dateObj` obbligatorio è un oggetto `Date`.  
  
## Valore restituito  
 Restituisce il numero di millisecondi trascorsi tra la mezzanotte del 1° gennaio 1970 e il valore di ora nell'oggetto `Date`.  L'intervallo di date è approssimativamente di 285.616 anni a partire da mezzanotte dell'1 gennaio 1970.  I numeri negativi indicano date antecedenti al 1970.  
  
## Note  
 Per eseguire calcoli con più date e orari, potresti trovare utile definire le variabili uguali al numero di millisecondi presenti in un giorno, in un'ora o in un minuto.  Di seguito è riportato un esempio:  
  
```javascript  
var minute = 1000 * 60;  
var hour = minute * 60;  
var day = hour * 24;  
```  
  
 Per ulteriori informazioni su come utilizzare il metodo `getTime`, vedi [Calcolo di date e ore \(JavaScript\)](../../javascript/calculating-dates-and-times-javascript.md).  
  
## Esempio  
 Nell'esempio seguente viene illustrato come utilizzare il metodo `getTime`.  
  
```javascript  
var minute = 1000 * 60;  
var hour = minute * 60;  
var day = hour * 24;  
  
date = new Date("1/1/2001");  
var time = date.getTime();  
  
document.write(Math.round(time / day) + " days from 1/1/1970 to 1/1/2001");  
  
// Output: 11323 days from 1/1/1970 to 1/1/2001  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Si applica a**: [Oggetto Date](../../javascript/reference/date-object-javascript.md)  
  
## Vedere anche  
 [Metodo setTime \(Date\)](../../javascript/reference/settime-method-date-javascript.md)