---
title: "Funzione escape (JavaScript) | Microsoft Docs"
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
  - "escape"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "codifica di oggetti String"
  - "Escape (metodo)"
  - "esadecimale"
  - "String (object), codifica"
ms.assetid: caa92bea-ba69-4109-a68a-6e2debda463a
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Funzione escape (JavaScript)
Codifica le stringhe in modo che siano leggibili su tutti i computer.  Deprecato.  
  
## Sintassi  
  
```  
escape(charString)   
```  
  
## Note  
 L'argomento `charString` obbligatorio è un oggetto `String` o un valore letterale stringa da codificare.  
  
 La funzione **escape** restituisce un valore stringa in formato Unicode che include il contenuto di `charstring`.  Tutti gli spazi, i segni di punteggiatura, i caratteri accentati e qualsiasi altro carattere non ASCII vengono sostituiti con il formato di codifica `%`*xx*, dove *xx* equivale al numero esadecimale che rappresenta il carattere.  Uno spazio, ad esempio, viene restituito come "%20".  
  
 I caratteri con valore maggiore di 255 vengono archiviati nel formato **%u** *xxxx*.  
  
> [!NOTE]
>  La funzione **escape** non deve essere utilizzata per codificare gli URI \(Uniform Resource Identifier\).  In alternativa, utilizzare le funzioni `encodeURI` e `encodeURIComponent`.  
  
 **Si applica a**: [Oggetto Global](../../javascript/reference/global-object-javascript.md)  
  
## Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Vedere anche  
 [Funzione encodeURI](../../javascript/reference/encodeuri-function-javascript.md)   
 [Funzione encodeURIComponent](../../javascript/reference/encodeuricomponent-function-javascript.md)   
 [Oggetto String](../../javascript/reference/string-object-javascript.md)   
 [Funzione unescape](../../javascript/reference/unescape-function-javascript.md)