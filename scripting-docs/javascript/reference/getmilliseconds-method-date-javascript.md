---
title: "Metodo getMilliseconds (Date) (JavaScript) | Microsoft Docs"
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
  - "getMilliseconds"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "millisecondi"
  - "getMilliseconds (metodo)"
ms.assetid: 1b512146-1e8a-44a4-89da-6cc5338d15cb
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Metodo getMilliseconds (Date) (JavaScript)
Ottiene i millisecondi di un oggetto Date che utilizza l'ora locale.  
  
## Sintassi  
  
```  
  
dateObj.getMilliseconds()   
```  
  
#### Parametri  
 Il riferimento di `dateObj` obbligatorio è un oggetto `Date`.  
  
## Valore restituito  
 Restituisce i millisecondi di una data.  Il valore è compreso tra 0 e 999.  Se una data è stata creata senza specificare i millisecondi, il valore restituito è 0.  
  
## Note  
 Per ottenere il numero di millisecondi nel formato UTC \(Universal Coordinated Time, Tempo universale coordinato\), è possibile impiegare il metodo `getUTCMilliseconds`.  
  
## Esempio  
 Nell'esempio seguente viene illustrato come utilizzare il metodo **getMilliseconds**.  
  
```javascript  
var date = new Date("1/1/2001");  
document.write(date.getMilliseconds());  
document.write("<br/>");  
  
date.setMilliseconds(5);  
document.write(date.getMilliseconds());  
// Output:   
// 0  
// 5  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Si applica a**: [Oggetto Date](../../javascript/reference/date-object-javascript.md)  
  
## Vedere anche  
 [Metodo getUTCMilliseconds \(Date\)](../../javascript/reference/getutcmilliseconds-method-date-javascript.md)   
 [Metodo setMilliseconds \(Date\)](../../javascript/reference/setmilliseconds-method-date-javascript.md)   
 [Metodo setUTCMilliseconds \(Date\)](../../javascript/reference/setutcmilliseconds-method-date-javascript.md)