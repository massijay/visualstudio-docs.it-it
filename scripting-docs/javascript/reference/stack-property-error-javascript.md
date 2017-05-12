---
title: "Propriet&#224; stack (Error) (JavaScript) | Microsoft Docs"
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
  - "Error.stack"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "stack errori [JavaScript]"
  - "stack errori (JavaScript)"
ms.assetid: 1dc21fdd-853c-4664-bf1c-24eb1f6f2daf
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Propriet&#224; stack (Error) (JavaScript)
Ottiene o imposta lo stack degli errori come una stringa contenente i frame di traccia dello stack.  
  
## Sintassi  
  
```  
  
object  
.stack   
```  
  
## Note  
 La proprietà `stack` è impostata su `undefined` quando l’errore viene costruito e ottiene le informazioni di traccia quando l'errore viene generato.  Se un errore viene generato più volte, la proprietà `stack` viene aggiornata ogni volta che viene generato l'errore.  
  
 Gli stack frame vengono visualizzati nel formato seguente: in FunctionName \(\<nome\/URL completo\>: \<numero di riga\>: \<numero di colonna\>\)  
  
 Se si crea un oggetto Error personalizzato e si imposta la traccia dello stack su un valore, il valore non verrà sovrascritto quando viene generato l'errore.  
  
 La proprietà `stack` non visualizza funzioni inline nei relativi frame.  Visualizza solo lo stack fisico.  
  
## Esempio  
 Nell'esempio seguente viene illustrato come ottenere lo stack quando viene intercettato un errore.  
  
```javascript  
try  
    {  
        var x = y.name;  
    }  
catch(e)  
    {  
        document.write ("Error stack: ")  
        document.write (e.stack);  
    }  
```  
  
## Esempio  
 Nell'esempio seguente viene illustrato come impostare e ottenere lo stack.  
  
```javascript  
try  
    {  
        var err = Error("my error");  
        err.stack = "my stack trace";  
        throw err;  
    }  
catch(e)  
    {  
        document.write ("Error stack: ")  
        document.write (e.stack);  
    }  
```  
  
## Requisiti  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]  
  
 **Si applica a**: [Oggetto Error](../../javascript/reference/error-object-javascript.md)  
  
## Vedere anche  
 [Proprietà description \(Error\)](../../javascript/reference/description-property-error-javascript.md)   
 [Proprietà message \(Error\)](../../javascript/reference/message-property-error-javascript.md)   
 [Proprietà name \(Error\)](../../javascript/reference/name-property-error-javascript.md)   
 [Proprietà stackTraceLimit \(Error\)](../../javascript/reference/stacktracelimit-property-error-javascript.md)