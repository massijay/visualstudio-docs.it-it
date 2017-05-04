---
title: "Oggetto Function (JavaScript) | Microsoft Docs"
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
  - "function"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Function (oggetto)"
ms.assetid: d3834767-203c-475e-848c-95c423ba15b6
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Oggetto Function (JavaScript)
Consente di creare una nuova funzione.  
  
## Sintassi  
  
```  
function functionName([argname1  [, ...[, argnameN]]])  
{  
   body  
}  
```  
  
## Sintassi  
  
```  
  
functionName = new Function( [argname1,  [... argnameN,]] body );  
```  
  
## Parametri  
 `functionName`  
 Obbligatorio.  Nome della funzione appena creata.  
  
 `argname1...argnameN`  
 Facoltativo.  Elenco di argomenti che la funzione accetta.  
  
 `body`  
 Facoltativo.  Stringa contenente il blocco di codice [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] da eseguire alla chiamata della funzione.  
  
## Note  
 La funzione è un tipo di dati di base in [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  La sintassi 1 crea un valore di funzione che [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] converte in un oggetto `Function` se necessario.  [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] converte gli oggetti `Function` creati dalla sintassi 2 in valori di funzione quando la funzione viene chiamata.  
  
 La sintassi 1 rappresenta la modalità standard di creazione delle nuove funzioni in [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  La sintassi 2 è un modulo alternativo utilizzato per creare oggetti funzione in modo esplicito.  
  
 Ad esempio, per dichiarare una funzione che aggiunge i due argomenti passati alla sintassi, puoi procedere in due modi:  
  
## Esempio 1  
  
```javascript  
function add(x, y)  
{  
   return(x + y);  
}  
```  
  
## Esempio 2  
  
```  
var add = function(x, y) {  
     return(x+y);  
}  
```  
  
 In entrambi i casi, chiama la funzione con una riga di codice simile al seguente:  
  
```javascript  
add(2, 3);  
```  
  
> [!NOTE]
>  Nelle chiamate di funzioni assicurati di includere sempre le parentesi ed eventuali argomenti obbligatori.  Se chiami una funzione senza utilizzare le parentesi, verrà restituita la funzione stessa e non il relativo valore restituito.  
  
## Proprietà  
 [0...  
          Proprietà n](../../javascript/reference/0-dot-dot-dot-n-properties-arguments-javascript.md) &#124;[Proprietà arguments](../../javascript/reference/arguments-property-function-javascript.md) &#124; [Proprietà callee](../../javascript/reference/callee-property-arguments-javascript.md) &#124; [Proprietà caller](../../javascript/reference/caller-property-function-javascript.md) &#124; [Proprietà constructor](../../javascript/reference/constructor-property-object-javascript.md) &#124; [Proprietà length \(Function\)](../../javascript/reference/length-property-function-javascript.md) &#124; [Proprietà prototype](../../javascript/reference/prototype-property-object-javascript.md)  
  
## Metodi  
 [Metodo apply](../../javascript/reference/apply-method-function-javascript.md) &#124; [Metodo bind](../../javascript/reference/bind-method-function-javascript.md) &#124; [Metodo call](../../javascript/reference/call-method-function-javascript.md) &#124; [Metodo toString](../../javascript/reference/tostring-method-object-javascript.md) &#124; [Metodo valueOf](../../javascript/reference/valueof-method-object-javascript.md)  
  
## Requisiti  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## Vedere anche  
 [Istruzione function](../../javascript/reference/function-statement-javascript.md)   
 [Operatore new](../../javascript/reference/new-operator-decrementjavascript.md)   
 [Istruzione var](../../javascript/reference/var-statement-javascript.md)