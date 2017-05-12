---
title: "Metodo match (String) (JavaScript) | Microsoft Docs"
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
  - "match"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Match (metodo)"
ms.assetid: eda9ad27-4f9b-4cb1-8345-a0ae85979ca0
caps.latest.revision: 22
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 22
---
# Metodo match (String) (JavaScript)
Corrisponde a una stringa con un'espressione regolare e restituisce una matrice contenente i risultati della ricerca.  
  
## Sintassi  
  
```  
  
stringObj.match(rgExp)   
```  
  
## Parametri  
 `stringObj`  
 Necessario.  Oggetto `String` o valore letterale stringa in cui eseguire la ricerca.  
  
 `rgExp`  
 Necessario.  Oggetto espressione regolare che contiene il modello di espressione regolare e i flag applicabili.  Può anche essere un nome di variabile o un valore letterale stringa contenente il criterio di espressione regolare e i flag.  
  
## Note  
 Se mediante il metodo `match` non viene trovata alcuna corrispondenza, verrà restituito `null`.  In caso contrario, verrà restituita una matrice e le proprietà dell'oggetto globale `RegExp` verranno aggiornate per riflettere i risultati di tale corrispondenza.  
  
 Se il flag globale \(`g`\) non è impostato, l'elemento zero della matrice contiene l'intera corrispondenza, mentre gli elementi da 1 a *n* contengono le sottocorrispondenze.  Questo comportamento è identico a quello di [Metodo exec \(Regular Expression\)](../../javascript/reference/exec-method-regular-expression-javascript.md) quando il flag globale non è impostato.  Con il flag globale impostato, gli elementi da 0 a *n* includono tutte le corrispondenze.  
  
 Se il flag globale non è impostato, la matrice restituita dal metodo `match` ha due proprietà, `input` e `index`.  La proprietà `input` contiene l'intera stringa in cui viene eseguita la ricerca.  La proprietà `index` contiene la posizione della sottostringa corrispondente all'interno della stringa completa in cui viene eseguita la ricerca.  
  
 Se è impostato il flag `i`, durante la ricerca non viene applicata la distinzione tra maiuscole e minuscole.  
  
## Esempio  
 Nell'esempio riportato di seguito viene illustrato l'utilizzo del metodo `match`.  
  
```javascript  
var src = "azcafAJAC";  
  
var re = /[a-c]/;  
  
var result = src.match(re);  
  
// The entire match is in array element 0.  
document.write(result[0] + "<br/>");  
  
// Now try the same match with the global flag.  
var reg = /[a-c]/g;  
result = src.match(reg);  
  
// The matches are in elements 0 through n.  
for (var index = 0; index < result.length; index++)  
{  
    document.write ("submatch " + index + ": " +  result[index]);  
    document.write("<br />");  
}  
```  
  
## Requisiti  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Si applica a**: [Oggetto String](../../javascript/reference/string-object-javascript.md)  
  
## Vedere anche  
 [Metodo exec \(Regular Expression\)](../../javascript/reference/exec-method-regular-expression-javascript.md)   
 [Oggetto RegExp](../../javascript/reference/regexp-object-javascript.md)   
 [Oggetto Regular Expression](../../javascript/reference/regular-expression-object-javascript.md)   
 [Metodo replace \(String\)](../../javascript/reference/replace-method-string-javascript.md)   
 [Metodo search \(String\)](../../javascript/reference/search-method-string-javascript.md)   
 [Metodo test \(Regular Expression\)](../../javascript/reference/test-method-regular-expression-javascript.md)   
 [Regular Expression Programming \(JavaScript\)](http://msdn.microsoft.com/it-it/3b62e27c-4f07-4726-a95b-6e841807bfaf)   
 [Alternation and Subexpressions \(JavaScript\)](http://msdn.microsoft.com/it-it/c59dd3e8-7fee-493e-9123-065af1e651ae)   
 [Backreferences \(JavaScript\)](http://msdn.microsoft.com/it-it/5d8dbd5a-cd03-4548-850b-9d7bad2c839a)