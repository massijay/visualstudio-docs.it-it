---
title: "Metodo charAt (String) (JavaScript) | Microsoft Docs"
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
  - "charAt"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "String (oggetto), restituzione di caratteri"
  - "charAt (metodo)"
  - "caratteri, restituzione parziale"
ms.assetid: 63173e15-17f6-47c5-8f94-98ef1eb04c1a
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# Metodo charAt (String) (JavaScript)
Restituisce il carattere in corrispondenza dell'indice specificato.  
  
## Sintassi  
  
```  
  
strObj. charAt(index)  
```  
  
## Parametri  
 `strObj`  
 Obbligatorio.  Qualsiasi oggetto `String` o valore letterale stringa.  
  
 `index`  
 Obbligatorio.  Indice in base zero del carattere desiderato.  
  
## Note  
 Il metodo `charAt` restituisce un valore del carattere uguale al carattere in corrispondenza del parametro `index` specificato.  Il primo carattere di una stringa corrisponde all'indice 0, il secondo all'indice 1 e così via.  I valori di `index` non compresi nell'intervallo valido restituiscono una stringa vuota.  
  
## Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo del metodo `charAt`:  
  
```javascript  
var str = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";  
document.write(str.charAt(str.length - 1));  
  
// Output: Z  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Si applica a**: [Oggetto String](../../javascript/reference/string-object-javascript.md)  
  
## Vedere anche  
 [Oggetto String](../../javascript/reference/string-object-javascript.md)