---
title: "Funzione decodeURIComponent (JavaScript) | Microsoft Docs"
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
  - "decodeURIComponent"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "decodeURIComponent (metodo)"
ms.assetid: 486ccee2-afd7-4863-97ce-4adb50cf39c0
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Funzione decodeURIComponent (JavaScript)
Ottiene la versione decodificata di un componente codificato di un URI \(Uniform Resource Identifier\).  
  
## Sintassi  
  
```  
decodeURIComponent(encodedURIString)  
```  
  
## Note  
 L'argomento `encodedURIString` obbligatorio è un valore che rappresenta un componente URI codificato.  
  
 Un componente URI fa parte di un URI completo.  
  
 Se il valore di `encodedURIString` non è valido, verrà restituito un URIError.  
  
## Esempio  
 Il seguente codice prima codifica e poi decodifica un URI.  
  
```javascript  
var uriEncode = encodeURI ("http://www.Not a URL.com");  
var uriDecode = decodeURIComponent(uriEncode);  
  
document.write (uriEncode);  
document.write("<br/>");  
document.write (uriDecode);  
  
// Output:  
// http://www.Not%20a%20URL.com  
// http://www.Not a URL.com  
```  
  
## Requisiti  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## Vedere anche  
 [Funzione decodeURI](../../javascript/reference/decodeuri-function-javascript.md)   
 [Funzione encodeURI](../../javascript/reference/encodeuri-function-javascript.md)