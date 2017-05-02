---
title: "Propriet&#224; ignoreCase (Regular Expression) (JavaScript) | Microsoft Docs"
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
  - "ignoreCase"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "IgnoreCase (proprietà)"
ms.assetid: 816f0df5-5a82-44a5-a4ab-dbc91fa76e61
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# Propriet&#224; ignoreCase (Regular Expression) (JavaScript)
Restituisce un valore booleano che indica lo stato del flag ignoreCase \(**i**\) utilizzato con un'espressione regolare.  L'impostazione predefinita è **false**.  Sola lettura.  
  
## Sintassi  
  
```  
  
rgExp.ignoreCase  
```  
  
## Note  
 Il riferimento `rgExp` obbligatorio è un'istanza dell'oggetto `RegExp`.  
  
 La proprietà **ignoreCase** restituisce **true** se il flag ignoreCase è impostato per un'espressione regolare, **false** in caso contrario.  
  
 Quando impostato, il flag ignoreCase indica che nella ricerca deve essere ignorata la differenza tra maiuscole e minuscole nella corrispondenza del criterio nella stringa cercata.  
  
## Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo della proprietà **ignoreCase**.  Se si passa "gi" alla funzione illustrata di seguito, tutte le istanze della parola "the" verranno sostituite dalla parola "a", inclusa la parola "The" iniziale.  Questo comportamento è determinato dal fatto che quando è impostato il flag ignoreCase, la ricerca ignora qualsiasi distinzione tra maiuscole e minuscole.  Ai fini della corrispondenza, pertanto, "T" equivale a "t".  
  
 Questa funzione restituisce i valori booleani che indicano lo stato dei flag dell'espressione regolare consentiti, ovvero **g**, **i** e **m**.  La funzione restituisce inoltre la stringa con tutte le sostituzioni apportate.  
  
```javascript  
function RegExpPropDemo(flag){  
    // The flag parameter is a string that contains  
    // g, i, or m. The flags can be combined.  
  
    // Check flags for validity.  
    if (flag.match(/[^gim]/))  
        {  
        return ("Flag specified is not valid");  
        }  
  
    // Create the string on which to perform the replacement.  
    var orig = "The batter hit the ball with the bat ";  
    orig += "and the fielder caught the ball with the glove.";  
  
    // Replace "the" with "a".  
    var re = new RegExp("the", flag);  
    var r = orig.replace(re, "a");          
  
    // Output the resulting string and the values of the flags.  
    var s = "";  
    s += "global: " + re.global.toString();  
    s += "<br />";  
    s += "ignoreCase: " + re.ignoreCase.toString();  
    s += "<br />";  
    s += "multiline: " + re.multiline.toString();  
    s += "<br />";  
    s += "Resulting String: " + r;  
    s += "<br />";  
    s += "<br />";  
    return (s);  
}  
  
document.write(RegExpPropDemo("gi"));  
document.write(RegExpPropDemo("g"));  
```  
  
## Esempio  
 Di seguito è riportato l'output risultante.  
  
```javascript  
global: true  
ignoreCase: true  
multiline: false  
Resulting String: a batter hit a ball with a bat and a fielder caught a ball with a glove.  
  
global: true  
ignoreCase: false  
multiline: false  
Resulting String: The batter hit a ball with a bat and a fielder caught a ball with a glove.  
```  
  
## Requisiti  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Si applica a**: [Oggetto Regular Expression](../../javascript/reference/regular-expression-object-javascript.md)  
  
## Vedere anche  
 [Proprietà global \(Regular Expression\)](../../javascript/reference/global-property-regular-expression-javascript.md)   
 [Proprietà multiline \(Regular Expression\)](../../javascript/reference/multiline-property-regular-expression-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/it-it/ab0766e1-7037-45ed-aa23-706f58358c0e)