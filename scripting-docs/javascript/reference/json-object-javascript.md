---
title: "Oggetto JSON (JavaScript) | Microsoft Docs"
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
  - "JSON"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "oggetto JSON"
ms.assetid: 0279a0e0-70bf-451a-a78e-0da4e2fdeb9a
caps.latest.revision: 43
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 43
---
# Oggetto JSON (JavaScript)
Oggetto intrinseco che contiene funzioni per convertire valori di [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] in e dal formato JSON \(JavaScript Object Notation\).  La funzione `JSON.stringify` serializza un valore di [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] in testo JSON.  La funzione `JSON.parse` deserializza il testo JSON per produrre un valore di [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## Sintassi  
  
```  
  
JSON.[method]  
  
```  
  
## Parametri  
 `Method`  
 Obbligatorio.  Nome di uno dei metodi dell'oggetto `JSON`.  
  
## Note  
 Non è possibile creare un oggetto `JSON` utilizzando l'operatore `new`.  Se si tenta di eseguire questa operazione, si verifica un errore.  Tuttavia, si può ignorare o modificare l'oggetto `JSON`.  
  
 Quando viene caricato, il motore di script crea l'oggetto `JSON`.  I metodi relativi sono sempre disponibili per lo script.  
  
 Per usare l'oggetto `JSON` intrinseco, assicurarsi che non venga sostituito con un altro oggetto `JSON` definito nello script.  Potrebbe essere necessario modificare le istruzioni di script esistenti che rilevano la presenza di un oggetto `JSON` perché tali istruzioni verranno valutate in modo diverso,  come illustrato nell'esempio seguente.  
  
```javascript  
if (!this.JSON) {  
    // JSON object does not exist.  
    }  
```  
  
 Nell'esempio precedente `!this.JSON` restituisce false in [!INCLUDE[jsv58text](../../javascript/reference/includes/jsv58text-md.md)].  Di conseguenza, il codice nell'istruzione `if` non viene eseguito.  
  
## Funzioni  
 [Funzione JSON.parse](../../javascript/reference/json-parse-function-javascript.md)  
  
 [Funzione JSON.stringify](../../javascript/reference/json-stringify-function-javascript.md)  
  
## Requisiti  
 [!INCLUDE[jsv58](../../javascript/reference/includes/jsv58-md.md)]  
  
## Vedere anche  
 [Metodo toJSON \(Date\)](../../javascript/reference/tojson-method-date-javascript.md)   
 [Oggetti JavaScript](../../javascript/reference/javascript-objects.md)   
 [Esempio di app di modello hub \(Windows Store\)](http://code.msdn.microsoft.com/Hub-template-sample-with-4b70002d)