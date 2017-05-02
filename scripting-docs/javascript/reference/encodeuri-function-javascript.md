---
title: "Funzione encodeURI (JavaScript) | Microsoft Docs"
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
  - "encodeURI"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "encodeURI (metodo)"
ms.assetid: 17bab5a2-bcd4-46c2-8b52-b2b5a0ed98a3
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Funzione encodeURI (JavaScript)
Codifica una stringa di testo come URI \(Uniform Resource Identifier\) valido.  
  
## Sintassi  
  
```  
  
encodeURI(  
URIString  
)  
  
```  
  
## Note  
 L'argomento `URIString` obbligatorio è un valore che rappresenta un URI codificato.  
  
 La funzione `encodeURI` restituisce un URI codificato.  Se si passa il risultato a `decodeURI`, viene restituita la stringa originale.  La funzione `encodeURI` non consente di codificare i seguenti caratteri: ":", "\/", ";" e "?".  Per codificare tali caratteri, utilizzare il metodo `encodeURIComponent`.  
  
## Esempio  
 Il seguente codice prima codifica e poi decodifica un URI.  
  
```javascript  
var uriEncode = encodeURI ("http://www.Not a URL.com");  
var uriDecode = decodeURIComponent(uriEncode);  
  
document.write(uriEncode);  
document.write("<br/>");  
document.write(uriDecode);  
  
// Output:  
// http://www.Not%20a%20URL.com  
// http://www.Not a URL.com  
```  
  
## Requisiti  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## Vedere anche  
 [Funzione decodeURI](../../javascript/reference/decodeuri-function-javascript.md)   
 [Funzione decodeURIComponent](../../javascript/reference/decodeuricomponent-function-javascript.md)