---
title: "Funzione decodeURI (JavaScript) | Microsoft Docs"
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
  - "decodeURI"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "decodeURI (metodo)"
ms.assetid: af6c81dc-10f4-4243-a7ce-d18ae3ea0fb8
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Funzione decodeURI (JavaScript)
Ottiene la versione decodificata di un URI \(Uniform Resource Identifier\) codificato.  
  
## Sintassi  
  
```  
decodeURI(URIstring)  
```  
  
## Note  
 L'argomento `URIstring` obbligatorio è un valore che rappresenta un URI codificato.  
  
 Utilizza la funzione `decodeURI` invece della funzione `unescape` deprecata.  
  
 La funzione `decodeURI` restituisce un valore stringa.  
  
 Se il valore di `URIString` non è valido, verrà restituito un URIError.  
  
 **Si applica a**: [Oggetto Global](../../javascript/reference/global-object-javascript.md)  
  
## Esempio  
 Il seguente codice prima codifica un componente URI e poi lo decodifica.  
  
```javascript  
var uriEncode = encodeURIComponent ("www.Not a URL.com");  
var uriDecode = decodeURIComponent(uriEncode);  
  
document.write (uriEncode);  
document.write ("<br/>");  
document.write (uriDecode);  
  
// Output:  
// www.Not%20a%20URL.com  
// www.Not a URL.com  
```  
  
## Requisiti  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## Vedere anche  
 [Funzione decodeURIComponent](../../javascript/reference/decodeuricomponent-function-javascript.md)   
 [Funzione encodeURI](../../javascript/reference/encodeuri-function-javascript.md)   
 [Oggetto Global](../../javascript/reference/global-object-javascript.md)