---
title: "Metodo setDate (Date) (JavaScript) | Microsoft Docs"
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
  - "setDate"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "setDate (metodo)"
  - "date, impostazione"
ms.assetid: a84b9b01-a6d0-489f-8a13-e7af9e9630b2
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# Metodo setDate (Date) (JavaScript)
Imposta il valore numerico di giorno\-de \-\- mese dell'oggetto `Date` utilizzando l'ora locale.  
  
## Sintassi  
  
```  
  
dateObj.setDate(numDate)   
```  
  
## Parametri  
 `dateObj`  
 Obbligatorio.  Qualsiasi oggetto `Date`.  
  
 `numDate`  
 Obbligatorio.  Valore numerico corrispondente al giorno del mese.  
  
## Note  
 Per impostare il valore di giorno\-de \-\- mese utilizzo di tempo universale coordinato \(UTC\), utilizzare il metodo `setUTCDate`.  
  
 Se il valore `numDate` è maggiore del numero di giorni del mese, la data viene chiamata a un mese e\/o all'anno più tardi.  Ad esempio, se la data archiviato è il 5 gennaio 1996 e `setDate(32)` viene chiamato, le modifiche della data a 1° febbraio 1996.  Se `numDate` è un numero negativo, la data alza su un mese e\/o a un anno precedente.  Ad esempio, se la data archiviato è il 5 gennaio 1996 e `setDate(-32)` viene chiamato, le modifiche della data a 29 novembre 1995.  
  
 [Metodo setFullYear \(Date\)](../../javascript/reference/setfullyear-method-date-javascript.md) può essere utilizzato per impostare l'anno, il mese e il giorno.  
  
## Esempio  
 Nell'esempio seguente viene illustrato come utilizzare il metodo `setDate`.  
  
```javascript  
var date = new Date("12/15/1990");  
date.setDate(30);  
document.write(date);  
  
// Output (for the PST time zone): Sun Dec 30 00:00:00 PST 1990  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Applies To**: [Oggetto Date](../../javascript/reference/date-object-javascript.md)  
  
## Vedere anche  
 [Metodo getDate \(Date\)](../../javascript/reference/getdate-method-date-javascript.md)   
 [Metodo setFullYear \(Date\)](../../javascript/reference/setfullyear-method-date-javascript.md)   
 [Metodo setMonth \(Date\)](../../javascript/reference/setmonth-method-date-javascript.md)   
 [Metodo setUTCDate \(Date\)](../../javascript/reference/setutcdate-method-date-javascript.md)