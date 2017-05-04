---
title: "Metodo endsWith Method (String) (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: c7d836e3-bc43-4d1b-be60-0a93beb8b7a2
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Metodo endsWith Method (String) (JavaScript)
Restituisce un valore che indica se una stringa o una sottostringa termina con un'altra stringa specificata.  
  
## Sintassi  
  
```vb  
  
stringObj.endsWith(str, [, position]);  
```  
  
#### Parametri  
 `stringObj`  
 Obbligatorio.  Oggetto string da cercare.  
  
 `str`  
 Obbligatorio.  Stringa di ricerca.  
  
 `position`  
 Facoltativo.  Posizione del primo carattere da cercare nell'oggetto string, partendo da 0.  
  
## Valore restituito  
 Se la stringa che parte da `position` inizia con la stringa di ricerca, il metodo `endsWith` restituisce `true`. In caso contrario, restituisce `false`.  
  
## Eccezioni  
 Se `str` è `RegExp`, viene generata un'eccezione `TypeError`.  
  
## Note  
  
## Requisiti  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]