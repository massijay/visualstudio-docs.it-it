---
title: "Funzione encodeURIComponent (JavaScript) | Microsoft Docs"
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
  - "encodeURIComponent"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "encodeURIComponent (metodo)"
ms.assetid: 8202bce6-1342-40dc-a5ef-ac6d210a7d15
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Funzione encodeURIComponent (JavaScript)
Codifica una stringa di testo come componente valido di un URI \(Uniform Resource Identifier\).  
  
## Sintassi  
  
```  
encodeURIComponent(encodedURIString)  
```  
  
## Note  
 L'argomento `encodedURIString` obbligatorio è un valore che rappresenta un componente URI codificato.  
  
 La funzione `encodeURIComponent` restituisce un URI codificato.  Se si passa il risultato a `decodeURIComponent`, viene restituita la stringa originale.  Dal momento che la funzione `encodeURIComponent` codifica tutti i caratteri, prestare attenzione se la stringa rappresenta un percorso quale \/folder1\/folder2\/default.html.  Le barre verranno codificate e non saranno valide se inviate come richiesta a un server Web.  Utilizzare la funzione `encodeURI` se la stringa contiene più di un componente URI.  
  
## Esempio  
 Il seguente codice prima codifica un componente URI e poi lo decodifica.  
  
```javascript  
var uriEncode = encodeURIComponent ("www.Not a URL.com");  
var uriDecode = decodeURIComponent(uriEncode);  
  
document.write(uriEncode);  
document.write("<br/>");  
document.write(uriDecode);  
  
// Output:  
// www.Not%20a%20URL.com  
// www.Not a URL.com  
```  
  
## Requisiti  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## Vedere anche  
 [Funzione decodeURI](../../javascript/reference/decodeuri-function-javascript.md)   
 [Funzione decodeURIComponent](../../javascript/reference/decodeuricomponent-function-javascript.md)