---
title: "Metodo test (Regular Expression) (JavaScript) | Microsoft Docs"
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
  - "test"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "metodo di test"
ms.assetid: 4f4b6e39-cb1a-4be9-a66f-7b846075580d
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Metodo test (Regular Expression) (JavaScript)
Restituisce un valore booleano che indica se una stringa in cui viene eseguita la ricerca include o meno un criterio.  
  
## Sintassi  
  
```  
  
rgExp.test(str)   
```  
  
## Parametri  
 `rgExp`  
 Obbligatorio.  Istanza di un oggetto **Regular Expression** contenente il criterio di ricerca di espressioni regolari e i flag applicabili.  
  
 `str`  
 Obbligatorio.  Stringa in cui eseguire la ricerca.  
  
## Note  
 Il metodo **test** verifica se una stringa include un criterio. Viene restituito **true** se la verifica ha esito positivo, **false** in caso contrario.  
  
 Le proprietà dell'oggetto `RegExp` globale non vengono modificate con il metodo **test**.  
  
## Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo del metodo **test**.  In questo esempio, utilizzare nella funzione un criterio di ricerca di espressioni regolari e una stringa.  Verrà verificata l'occorrenza del criterio di ricerca di espressioni regolari nella stringa e restituita una stringa con i risultati della ricerca:  
  
```javascript  
function TestDemo(re, teststring)  
{  
   // Test string for existence of regular expression.  
   var found = re.test(teststring)  
  
   // Format the output.  
   var s = "";  
   s += "'" + teststring + "'"  
  
   if (found)  
      s += " contains ";  
   else  
      s += " does not contain ";  
  
   s += "'" + re.source + "'"  
   return(s);  
}  
```  
  
## Requisiti  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Si applica a**: [Oggetto Regular Expression](../../javascript/reference/regular-expression-object-javascript.md)  
  
## Vedere anche  
 [Oggetto RegExp](../../javascript/reference/regexp-object-javascript.md)   
 [Oggetto Regular Expression](../../javascript/reference/regular-expression-object-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/it-it/ab0766e1-7037-45ed-aa23-706f58358c0e)