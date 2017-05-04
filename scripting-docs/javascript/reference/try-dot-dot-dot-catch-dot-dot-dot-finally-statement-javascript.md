---
title: "Istruzione try...catch...finally (JavaScript) | Microsoft Docs"
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
  - "try_JavaScriptKeyword"
  - "finally_JavaScriptKeyword"
  - "catch_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "gestione eccezioni try-catch"
  - "gestione eccezioni try-catch, about try-catch (gestione eccezioni)"
  - "gestione eccezioni try-catch, blocco catch"
  - "gestione eccezioni try-catch, blocco finally"
ms.assetid: b7a0a54e-dfaa-4e41-bf25-bcaa43e601fb
caps.latest.revision: 28
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 28
---
# Istruzione try...catch...finally (JavaScript)
Imposta blocchi di codice in cui gli errori generati in un blocco vengono gestiti in un altro.  Gli errori generati all'interno del blocco `try` vengono individuati nel blocco `catch`.  [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## Sintassi  
  
```  
try {  
    tryStatements  
}  
catch(exception){  
    catchStatements  
}  
finally {  
    finallyStatements  
}  
```  
  
## Parametri  
 `tryStatements`  
 Obbligatorio.  Istruzioni in cui può verificarsi un errore.  
  
 `exception`  
 Obbligatorio.  Qualsiasi nome di variabile.  Il valore iniziale di `exception` corrisponde al valore dell'errore generato.  
  
 `catchStatements`  
 Facoltativo.  Istruzioni che gestiscono gli errori generati nel blocco `tryStatements`.  
  
 `finallyStatements`  
 Facoltativo.  Istruzioni che vengono eseguite in modo non condizionale al termine dell'elaborazione di tutti gli altri errori.  
  
## Note  
 L'istruzione `try...catch...finally` consente di gestire parte o tutti gli errori che potrebbero verificarsi in un blocco di codice specifico, senza interrompere l'esecuzione del programma.  Se si verificano errori non gestiti, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] fornisce il messaggio normale di errore.  
  
 Il blocco `try` contiene il codice che può provocare un errore, mentre il blocco `catch` contiene il codice che gestisce alcuni o tutti gli errori.  Se si verifica un errore nel blocco `try`, il controllo del programma viene passato al blocco `catch`.  Il valore di `exception` è il valore dell'errore verificatosi nel blocco `try`.  Se non si verifica un errore, il codice all'interno del blocco `catch` non verrà mai eseguito.  
  
 È possibile passare l'errore al livello successivo utilizzando l'istruzione `throw` per rigenerare l'errore.  
  
 Dopo che le istruzioni nel blocco `try` sono state eseguite e la gestione degli errori è stata effettuata nel blocco `catch`, le istruzioni nel blocco `finally` vengono eseguite, indipendentemente dal fatto che un errore sia stato gestito.  Il codice nel blocco `finally` è sicuramente eseguito a meno che non si verifichi un errore non gestito \(ad esempio un errore di runtime all'interno del blocco **catch**\).  
  
## Esempio  
 Nell'esempio seguente viene generata un'eccezione `ReferenceError` e quindi viene visualizzato il nome dell'errore e il relativo messaggio.  
  
```javascript  
try {  
    addalert("bad call");  
}  
catch(e) {  
    document.write ("Error Message: " + e.message);  
    document.write ("<br />");  
    document.write ("Error Code: ");  
    document.write (e.number & 0xFFFF);  
    document.write ("<br />");  
    document.write ("Error Name: " + e.name);  
}  
  
// Output:  
Error Message: 'addalert' is undefined  
Error Code: 5009  
Error Name: ReferenceError  
  
```  
  
## Esempio  
 Nell'esempio seguente viene illustrato come rigenerare un errore e come vengono eseguiti i blocchi `try…catch` annidati.  Quando viene generato l'errore dal blocco `try` annidato, questo viene passato al blocco `catch` annidato, che lo genera nuovamente.  Il blocco `finally` annidato viene eseguito prima del blocco `catch` esterno che gestisce l'errore e alla fine viene eseguito il blocco `finally` esterno.  
  
```javascript  
try {  
    document.write("Outer try running...<br/>");  
  
    try {  
        document.write("Nested try running...<br/>");  
        throw new Error(301, "an error");  
    }  
    catch (e) {  
        document.write ("Nested catch caught " + e.message + "<br/>");  
        throw e;  
    }  
    finally {  
        document.write ("Nested finally is running...<br/>");  
    }  
}  
catch (e) {  
    document.write ("Outer catch caught " + e.message + "<br/>");  
}  
finally {  
    document.write ("Outer finally running");  
}  
  
// Output:  
// Outer try running...  
// Nested try running...  
// Nested catch caught error from nested try  
// Nested finally is running...  
// Outer catch caught error from nested try  
// Outer finally running  
```  
  
## Requisiti  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
> [!NOTE]
>  Eseguendo l'avvio con Internet Explorer 8 in modalità Standard, il blocco **catch** non è più necessario per l'esecuzione di `finally`.  
  
## Vedere anche  
 [Istruzione throw](../../javascript/reference/throw-statement-javascript.md)   
 [App di esempio per una configurazione guidata dello script Junkie](http://code.msdn.microsoft.com/Script-Junkie-Configuration-543ece24)