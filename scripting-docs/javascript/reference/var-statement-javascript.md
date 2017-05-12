---
title: "Istruzione var (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/22/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "var_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "dichiarazione di variabili, istruzione var"
  - "var (istruzione)"
ms.assetid: 56f900af-a5c4-4667-9664-5956d30f0aae
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# Istruzione var (JavaScript)
Dichiara una variabile.  
  
## Sintassi  
  
```  
var variable1 = value1  
```  
  
## Parametri  
 `variable1`  
 Il nome della variabile che si sta dichiarando.  
  
 `value1`  
 Valore iniziale assegnato alla variabile.  
  
## Note  
 Utilizzare l'istruzione `var` per la dichiarazione di variabili.  È possibile assegnare valori alle variabili quando vengono dichiarate o più avanti nello script.  
  
 Una variabile viene dichiarata la prima volta che appare nello script.  
  
 È possibile dichiarare una variabile senza utilizzare la parola chiave `var` e assegnare ad essa un valore.  Questa tecnica, nota come *dichiarazione implicita*, non è consigliata.  Una dichiarazione implicita fornisce alla variabile un ambito globale.  Quando tuttavia si dichiara una variabile a livello di procedura, in genere non si desidera che questa abbia un ambito globale.  Per evitare di dare l'ambito globale alla variabile, è necessario utilizzare la parola chiave `var` nella dichiarazione della variabile.  
  
 Se non si inizializza la variabile in un'istruzione `var`, viene automaticamente assegnato il valore `undefined` di [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## Esempio  
 Negli esempi seguenti viene illustrato l'utilizzo dell'istruzione `var`.  
  
```javascript  
var index;  
var name = "Thomas Jefferson";  
var answer = 42, counter, numpages = 10;  
var myarray = new Array();  
```  
  
## Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Vedere anche  
 [Istruzione function](../../javascript/reference/function-statement-javascript.md)   
 [Operatore new](../../javascript/reference/new-operator-decrementjavascript.md)   
 [Oggetto Array](../../javascript/reference/array-object-javascript.md)   
 [Variabili](../../javascript/variables-javascript.md)