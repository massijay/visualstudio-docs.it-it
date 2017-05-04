---
title: "Metodo setMilliseconds (Date) (JavaScript) | Microsoft Docs"
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
  - "setMilliseconds"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "millisecondi"
  - "setMilliseconds (metodo)"
ms.assetid: 6c398961-130e-4f60-802f-6c30e1ef4de4
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Metodo setMilliseconds (Date) (JavaScript)
Consente di impostare il valore dei millisecondi nell'oggetto `Date` utilizzando l'ora locale.  
  
## Sintassi  
  
```  
  
dateObj.  
setMilliseconds(  
numMilli  
)   
```  
  
## Parametri  
 `dateObj`  
 Obbligatorio.  Qualsiasi oggetto `Date`.  
  
 `numMilli`  
 Obbligatorio.  Valore numerico che rappresenta i millisecondi.  
  
## Note  
 Per impostare il valore dei millisecondi in base al formato UTC \(Universal Coordinated Time, Tempo universale coordinato\), utilizzare il metodo `setUTCMilliseconds`.  
  
 Se il valore di `numMilli` è maggiore di 999 o è un numero negativo, il valore memorizzato dei secondi \(e dei minuti, delle ore e così via se necessario\) viene incrementato in modo appropriato.  
  
## Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo del metodo `setMilliseconds`.  
  
```javascript  
function SetMSecDemo(nmsec){  
   var d, s;                    // Declare variables.  
   d = new Date();              // Create Date object.  
   d.setMilliseconds(nmsec);    // Set milliseconds.  
   s = "Current setting is ";  
   s += d.toLocaleString();  
   s += " and " + d.getMilliseconds();  
   s += " milliseconds";  
   return(s);                   // Return new date setting.  
}  
```  
  
## Requisiti  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Si applica a**: [Oggetto Date](../../javascript/reference/date-object-javascript.md)  
  
## Vedere anche  
 [Metodo getMilliseconds \(Date\)](../../javascript/reference/getmilliseconds-method-date-javascript.md)   
 [Metodo getUTCMilliseconds \(Date\)](../../javascript/reference/getutcmilliseconds-method-date-javascript.md)   
 [Metodo setUTCMilliseconds \(Date\)](../../javascript/reference/setutcmilliseconds-method-date-javascript.md)