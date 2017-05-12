---
title: "Metodo exec (Regular Expression) (JavaScript) | Microsoft Docs"
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
  - "exec"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "exec (metodo)"
  - "stringhe corrispondenti"
ms.assetid: 83092452-60cc-4218-b4ae-af9e3cb96c34
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# Metodo exec (Regular Expression) (JavaScript)
Esegue una ricerca in una stringa utilizzando un criterio di ricerca di espressioni regolari e restituisce una matrice contenente i risultati della ricerca.  
  
## Sintassi  
  
```  
  
rgExp.exec(str)   
```  
  
## Parametri  
 `rgExp`  
 Obbligatorio.  Istanza di un oggetto **Regular Expression** contenente il criterio di ricerca di espressioni regolari e i flag applicabili.  
  
 `str`  
 Obbligatorio.  Oggetto `String` o valore letterale stringa in cui eseguire la ricerca.  
  
## Note  
 Se mediante il metodo `exec` non viene trovata alcuna corrispondenza, verrà restituito `null`.  In caso contrario, verrà restituita una matrice da `exec` e le proprietà dell'oggetto `RegExp` globale verranno aggiornate in modo da riflettere i risultati della corrispondenza.  L'elemento zero della matrice contiene l'intera corrispondenza, mentre gli elementi da 1 a *n* contengono qualsiasi sottocorrispondenza presente all'interno della corrispondenza.  Il comportamento è identico a quello del metodo `match` senza il flag globale \(**g**\) impostato.  
  
 Se per un'espressione regolare è impostato il flag globale, in `exec` verrà cercata la stringa che ha inizio nella posizione indicata dal valore di `lastIndex`.  Se il flag globale non è impostato, in `exec` viene ignorato il valore di `lastIndex` e viene eseguita la ricerca dall'inizio della stringa.  
  
 La matrice restituita dal metodo `exec` ha tre proprietà: **input**, **index** e **lastIndex.** La proprietà **input** contiene l'intera stringa cercata.  La proprietà **index** contiene la posizione della sottostringa corrispondente all'interno dell'intera stringa cercata.  La proprietà `lastIndex` contiene la posizione che segue l'ultimo carattere nella corrispondenza.  
  
## Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo del metodo `exec`:  
  
```javascript  
function RegExpTest()  
{  
   var ver = Number(ScriptEngineMajorVersion() + "." + ScriptEngineMinorVersion())  
   if (ver < 5.5)  
   {  
      document.write("You need a newer version of JavaScript for this to work");  
      return;  
   }  
  
   var src = "The quick brown fox jumps over the lazy dog.";  
  
   // Create regular expression pattern with a global flag.  
   var re = /\w+/g;  
  
   // Get the next word, starting at the position of lastindex.  
   var arr;  
   while ((arr = re.exec(src)) != null)  
      {  
      // New line:  
      document.write ("<br />");    
      document.write (arr.index + "-" + arr.lastIndex + " ");  
      document.write (arr[0]);  
      }  
}  
```  
  
## Requisiti  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Si applica a**: [Oggetto Regular Expression](../../javascript/reference/regular-expression-object-javascript.md)  
  
## Vedere anche  
 [Metodo match \(String\)](../../javascript/reference/match-method-string-javascript.md)   
 [Oggetto RegExp](../../javascript/reference/regexp-object-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/it-it/ab0766e1-7037-45ed-aa23-706f58358c0e)   
 [Metodo search \(String\)](../../javascript/reference/search-method-string-javascript.md)   
 [Metodo test \(Regular Expression\)](../../javascript/reference/test-method-regular-expression-javascript.md)   
 [Regular Expression Programming \(JavaScript\)](http://msdn.microsoft.com/it-it/3b62e27c-4f07-4726-a95b-6e841807bfaf)