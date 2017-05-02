---
title: "Propriet&#224; multiline (Regular Expression) (JavaScript) | Microsoft Docs"
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
  - "multiline"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "multiline (proprietà)"
ms.assetid: ca7b276a-1fe2-4189-ac27-f089ab3e9974
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Propriet&#224; multiline (Regular Expression) (JavaScript)
Restituisce un valore booleano che indica lo stato del flag multiline \(**m**\) utilizzato con un'espressione regolare.  L'impostazione predefinita è **false**.  Sola lettura.  
  
## Sintassi  
  
```  
  
rgExp.multiline  
```  
  
## Note  
 L'argomento `rgExp` obbligatorio è un'istanza dell'oggetto `RegExp`.  
  
 La proprietà **multiline** restituisce **true** se il flag multiline è impostato per un'espressione regolare, **false** in caso contrario.  Il valore della proprietà **multiline** è **true** se l'oggetto espressione regolare è stato creato con il flag **m**.  
  
 Se il valore della proprietà **multiline** è **false**, "^" corrisponde alla posizione iniziale di una stringa, mentre "$" alla posizione finale.  Se il valore della proprietà **multiline** è **true**, "^" corrisponde alla posizione iniziale di una stringa e a quella che segue un carattere "\\n" o "\\r", mentre "$" corrisponde alla posizione finale e a quella che precede un carattere "\\n" o "\\r".  
  
## Esempio  
 Nell'esempio seguente viene illustrato il comportamento della proprietà **multiline**.  Se si passa "m" alla funzione illustrata di seguito, la parola "while" verrà sostituita dalla parola "and".  Questo comportamento è dovuto all'impostazione del flag multiline e alla posizione della parola "while" all'inizio della riga dopo un carattere di nuova riga.  Il flag multiline consente l'esecuzione della ricerca in stringhe su più righe.  
  
```javascript  
function RegExpMultilineDemo(flag){  
   // The flag parameter is a string that contains  
   // g, i, or m.  The flags can be combined.  
  
   // Check flags for validity.  
   if (flag.match(/[^gim]/))  
      {  
      return ("Flag specified is not valid");  
      }  
  
   // Create the string on which to perform the replacement.  
   var ss = "The man hit the ball with the bat ";  
   ss += "\nwhile the fielder caught the ball with the glove.";  
  
   // Replace "while" with "and".  
   var re = new RegExp("^while", flag);  
   var r = ss.replace(re, "and");          
  
   // Output the multiline flag and the resulting string.  
   var s = "";  
   s += "Result for multiline = " + re.multiline.toString();  
   s += ": " + r;  
  
   return(s);  
  
}  
  
sa = RegExpMultilineDemo("m");  
sb = RegExpMultilineDemo("");  
document.write (sa + "<br />" + sb);  
```  
  
## Requisiti  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Si applica a**: [Oggetto Regular Expression](../../javascript/reference/regular-expression-object-javascript.md)  
  
## Vedere anche  
 [Proprietà global \(Regular Expression\)](../../javascript/reference/global-property-regular-expression-javascript.md)   
 [Proprietà ignoreCase \(Regular Expression\)](../../javascript/reference/ignorecase-property-regular-expression-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/it-it/ab0766e1-7037-45ed-aa23-706f58358c0e)