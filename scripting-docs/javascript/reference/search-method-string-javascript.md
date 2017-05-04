---
title: "Metodo search (String) (JavaScript) | Microsoft Docs"
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
  - "search"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "search (metodo)"
ms.assetid: 1cae0fbc-3319-4327-ba4e-d5fa2c4a9ba0
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# Metodo search (String) (JavaScript)
Trova la prima corrispondenza di una sottostringa in una ricerca di espressioni regolari.  
  
## Sintassi  
  
```  
  
stringObj.search(rgExp)   
```  
  
## Parametri  
 `stringObj`  
 Obbligatorio.  Oggetto `String` o valore letterale stringa in cui eseguire la ricerca.  
  
 `rgExp`  
 Obbligatorio.  Istanza di un oggetto **Regular Expression** contenente il criterio di ricerca di espressioni regolari e i flag applicabili.  
  
## Valore restituito  
 Se viene individuata una corrispondenza, il metodo **search** restituisce un valore intero che indica l'offset dall'inizio della stringa in cui è stata individuata la prima corrispondenza.  Se non viene trovata alcuna corrispondenza, viene restituito \-1.  
  
## Note  
 Puoi anche impostare il flag `i` per eseguire la ricerca senza distinzione tra maiuscole e minuscole.  
  
## Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo del metodo **search**.  
  
```javascript  
var src = "is but a Dream within a dream";  
var re = /dream/;  
var pos = src.search(re);  
document.write(pos);  
document.write("<br/>");  
  
re = /dream/i;  
pos = src.search(re);  
document.write(pos);  
  
// Output:   
// 24   
// 9  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Si applica a**: [Oggetto String](../../javascript/reference/string-object-javascript.md)  
  
## Vedere anche  
 [Metodo exec \(Regular Expression\)](../../javascript/reference/exec-method-regular-expression-javascript.md)   
 [Metodo match \(String\)](../../javascript/reference/match-method-string-javascript.md)   
 [Oggetto Regular Expression](../../javascript/reference/regular-expression-object-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/it-it/ab0766e1-7037-45ed-aa23-706f58358c0e)   
 [Metodo replace \(String\)](../../javascript/reference/replace-method-string-javascript.md)   
 [Metodo test \(Regular Expression\)](../../javascript/reference/test-method-regular-expression-javascript.md)   
 [Regular Expression Programming \(JavaScript\)](http://msdn.microsoft.com/it-it/3b62e27c-4f07-4726-a95b-6e841807bfaf)