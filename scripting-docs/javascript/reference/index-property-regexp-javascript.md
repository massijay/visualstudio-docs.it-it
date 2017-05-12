---
title: "Propriet&#224; index (RegExp) (JavaScript) | Microsoft Docs"
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
  - "index"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Index (proprietà)"
  - "stringhe corrispondenti"
ms.assetid: d8be1ef6-1bf2-43cd-b0b5-567a61eabaad
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# Propriet&#224; index (RegExp) (JavaScript)
Restituisce la posizione del carattere in cui inizia la prima corrispondenza individuata in una stringa.  Sola lettura.  
  
## Sintassi  
  
```  
  
RegExp.index   
```  
  
## Note  
 L'oggetto associato a questa proprietà è sempre l'oggetto `RegExp` globale.  
  
 La proprietà **index** in base zero.  Il valore iniziale della proprietà **index** è –1.  Il valore cambia ogni volta che viene individuata una corrispondenza.  
  
## Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo della proprietà **index**.  Mediante questa funzione viene ripetuta la ricerca in una stringa e vengono stampati i valori **index** e `lastIndex` per ciascuna parola della stringa.  
  
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
      document.write (arr);  
      }  
}  
```  
  
## Requisiti  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Si applica a**: [Oggetto RegExp](../../javascript/reference/regexp-object-javascript.md)  
  
## Vedere anche  
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/it-it/ab0766e1-7037-45ed-aa23-706f58358c0e)