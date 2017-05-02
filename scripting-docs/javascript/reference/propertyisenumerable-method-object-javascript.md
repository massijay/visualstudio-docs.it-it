---
title: "Metodo propertyIsEnumerable (Object) (JavaScript) | Microsoft Docs"
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
  - "propertyIsEnumerable"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "propertyIsEnumerable (proprietà)"
ms.assetid: d90c7c2e-ea23-4710-a957-9aefbbd1f68b
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Metodo propertyIsEnumerable (Object) (JavaScript)
Determina se una proprietà specificata è enumerabile.  
  
## Sintassi  
  
```  
  
object. propertyIsEnumerable(proName)  
```  
  
## Parametri  
 `object`  
 Obbligatorio.  Istanza di un oggetto.  
  
 `proName`  
 Obbligatorio.  Valore stringa del nome di una proprietà.  
  
## Note  
 Il metodo `propertyIsEnumerable` restituisce `true` se `proName` esiste in `object` e può essere enumerato utilizzando un ciclo `For`.  Il metodo `propertyIsEnumerable` restituisce `false` se a `object` non è associata una proprietà con il nome specificato oppure se la proprietà specificata non è enumerabile.  Le proprietà predefinite non sono in genere enumerabili ma quelle definite dall'utente sono sempre enumerabili.  
  
 Mediante il metodo `propertyIsEnumerable` non vengono considerati gli oggetti nella catena di prototipi.  
  
## Esempio  
  
```javascript  
var a = new Array("apple", "banana", "cactus");  
document.write(a.propertyIsEnumerable(1));  
  
// Output: true  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## Vedere anche  
 [Proprietà prototype \(Object\)](../../javascript/reference/prototype-property-object-javascript.md)