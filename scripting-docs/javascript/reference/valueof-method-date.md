---
title: "Metodo valueOf (Date) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 39a1f96e-14b0-4db2-b53d-cdfd67cbb208
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Metodo valueOf (Date)
Restituisce il valore memorizzato dell'ora espresso in millisecondi a partire dalla mezzanotte dell'1 gennaio 1970 in formato UTC.  
  
## Sintassi  
  
```  
  
date.valueOf()  
```  
  
#### Parametri  
 L'oggetto `date` rappresenta qualsiasi istanza di una data.  
  
## Valore restituito  
 Il valore memorizzato dell'ora espresso in millisecondi a partire dalla mezzanotte dell'1 gennaio 1970 in formato UTC.  Il valore è uguale a `getTime`.  
  
## Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo del metodo `valueOf` con una data.  
  
```javascript  
var myDate = new Date();  
myDate.setFullYear(2100, 5, 5);  
if (myDate.getTime() == myDate.valueOf())  
    document.write("values are the same");  
else  
    document.write("values are different");  
  
// Output: values are the same  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]