---
title: "Metodo compile (Regular Expression) (JavaScript) | Microsoft Docs"
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
  - "compile"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Compile (metodo)"
  - "compilazione di codice sorgente, espressioni regolari"
  - "espressioni regolari, compilazione"
ms.assetid: dc28cae3-478d-49b5-b5ea-203e5edfe195
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# Metodo compile (Regular Expression) (JavaScript)
Consente di compilare un'espressione regolare in un formato interno che ne rende più rapida l'esecuzione.  
  
## Sintassi  
  
```  
  
rgExp.compile(pattern, [flags])   
```  
  
## Parametri  
 `rgExp`  
 Obbligatorio.  Istanza di un oggetto **Regular Expression**.  Può essere un nome di variabile o un valore letterale.  
  
 *pattern*  
 Obbligatorio.  Espressione stringa contenente i criteri di ricerca di espressioni regolari da compilare.  
  
 `flags`  
 Facoltativo.  I flag disponibili che possono essere combinati sono:  
  
-   g \(ricerca globale di tutte le occorrenze di *pattern*\);  
  
-   i \(ignora la distinzione tra maiuscole e minuscole\);  
  
-   m \(ricerca su più righe\).  
  
## Note  
 Mediante il metodo **compile**, l'argomento *pattern* viene convertito in un formato interno che ne rende più rapida l'esecuzione.  L'utilizzo di espressioni regolari, ad esempio nei cicli, risulta pertanto più efficiente.  L'esecuzione viene accelerata quando una stessa espressione regolare compilata viene utilizzata più volte.  Non si otterrà invece alcun vantaggio se l'espressione regolare cambia.  
  
## Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo del metodo **compile**:  
  
```javascript  
function CompileDemo(){  
   var rs;  
   var s = "AaBbCcDdEeFfGgHhIiJjKkLlMmNnOoPp"  
   // Create regular expression for uppercase only.  
   var r = new RegExp("[A-Z]", "g");  
   var a1 = s.match(r)              // Find matches.  
   // Compile the regular expression for lowercase only.  
   r.compile("[a-z]", "g");  
// Find matches.  
   var a2 = s.match(r)                
   return(a1 + "\n" + a2);  
}  
```  
  
## Requisiti  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Si applica a**: [Oggetto Regular Expression](../../javascript/reference/regular-expression-object-javascript.md)  
  
## Vedere anche  
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/it-it/ab0766e1-7037-45ed-aa23-706f58358c0e)