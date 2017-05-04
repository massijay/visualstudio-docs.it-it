---
title: "Propriet&#224; global (Regular Expression) (JavaScript) | Microsoft Docs"
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
  - "Global"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "global (proprietà)"
ms.assetid: 76a0f115-0d89-4aca-86d5-932895c6d649
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# Propriet&#224; global (Regular Expression) (JavaScript)
Restituisce un valore booleano che indica lo stato del flag globale \(**g**\) utilizzato con un'espressione regolare.  L'impostazione predefinita è **false**.  Sola lettura.  
  
## Sintassi  
  
```  
  
rgExp.global  
```  
  
## Note  
 Il riferimento `rgExp` obbligatorio è un'istanza di un oggetto **Regular Expression**.  
  
 La proprietà `global` restituisce **true** se il flag globale è impostato per un'espressione regolare, **false** in caso contrario.  
  
 Quando utilizzato, il flag globale indica che in una ricerca devono essere individuate tutte le occorrenze del modello nella stringa in cui viene eseguita la ricerca e non solo nella prima.  È noto anche come corrispondenza globale.  
  
## Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo della proprietà `global`.  Se si passa **g** alla funzione illustrata di seguito, tutte le istanze della parola "the" vengono sostituite dalla parola "a".  Si noti che la parola "The" all'inizio della stringa non viene sostituita in quanto il flag **i** \(che consente di ignorare la distinzione tra maiuscole e minuscole\) non viene passato alla funzione.  
  
 Questa funzione visualizza la condizione delle proprietà associate ai flag dell'espressione regolare consentiti, ovvero **g**, **i** e **m**.  La funzione inoltre visualizza la stringa con tutte le sostituzioni apportate.  
  
```javascript  
function RegExpPropDemo(flag){  
   // The flag parameter is a string that contains  
   // g, i, or m.  The flags can be combined.  
  
   // Check flags for validity.  
   if (flag.match(/[^gim]/))  
      {  
      return ("Flag specified is not valid");  
      }  
  
   // Create the string on which to perform the replacement.  
   var ss = "The batter hit the ball with the bat ";  
   ss += "and the fielder caught the ball with the glove.";  
  
   //Replace "the" with "a".  
   var re = new RegExp("the", flag);  
   var r = ss.replace(re, "a");          
  
   // Output the resulting string and the flags.  
   var s = "";  
   s += "global: " + re.global.toString();  
   s += "<br />";  
   s += "ignoreCase: " + re.ignoreCase.toString();  
   s += "<br />";  
   s += "multiline: " + re.multiline.toString();  
   s += "<br />";  
   s += "Resulting String: " + r;  
  
   return (s);  
}  
  
document.write(RegExpPropDemo("g"));  
```  
  
## Esempio  
 Di seguito è riportato l'output risultante.  
  
```javascript  
global: true  
ignoreCase: false  
multiline: false  
Resulting String: The batter hit a ball with a bat and a fielder caught a ball with a glove.  
```  
  
## Requisiti  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Si applica a**: [Oggetto Regular Expression](../../javascript/reference/regular-expression-object-javascript.md)  
  
## Vedere anche  
 [Proprietà ignoreCase \(Regular Expression\)](../../javascript/reference/ignorecase-property-regular-expression-javascript.md)   
 [Proprietà multiline \(Regular Expression\)](../../javascript/reference/multiline-property-regular-expression-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/it-it/ab0766e1-7037-45ed-aa23-706f58358c0e)