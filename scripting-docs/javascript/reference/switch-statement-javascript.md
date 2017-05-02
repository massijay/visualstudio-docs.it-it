---
title: "Istruzione switch (JavaScript) | Microsoft Docs"
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
  - "switch_JavaScriptKeyword"
  - "default_JavaScriptKeyword"
  - "case_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "switch (istruzione)"
ms.assetid: 61f80e8b-3739-4146-a893-c2832d92b28c
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# Istruzione switch (JavaScript)
Attiva l'esecuzione di una o più istruzioni quando il valore dell'espressione specificata corrisponde a un'etichetta.  
  
## Sintassi  
  
```  
switch (expression) {  
    case label :  
        statementlist  
    case label :  
    default :  
        statementlist  
}   
```  
  
## Parametri  
 `expression`  
 Espressione da valutare.  
  
 `label`  
 Identificatore a cui `expression` deve corrispondere.  Se `label` corrisponde a `expression`, l'esecuzione inizia con `statementlist` immediatamente dopo i due punti e continua fino a quando non viene individuata un'istruzione `break`, facoltativa, oppure fino alla fine dell'istruzione `switch`.  
  
 `statementlist`  
 Una o più istruzioni da eseguire.  
  
## Note  
 Utilizzare la clausola `default` per specificare un'istruzione da eseguire se nessuno dei valori delle etichette corrisponde a `expression`.  Tale clausola può essere specificata in qualsiasi punto del blocco di codice dell'istruzione `switch`.  
  
 È possibile specificare zero o più blocchi `label`.  Se nessun valore di `label` corrisponde al valore di `expression` e non viene specificato un caso `default`, non verrà eseguita alcuna istruzione.  
  
 Il flusso di esecuzione di un'istruzione `switch` è il seguente:  
  
-   Si valuta `expression` confrontando il risultato con il valore di `label` fino a quando non viene individuata una corrispondenza.  
  
-   Se il valore di `label` equivale a `expression`, viene eseguito il corrispondente `statementlist`.  
  
     L'esecuzione continua fino a quando non viene individuata un'istruzione `break` oppure fino alla fine dell'istruzione `switch`.  Ciò significa che se non si utilizza alcuna istruzione `break`, vengono eseguiti più blocchi `label`.  
  
-   Se nessun valore di `label` equivale a `expression`, si passa al caso `default`.  Se non è presente alcun caso `default`, il flusso di programma si posiziona dopo l'ultima istruzione.  
  
-   L'esecuzione continua con l'istruzione che segue la fine del blocco di codice `switch`.  
  
## Esempio  
 Nell'esempio seguente viene verificato il tipo di un oggetto.  
  
```javascript  
function MyObjectType(obj) {  
    switch (obj.constructor) {  
        case Date:  
            document.write("Object is a Date.");  
            break;  
        case Number:  
            document.write("Object is a Number.");  
            break;  
        case String:  
            document.write("Object is a String.");  
            break;  
        default:  
            document.write("Object is unknown.");  
    }  
}  
  
// Output when obj is a Date:  
// Object is a Date.  
  
// Output when obj is a Number:  
// Object is a Number.  
  
// Output when obj is a String:  
// Object is a String.  
  
// Output when obj is something other than a Date, Number, or String:  
// Object is unknown.  
  
```  
  
## Esempio  
 Nel codice seguente viene mostrato cosa avviene se non si utilizza un'istruzione `break`.  
  
```javascript  
function MyObjectType(obj) {  
    switch (obj.constructor) {  
        case Date:  
            document.write("Object is a Date.");  
        case Number:  
            document.write("Object is a Number.");  
        case String:  
            document.write("Object is a String.");  
        default:  
            document.write("Object is unknown.");  
    }  
}  
  
// Output when obj is a Date:  
// Object is a Date.Object is a Number.Object is a String.Object is unknown.  
  
// Output when obj is a Number:  
// Object is a Number.Object is a String.Object is unknown.  
  
// Output when obj is a String:  
// Object is a String.Object is unknown.  
  
// Output when obj is something other than a Date, Number, or String:  
// Object is unknown.  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## Vedere anche  
 [Istruzione break](../../javascript/reference/break-statement-javascript.md)   
 [Istruzione if...else](../../javascript/reference/if-dot-dot-dot-else-statement-javascript.md)