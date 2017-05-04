---
title: "Metodo setUTCMilliseconds (Date) (JavaScript) | Microsoft Docs"
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
  - "setUTCMilliseconds"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "date, UTC"
  - "millisecondi"
  - "setUTCMilliseconds (metodo)"
  - "UTC (ora), impostazione"
ms.assetid: ed8e4486-d4b2-4b73-836b-dd1d3bb991a0
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Metodo setUTCMilliseconds (Date) (JavaScript)
Imposta il valore dei millisecondi nell'oggetto `Date` utilizzando il formato UTC \(Universal Coordinated Time\).  
  
## Sintassi  
  
```  
  
dateObj.setUTCMilliseconds(numMilli)   
```  
  
## Parametri  
 `dateObj`  
 Obbligatorio.  Qualsiasi oggetto `Date`.  
  
 `numMilli`  
 Obbligatorio.  Valore numerico che rappresenta i millisecondi.  
  
## Note  
 Per impostare il valore dei millisecondi in base all'ora locale, utilizzare il metodo `setMilliseconds`.  
  
 Se il valore di `numMilli` è maggiore di 999 o è un numero negativo, il valore memorizzato dei secondi \(e dei minuti, delle ore e così via se necessario\) viene incrementato in modo appropriato.  
  
## Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo del metodo `setUTCMilliseconds`.  
  
```javascript  
function SetUTCMSecDemo(nmsec){     
// Create Date object.  
   var d = new Date();             
// Set UTC milliseconds.  
   d.setUTCMilliseconds(nmsec);    
  
   var s = "Current setting is ";  
   s += d.toUTCString();  
   s += " and " + d.getUTCMilliseconds();  
   s += " milliseconds"  
   return(s);  
}  
```  
  
## Requisiti  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Si applica a**: [Oggetto Date](../../javascript/reference/date-object-javascript.md)  
  
## Vedere anche  
 [Metodo getMilliseconds \(Date\)](../../javascript/reference/getmilliseconds-method-date-javascript.md)   
 [Metodo getUTCMilliseconds \(Date\)](../../javascript/reference/getutcmilliseconds-method-date-javascript.md)   
 [Metodo setMilliseconds \(Date\)](../../javascript/reference/setmilliseconds-method-date-javascript.md)