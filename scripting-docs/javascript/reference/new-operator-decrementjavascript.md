---
title: "Operatore new (JavaScript) | Microsoft Docs"
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
  - "new_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Operatore new in JavaScript"
ms.assetid: 5ea556ba-7ae6-426c-8430-9032eee5a0a5
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Operatore new (JavaScript)
Consente di creare un nuovo oggetto.  
  
## Sintassi  
  
```  
new constructor ([arguments])   
```  
  
## Parametri  
 `constructor`  
 Obbligatorio.  Costruttore dell'oggetto.  Se il costruttore non richiede alcun argomento, è possibile omettere le parentesi.  
  
 `arguments`  
 Facoltativo.  Qualsiasi argomento da passare al costruttore del nuovo oggetto.  
  
## Note  
 Mediante l'operatore `new` vengono effettuate le seguenti attività:  
  
-   Viene creato un oggetto privo di membri.  
  
-   Viene chiamato il costruttore dell'oggetto, passando un puntatore all'oggetto appena creato come puntatore `this`.  
  
-   Il costruttore inizializza quindi l'oggetto in base agli argomenti passati.  
  
 Di seguito sono riportati alcuni esempi di utilizzi validi dell'operatore **new**.  
  
```javascript  
my_object = new Object;  
my_array = new Array();  
my_date = new Date("Jan 5 1996");  
```  
  
## Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Vedere anche  
 [Istruzione function](../../javascript/reference/function-statement-javascript.md)