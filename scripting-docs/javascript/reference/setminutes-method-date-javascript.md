---
title: "Metodo setMinutes (Date) (JavaScript) | Microsoft Docs"
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
  - "setMinutes"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "minuti"
  - "setMinutes (metodo)"
ms.assetid: 34c959cd-cd29-4cee-8e04-9061cf6d42f3
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Metodo setMinutes (Date) (JavaScript)
Consente di impostare il valore dei minuti nell'oggetto **Date** utilizzando l'ora locale.  
  
## Sintassi  
  
```  
  
dateObj.setMinutes(numMinutes[, numSeconds[, numMilli]])   
```  
  
## Parametri  
 `dateObj`  
 Obbligatorio.  Qualsiasi oggetto `Date`.  
  
 `numMinutes`  
 Obbligatorio.  Valore numerico corrispondente ai minuti.  Obbligatorio se si utilizza uno degli argomenti seguenti.  
  
 *numSeconds*  
 Facoltativo.  Valore numerico corrispondente ai secondi.  Obbligatorio se viene utilizzato l'argomento `numMilli`.  
  
 `numMilli`  
 Facoltativo.  Valore numerico corrispondente ai millisecondi.  
  
## Note  
 Per tutti i metodi **set** che prevedono argomenti facoltativi, se un argomento facoltativo non viene specificato, viene utilizzato il valore restituito dai corrispondenti metodi **get**.  Se, ad esempio, l'argomento *numSeconds* non viene specificato, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] utilizza il valore restituito dal metodo `getSeconds`.  
  
 Per impostare il valore dei minuti utilizzando il formato UTC \(Universal Coordinated Time, Tempo universale coordinato\), è possibile impiegare il metodo `setUTCMinutes`.  
  
 Se il valore di un argomento è maggiore del relativo intervallo o è un numero negativo, gli altri valori memorizzati verranno modificati di conseguenza.  Se, ad esempio, la data memorizzata è "5 gen 1996 00.00.00" e si chiama il metodo **setMinutes\(90\)**, la data viene modificata in "5 gen 1996 01.30.00". I numeri negativi vengono modificati nello stesso modo.  
  
## Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo del metodo `setMinutes`.  
  
```javascript  
function SetMinutesDemo(nmin, nsec){  
   var d, s;                     // Declare variables.  
   d = new Date();               // Create Date object.  
   d.setMinutes(nmin, nsec);     // Set minutes.  
   s = "Current setting is " + d.toLocaleString()   
   return(s);                    // Return new setting.  
}  
```  
  
## Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Si applica a**: [Oggetto Date](../../javascript/reference/date-object-javascript.md)  
  
## Vedere anche  
 [Metodo getMinutes \(Date\)](../../javascript/reference/getminutes-method-date-javascript.md)   
 [Metodo getUTCMinutes \(Date\)](../../javascript/reference/getutcminutes-method-date-javascript.md)   
 [Metodo setUTCMinutes \(Date\)](../../javascript/reference/setutcminutes-method-date-javascript.md)