---
title: "Metodo getVarDate (Date) (JavaScript) | Microsoft Docs"
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
  - "getVarDate"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Date (oggetto)"
  - "getVarDate (metodo)"
  - "date, formato VT_DATE"
ms.assetid: 561238de-5c91-45a3-b839-a16910d3a1cf
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# Metodo getVarDate (Date) (JavaScript)
Restituisce un valore VT\_DATE da un oggetto `Date`.  
  
> [!WARNING]
>  Questo metodo è supportato solo in Internet Explorer.  
  
## Sintassi  
  
```  
  
dateObj.getVarDate()   
```  
  
#### Parametri  
 Il riferimento `dateObj` obbligatorio è un oggetto `Date`.  
  
## Valore restituito  
 Restituisce un valore VT\_DATE.  
  
## Note  
 Il metodo `getVarDate` viene usato quando il codice JavaScript interagisce con oggetti COM, oggetti ActiveX o altri oggetti che accettano e restituiscono i valori di data in formato VT\_DATE. Tra questi, gli oggetti in Visual Basic e Visual Basic, Scripting Edition \(VBScript\). Il formato effettivo del valore restituito dipende dalle impostazioni internazionali.  
  
## Requisiti  
 Supportato nelle modalità documento seguenti: Quirks, standard di Internet Explorer 6, standard di Internet Explorer 7, standard di Internet Explorer 8, standard di Internet Explorer 9 e standard di Internet Explorer 10. Non supportato in applicazioni [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]. Vedere [Informazioni sulla versione](../../javascript/reference/javascript-version-information.md).  
  
 **Si applica a**: [Oggetto Date](../../javascript/reference/date-object-javascript.md)  
  
## Vedere anche  
 [Metodo getDate \(Date\)](../../javascript/reference/getdate-method-date-javascript.md)   
 [Funzione Date.parse](../../javascript/reference/date-parse-function-javascript.md)