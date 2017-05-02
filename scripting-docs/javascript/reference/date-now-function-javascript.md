---
title: "Funzione Date.now (JavaScript) | Microsoft Docs"
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
helpviewer_keywords: 
  - "now (metodo)"
ms.assetid: 41beda89-1a40-4fb1-88b0-38c090af739b
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# Funzione Date.now (JavaScript)
Ottiene la data e l'ora corrente.  
  
## Sintassi  
  
```  
  
Date.now()  
```  
  
## Valore restituito  
 Il numero di millisecondi tra la mezzanotte dell'1 gennaio 1970 e la data e l'ora corrente.  
  
## Note  
 Il [metodo getTime](../../javascript/reference/gettime-method-date-javascript.md) restituisce il numero di millisecondi tra l'1 gennaio 1970 e una data specificata.  
  
 Per informazioni su come calcolare il tempo trascorso e sul confronto tra date, vedere la pagina [Calcolo di date e ore \(JavaScript\)](../../javascript/calculating-dates-and-times-javascript.md).  
  
## Esempio  
 Nell'esempio riportato di seguito viene illustrato l'utilizzo del metodo `now`.  
  
```javascript  
var start = Date.now();  
var response = prompt("What is your name?", "");  
var end = Date.now();  
var elapsed = (end - start) / 1000;  
document.write("You took " + elapsed + " seconds" + " to type: " + response);  
  
// Output:  
// You took <seconds> seconds to type: <name>  
```  
  
## Requisiti  
 Non supportato in versioni installate precedentemente a Internet Explorer 9.  Tuttavia è supportato nelle modalità documento seguenti: Quirks, standard di Internet Explorer 6, standard di Internet Explorer 7, standard di Internet Explorer 8, standard di Internet Explorer 9, standard di Internet Explorer 10.  Supportato inoltre nelle applicazioni [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)].  
  
## Vedere anche  
 [Metodo getTime \(Date\)](../../javascript/reference/gettime-method-date-javascript.md)   
 [Oggetto Date](../../javascript/reference/date-object-javascript.md)   
 [Calcolo di date e ore \(JavaScript\)](../../javascript/calculating-dates-and-times-javascript.md)   
 [Metodi JavaScript](../../javascript/reference/javascript-methods.md)