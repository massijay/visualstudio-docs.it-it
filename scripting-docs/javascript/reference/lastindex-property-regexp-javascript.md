---
title: "Propriet&#224; lastIndex (RegExp) (JavaScript) | Microsoft Docs"
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
  - "lastIndex"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "lastIndex (proprietà)"
ms.assetid: c8ae2a13-6dff-4cbe-b662-aca3d66c2a7f
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# Propriet&#224; lastIndex (RegExp) (JavaScript)
Restituisce la posizione del carattere in cui inizia la successiva corrispondenza individuata in una stringa.  
  
## Sintassi  
  
```  
  
RegExp.lastIndex  
```  
  
## Note  
 L'oggetto associato a questa proprietà è sempre l'oggetto globale `RegExp`.  
  
 La proprietà `lastIndex` è a base zero, ovvero l'indice del primo carattere è zero.  Il valore iniziale è –1.  Il valore viene modificato ogni volta che viene individuata una corrispondenza.  
  
 La proprietà `lastIndex` viene modificata tramite i metodi `exec` e **test** dell'oggetto `RegExp` e dai metodi `match`, **replace** e **split** dell'oggetto `String`.  
  
 Per l'impostazione del valore della proprietà `lastIndex` vengono adottati i seguenti criteri:  
  
-   Se non viene individuata alcuna corrispondenza, la proprietà viene impostata su \-1.  
  
-   Se il valore di `lastIndex` è maggiore della lunghezza della stringa, i metodi **test** ed `exec` avranno esito negativo e la proprietà verrà impostata su \-1.  
  
-   Se il valore di `lastIndex` è uguale alla lunghezza della stringa, esisterà una corrispondenza dell'espressione regolare se i criteri di ricerca corrispondono alla stringa vuota.  In caso contrario, non sarà disponibile alcuna corrispondenza e la proprietà `lastIndex` verrà reimpostata su \-1.  
  
-   Negli altri casi, la proprietà `lastIndex` viene impostata sulla posizione successiva all'ultima corrispondenza individuata.  
  
## Esempio  
 Nell'esempio riportato di seguito viene illustrato l'utilizzo della proprietà `lastIndex`.  Mediante questa funzione viene ripetuta la ricerca in una stringa e vengono stampati i valori **index** e `lastIndex` per ciascuna parola della stringa.  
  
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
      document.write (arr.index + "-" + re.lastIndex + " ");  
      document.write (arr);  
      }  
}  
```  
  
## Requisiti  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Si applica a**: [Oggetto RegExp](../../javascript/reference/regexp-object-javascript.md)  
  
## Vedere anche  
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/it-it/ab0766e1-7037-45ed-aa23-706f58358c0e)