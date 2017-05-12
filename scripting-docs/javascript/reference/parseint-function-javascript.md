---
title: "Funzione parseInt (JavaScript) | Microsoft Docs"
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
  - "parseInt"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "parseInt (metodo)"
ms.assetid: e86471af-2a0e-4359-83af-f1ac81e51421
caps.latest.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 24
---
# Funzione parseInt (JavaScript)
Converte una stringa in un intero.  
  
## Sintassi  
  
```  
parseInt(numString, [radix])   
```  
  
## Parametri  
 `numString`  
 Obbligatorio.  Stringa da convertire in un numero.  
  
 `radix`  
 Facoltativo.  Valore compreso tra 2 e 36 che specifica la base del numero in `numString`.  Se questo argomento non viene fornito, le stringhe con un prefisso '0x' sono considerate esadecimali.  Tutte le altre stringhe vengono considerate stringhe decimali.  
  
## Note  
 La funzione `parseInt` restituisce un valore intero uguale al numero contenuto in `numString`.  Se non è possibile convertire correttamente in un intero alcun prefisso di `numString`, verrà restituito il valore `NaN` \(Non numerico\).  
  
```javascript  
parseInt("abc");     // Returns NaN.  
parseInt("12abc");   // Returns 12.  
```  
  
 Per verificare la presenza del valore `NaN`, è possibile utilizzare la funzione `isNaN`.  
  
## Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Si applica a**: [Oggetto Global](../../javascript/reference/global-object-javascript.md)  
  
> [!NOTE]
>  A partire da [!INCLUDE[jsv9textspecific](../../javascript/reference/includes/jsv9textspecific-md.md)], la funzione `parseInt` non considera una stringa con prefisso '0' come ottale.  Quando non si utilizza la funzione `parseInt`, tuttavia, le stringhe con prefisso '0' possono ancora essere interpretate come ottali.  Vedere [Riepilogo dei tipi di dati](../../javascript/data-types-javascript.md) per informazioni sugli interi ottali.  
  
## Vedere anche  
 [Funzione isNaN](../../javascript/reference/isnan-function-javascript.md)   
 [Funzione parseFloat](../../javascript/reference/parsefloat-function-javascript.md)   
 [Oggetto String](../../javascript/reference/string-object-javascript.md)   
 [Metodo valueOf \(Object\)](../../javascript/reference/valueof-method-object-javascript.md)