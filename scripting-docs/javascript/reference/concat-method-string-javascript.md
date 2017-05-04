---
title: "Metodo concat (String) (JavaScript) | Microsoft Docs"
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
  - "concat"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "concat (metodo) (String)"
  - "Concat (metodo)"
ms.assetid: 5d28ebb2-d534-4179-9297-a4c821ee9f24
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# Metodo concat (String) (JavaScript)
Restituisce una stringa contenente la concatenazione di due o più stringhe.  
  
## Sintassi  
  
```  
  
string1. concat([string2[, string3[, . . . [, stringN]]]])  
```  
  
## Parametri  
 `string1`  
 Obbligatorio.  Oggetto `String` o valore letterale stringa a cui vengono concatenate tutte le altre stringhe specificate.  
  
 `string2,. . ., stringN`  
 Facoltativo.  Stringa da accodare alla fine di `string1`.  
  
## Note  
 Il risultato del metodo `concat` equivale a: `result` \= `string1` \+ `string2` \+ `string3` \+ `stringN`.  Qualsiasi modifica apportata al valore in una stringa di origine o di risultato non influisce sul valore dell'altra stringa.  Se uno o più argomenti qualsiasi non sono stringhe, verranno convertiti in stringhe prima di essere concatenati a `string1`.  
  
## Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo del metodo `concat` con una stringa:  
  
```javascript  
var str1 = "ABCD"  
var str2 = "EFGH";  
var str3 = "1234";  
var str4 = "5678";  
document.write(str1.concat(str2, str3, str4));  
  
// Output: "ABCDEFGH12345678"  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Si applica a**: [Oggetto String](../../javascript/reference/string-object-javascript.md)  
  
## Vedere anche  
 [Operatore addizione \(\+\)](../../javascript/reference/addition-operator-decrement-javascript.md)