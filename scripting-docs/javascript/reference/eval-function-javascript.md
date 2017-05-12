---
title: "Funzione eval (JavaScript) | Microsoft Docs"
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
  - "eval"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "eval (funzione)"
  - "analisi, codice"
  - "parser"
ms.assetid: 85587e39-9325-4b75-b9f9-9d7d475a2120
caps.latest.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 21
---
# Funzione eval (JavaScript)
Valuta il codice [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] e lo esegue.  
  
## Sintassi  
  
```  
eval(codeString)   
```  
  
## Parametri  
 `codeString`  
 Obbligatorio.  Valore `String` contenente il codice [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] valido.  
  
## Note  
 La funzione `eval` consente l'esecuzione dinamica del codice [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] sorgente.  
  
 La stringa `codeString` viene analizzata dal parser [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] e viene eseguita.  
  
 Il codice passato alla funzione `eval` viene eseguito nello stesso contesto della chiamata alla funzione `eval`.  
  
 Quando possibile, utilizzare la [funzione JSON.parse](../../javascript/reference/json-parse-function-javascript.md) per deserializzare il testo JSON \(JavaScript Object Notation\).  La funzione `JSON.parse` è più sicura e viene eseguita più velocemente della funzione `eval`.  
  
## Esempio  
 Nel codice seguente viene inizializzata la variabile `myDate` in una data di test.  
  
```javascript  
var dateFn = "Date(1971,3,8)";  
var myDate;  
eval("myDate = new " + dateFn + ";");  
  
document.write(myDate);  
  
// Output: Thu Apr 8 00:00:00 PDT 1971  
```  
  
## Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Si applica a**: [Oggetto Global](../../javascript/reference/global-object-javascript.md)  
  
## Vedere anche  
 [Oggetto String](../../javascript/reference/string-object-javascript.md)