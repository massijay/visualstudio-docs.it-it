---
title: "Propriet&#224; stackTraceLimit (Error) (JavaScript) | Microsoft Docs"
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
  - "Error.stackTraceLimit"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "limite di rilevamento stack errori [JavaScript]"
  - "stack errori (JavaScript)"
  - "stack errori [JavaScript]"
  - "limite di traccia dello stack (JavaScript)"
ms.assetid: 127ef8e8-892e-4263-9ebc-03364af01212
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Propriet&#224; stackTraceLimit (Error) (JavaScript)
Ottiene o imposta il limite dell'analisi dello stack, che equivale al numero di frame di errore che vengono visualizzati.  Il limite predefinito è 10.  
  
## Sintassi  
  
```  
  
Error  
.stackTraceLimit   
```  
  
## Note  
 È possibile impostare la proprietà `stackTraceLimit` a qualsiasi valore positivo compreso tra 0 e `Infinity`.  Se la proprietà `stackTraceLimit` viene impostata a 0 nel momento in cui viene generato un errore, l'analisi dello stack non viene visualizzata.  Se la proprietà è impostata su un valore negativo o un valore non numerico, il valore viene convertito in 0.  Se stackTraceLimit è impostato a `Infinity`, l'intero stack viene visualizzato.  In caso contrario, si utilizza `ToUint32` per convertire il valore.  
  
## Esempio  
 Il seguente esempio mostra come impostare ed ottenere il limite dell'analisi dello stack.  
  
```javascript  
try  
    {  
    var err = new Error("my error");  
    Error.stackTraceLimit = 7;  
    throw err;  
    }  
catch(e)  
    {  
    document.write ("Error stack trace limit: ")  
    document.write (Error.stackTraceLimit);  
    }  
```  
  
## Requisiti  
 Supportato in Internet Explorer 10 e nelle applicazioni [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)].  
  
 **Si applica a**: [Oggetto Error](../../javascript/reference/error-object-javascript.md)  
  
## Vedere anche  
 [Proprietà description \(Error\)](../../javascript/reference/description-property-error-javascript.md)   
 [Proprietà message \(Error\)](../../javascript/reference/message-property-error-javascript.md)   
 [Proprietà name \(Error\)](../../javascript/reference/name-property-error-javascript.md)   
 [Proprietà stack \(Error\)](../../javascript/reference/stack-property-error-javascript.md)