---
title: "Variabili (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "distinzione tra maiuscole e minuscole, nome di variabili JavaScript"
  - "coercizione"
ms.assetid: 12a450e5-4818-4a09-9878-cd7c6cd2a248
caps.latest.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 20
---
# Variabili (JavaScript)
In [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] una variabile contiene un valore, ad esempio "hello" o 5.  Quando si utilizza la variabile, si fa riferimento ai dati che rappresenta, ad esempio `NumberOfDaysLeft = EndDate – TodaysDate`.  
  
 Le variabili vengono utilizzate per archiviare, recuperare e modificare i valori inseriti nel codice.  Per semplificare la comprensione del codice, provare ad assegnare alle variabili nomi significativi.  
  
## Dichiarazione di variabili  
 Una dichiarazione rappresenta la prima visualizzazione della variabile nello script.  La prima volta in cui viene citata, la variabile viene impostata in memoria, in modo da farvi riferimento in un secondo momento nello script.  È necessario dichiarare le variabili prima di utilizzarle.  A tale scopo, utilizzare la parola chiave `var`.  
  
```javascript  
// A single declaration.  
var count;    
// Multiple declarations with a single var keyword.  
var count, amount, level;      
// Variable declaration and initialization in one statement.  
var count = 0, amount = 100;   
```  
  
 Se non viene inizializzata, la variabile nell'istruzione `var` assume automaticamente il valore `undefined`.  
  
## Denominazione di variabili  
 Nel linguaggio [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] viene fatta distinzione tra maiuscole e minuscole,  ovvero un nome di variabile come myCounter è diverso dal nome di variabile MYCounter.  La lunghezza dei nomi di variabile non è soggetta a limitazioni.  Le regole per la creazione di nomi di variabile validi sono le seguenti:  
  
-   Il primo carattere deve essere una lettera ASCII maiuscola o minuscola o un carattere di sottolineatura \(\_\).  Non è possibile utilizzare un numero come primo carattere.  
  
-   I caratteri successivi devono essere lettere, numeri o caratteri di sottolineatura \(\_\).  
  
-   Il nome di una variabile non deve essere una [parola riservata](../javascript/reference/javascript-reserved-words.md).  
  
 Di seguito sono riportati alcuni esempi di nomi di variabile validi:  
  
```  
_pagecount   
Part9   
Number_Items   
```  
  
 Di seguito sono riportati alcuni esempi di nomi di variabile non validi:  
  
```javascript  
// Cannot begin with a number.   
99Balloons     
// The ampersand (&) character is not a valid character for variable names.   
Alpha&Beta   
```  
  
 Per dichiarare e inizializzare una variabile senza fornire un valore specifico, assegnarle il valore `null`.  Di seguito è riportato un esempio.  
  
```javascript  
var bestAge = null;  
var muchTooOld = 3 * bestAge; // muchTooOld has the value 0.  
```  
  
 Se si dichiara una variabile senza assegnarle un valore, la variabile presenterà il valore `undefined`.  Di seguito è riportato un esempio.  
  
```javascript  
var currentCount;  
// finalCount has the value NaN because currentCount is undefined.  
var finalCount = 1 * currentCount;   
```  
  
 Il valore `null` equivale al numero 0, mentre `undefined` equivale al valore speciale `NaN` \(non numerico\).  Se confrontati, un valore `null` e un valore `undefined` sono uguali.  
  
 È possibile dichiarare una variabile senza utilizzare la parola chiave `var` nella dichiarazione e assegnarle un valore.  Si tratta di una dichiarazione implicita.  
  
```javascript  
// The variable noStringAtAll is declared implicitly.  
noStringAtAll = "";   
```  
  
 Non si può utilizzare una variabile che non è mai stata dichiarata.  
  
```javascript  
// Error. Length and width do not yet exist.  
var area = length * width;   
```  
  
## Coercizione  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] non è un linguaggio fortemente tipizzato, contrariamente a linguaggi come C\+\+.  Ciò significa che le variabili JavaScript non dispongono di alcun tipo predeterminato.  Al contrario, il tipo di una variabile corrisponde al tipo del relativo valore.  Questo comportamento consente di considerare un valore come se fosse un valore di tipo diverso.  
  
 In [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] è possibile eseguire operazioni su valori di tipi diversi senza generare eccezioni.  L'interprete [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] esegue la conversione in modo implicito, o l'*assegnazione forzata*, del tipo di dati di un valore in un altro ed esegue l'operazione.  Le regole per la coercizione di valori stringa, numerici e booleani sono le seguenti:  
  
-   Se si aggiunge un numero e una stringa, il numero viene assegnato a una stringa.  
  
-   Se si aggiunge un valore booleano e una stringa, il valore booleano viene assegnato a una stringa.  
  
-   Se si aggiunge un numero e un valore booleano, il valore booleano viene assegnato a un numero.  
  
 Nell'esempio seguente un numero aggiunto a una stringa genera una stringa.  
  
```javascript  
var x = 2000;  
var y = "Hello";  
// The number is coerced to a string.  
x = x + y;  
document.write(x);   
  
// Output:  
// 2000Hello  
```  
  
 Le stringhe vengono convertite automaticamente in numeri equivalenti a scopo di confronto.  Per convertire esplicitamente una stringa in un Integer, utilizzare la [funzione parseInt](../javascript/reference/parseint-function-javascript.md).  Per convertire esplicitamente una stringa in un numero, utilizzare la [funzione parseFloat](../javascript/reference/parsefloat-function-javascript.md).