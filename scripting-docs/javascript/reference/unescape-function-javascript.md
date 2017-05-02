---
title: "Funzione unescape (JavaScript) | Microsoft Docs"
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
  - "unescape"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "unescape (metodo)"
ms.assetid: 4adf0270-88b5-4d54-8110-d879d6ae97c2
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Funzione unescape (JavaScript)
Decodifica gli oggetti `String` codificati con la funzione `escape`.  Deprecato.  
  
## Sintassi  
  
```  
unescape(charString)   
```  
  
## Note  
 L'argomento `charString` obbligatorio è un oggetto `String` o un valore letterale stringa da decodificare.  
  
 La funzione `unescape` restituisce un valore stringa con il contenuto di `charstring`.  Tutti i caratteri codificati in formato esadecimale %*xx* vengono sostituiti con gli equivalenti del set di caratteri ASCII.  
  
 I caratteri codificati in formato **%u** *xxxx* \(caratteri Unicode\) vengono sostituiti con il carattere Unicode in base al formato di codifica esadecimale *xxxx*.  
  
> [!NOTE]
>  La funzione `unescape` non deve essere utilizzata per codificare gli URI \(Uniform Resource Identifier\).  In alternativa, utilizzare le funzioni `decodeURI` e `decodeURIComponent`.  
  
## Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Si applica a**: [Oggetto Global](../../javascript/reference/global-object-javascript.md)  
  
## Vedere anche  
 [Funzione decodeURI](../../javascript/reference/decodeuri-function-javascript.md)   
 [Funzione decodeURIComponent](../../javascript/reference/decodeuricomponent-function-javascript.md)   
 [Funzione escape](../../javascript/reference/escape-function-javascript.md)   
 [Oggetto String](../../javascript/reference/string-object-javascript.md)