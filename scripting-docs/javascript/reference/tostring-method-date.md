---
title: "Metodo toString (Date) | Microsoft Docs"
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
ms.assetid: d3037289-d805-409b-8781-045c59a2c404
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Metodo toString (Date)
Restituisce la rappresentazione in forma di stringa di una data.  Il formato della stringa dipende dalle impostazioni locali.  Per l'inglese U.S. \(en\-us\), è il seguente:  
  
 *giorno della settimana* *mese* *giorno* *ora*: *minuto*:*secondo* *fuso orario* *anno*  
  
## Sintassi  
  
```  
  
date.toString()  
```  
  
## Parametri  
 `date`  
 Necessario.  La data da rappresentare come stringa.  
  
## Valore restituito  
 Restituisce la rappresentazione in forma di stringa della data.  
  
## Esempio  
 Nell'esempio riportato di seguito viene illustrato l'utilizzo del metodo `toString` con una data.  
  
```javascript  
var myDate = new Date();  
myDate.setFullYear(2100, 5, 5);  
var dateString = myDate.toString();  
document.write(dateString);  
  
// Output: <date>  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]