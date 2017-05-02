---
title: "Metodo replace (String) (JavaScript) | Microsoft Docs"
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
  - "replace"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Replace (metodo)"
  - "sostituzione di stringhe"
ms.assetid: 5f0e4765-df4d-4887-bd09-efe5e58251bf
caps.latest.revision: 28
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 28
---
# Metodo replace (String) (JavaScript)
Sostituisce il testo in una stringa usando un'espressione regolare o una stringa di ricerca.  
  
## Sintassi  
  
```  
  
stringObj. replace(rgExp, replaceText)  
```  
  
## Parametri  
 `stringObj`  
 Obbligatorio.  Oggetto `String` o valore letterale stringa su cui eseguire la sostituzione.  Questa stringa non viene modificata dal metodo **replace**.  Il valore restituito da questo metodo è piuttosto la stringa prodotta dalla sostituzione.  
  
 `rgExp`  
 Obbligatorio.  Istanza di un oggetto **Espressione regolare** che contiene il modello dell'espressione regolare e i flag applicabili.  Può essere anche un oggetto `String` o un valore letterale stringa che rappresenta l'espressione regolare.  Se `rgExp` non è un'istanza di un oggetto **Espressione regolare**, viene convertito in una stringa e viene eseguita una ricerca esatta dei risultati. Non vengono effettuati tentativi di convertire la stringa in un'espressione regolare.  
  
 `replaceText`  
 Obbligatorio.  Oggetto o `String` valore letterale stringa contenente il testo da sostituire per ogni corrispondenza esatta di `rgExp` in `stringObj`.  In [!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] o versioni successive l'argomento `replaceText` può essere anche una funzione che restituisce il testo di sostituzione.  
  
## Valore restituito  
 Il risultato del metodo **replace** è costituito da una copia di `stringObj` dopo l'applicazione delle sostituzioni specificate.  
  
## Note  
 È possibile usare una delle variabili di corrispondenza seguenti per identificare la corrispondenza più recente e la stringa da cui proviene.  Le variabili di corrispondenza possono essere usate nella sostituzione di testo nei casi in cui la stringa di sostituzione deve essere determinata in modo dinamico.  
  
|Caratteri|Significato|  
|---------------|-----------------|  
|**$$**|`$` \([!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] o versioni successive\)|  
|**$&**|Specifica la parte di `stringObj` corrispondente all'intero criterio.  \([!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] o versioni successive\)|  
|`$``|Specifica la parte di `stringObj` che precede la corrispondenza descritta da **$&**.  \([!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] o versioni successive\)|  
|`$'`|Specifica la parte di `stringObj` che segue la corrispondenza descritta da **$&**.  \([!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] o versioni successive\)|  
|`$`  ***n***|*n*\-esima sottocorrispondenza acquisita, dove *n* è una singola cifra decimale compresa tra 1 e 9.  \([!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] o versioni successive\)|  
|`$`  ***nn***|*nn*\-esima sottocorrispondenza acquisita, dove *nn* è un numero decimale a due cifre compreso tra 01 e 99.  \([!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] o versioni successive\)|  
  
 Se `replaceText` è una funzione, per ogni sottostringa corrispondente viene chiamata la funzione con gli argomenti *m* \+ 3 seguenti, dove *m* è il numero di parentesi di acquisizione in `rgExp`.  Il primo argomento corrisponde alla sottostringa corrispondente.  Gli argomenti *m* successivi corrispondono a tutte le acquisizioni risultanti dalla ricerca.  L'argomento *m* \+ 2 corrisponde all'offset in `stringObj` in cui si è verificata la corrispondenza e l'argomento *m* \+ 3 è `stringObj`.  Il risultato è il valore di stringa ottenuto dalla sostituzione di ogni sottostringa con corrispondenza con il rispettivo valore restituito della chiamata di funzione.  
  
 Il metodo **replace** aggiorna le proprietà dell'oggetto `RegExp` globale.  
  
## Esempio  
 L'esempio seguente illustra l'uso del metodo **replace** per sostituire tutte le istanze di "the" con "a".  
  
```javascript  
var s = "the batter hit the ball with the bat";  
  
// Replace "the" with "a".  
var re = /the/g;  
var result = s.replace(re, "a");  
document.write(result);  
// Output: a batter hit a ball with a bat  
```  
  
 Il metodo **replace** può anche sostituire sottoespressioni nei criteri.  L'esempio seguente scambia ogni coppia di parole nella stringa.  
  
```javascript  
  
var s = "The quick brown fox jumped over the lazy dog.";  
var re = /(\S+)(\s+)(\S+)/g;  
// Exchange each pair of words.  
var result = s.replace(re, "$3$2$1");  
document.write(result);  
  
// Output:  quick The fox brown over jumps lazy the dog.  
```  
  
 L'esempio seguente, compatibile con [!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] e versioni successive, illustra come usare una funzione che restituisce il testo di sostituzione.  Sostituisce qualsiasi istanza di un numero seguito da "F" con una conversione in gradi Celsius.  
  
```javascript  
function f2c(s1) {  
    // Initialize pattern.  
    var test = /(\d+(\.\d*)?)F\b/g;  
  
    // Use a function for the replacement.  
    var s2 = s1.replace(test,  
      function($0,$1,$2)  
           {   
           return((($1-32) * 5/9) + "C");  
           }  
        )  
    return s2;  
}  
document.write(f2c("Water freezes at 32F and boils at 212F."));  
  
// Output: Water freezes at 0C and boils at 100C.  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Applicabile a**: [Oggetto String](../../javascript/reference/string-object-javascript.md)  
  
## Vedere anche  
 [Metodo exec \(Regular Expression\)](../../javascript/reference/exec-method-regular-expression-javascript.md)   
 [Metodo match \(String\)](../../javascript/reference/match-method-string-javascript.md)   
 [Oggetto RegExp](../../javascript/reference/regexp-object-javascript.md)   
 [Metodo search \(String\)](../../javascript/reference/search-method-string-javascript.md)   
 [Metodo test \(Regular Expression\)](../../javascript/reference/test-method-regular-expression-javascript.md)   
 [Regular Expression Programming \(JavaScript\)](http://msdn.microsoft.com/it-it/3b62e27c-4f07-4726-a95b-6e841807bfaf)   
 [Alternation and Subexpressions \(JavaScript\)](http://msdn.microsoft.com/it-it/c59dd3e8-7fee-493e-9123-065af1e651ae)   
 [Backreferences \(JavaScript\)](http://msdn.microsoft.com/it-it/5d8dbd5a-cd03-4548-850b-9d7bad2c839a)   
 [App di esempio di trascinamento HTML5](http://code.msdn.microsoft.com/Drag-and-drop-e2701a72)