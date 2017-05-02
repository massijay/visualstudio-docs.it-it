---
title: "Metodo valueOf (Object) (JavaScript) | Microsoft Docs"
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
  - "valueOf"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "valueOf (metodo)"
ms.assetid: c555e38b-f451-4341-8fcd-4c8b02906a2c
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Metodo valueOf (Object) (JavaScript)
Restituisce il valore primitivo dell'oggetto specificato.  
  
## Sintassi  
  
```  
  
object.valueOf( )  
```  
  
## Note  
 Il riferimento `object` obbligatorio è un oggetto [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] intrinseco.  
  
 Il metodo `valueOf` è definito in modo diverso per ciascun oggetto [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] intrinseco.  
  
|Oggetto|Valore restituito|  
|-------------|-----------------------|  
|Array|Restituisce l'istanza della matrice.|  
|Boolean|Valore Boolean.|  
|Date|Il valore memorizzato dell'ora espresso in millisecondi a partire dalla mezzanotte dell'1 gennaio 1970 in formato UTC.|  
|Funzione|Funzione stessa.|  
|Number|Valore numerico.|  
|Oggetto|Oggetto stesso.  È l'impostazione predefinita.|  
|Stringa|Valore stringa.|  
  
 Il metodo `valueOf` non è disponibile per gli oggetti **Math** ed `Error`.  
  
## Requisiti  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
 **Si applica a**: [Oggetto Array](../../javascript/reference/array-object-javascript.md)&#124; [Oggetto Boolean](../../javascript/reference/boolean-object-javascript.md)&#124; [Oggetto Date](../../javascript/reference/date-object-javascript.md)&#124; [Oggetto Function](../../javascript/reference/function-object-javascript.md)&#124; [Oggetto Number](../../javascript/reference/number-object-javascript.md)&#124; [Oggetto Object](../../javascript/reference/object-object-javascript.md)&#124; [Oggetto String](../../javascript/reference/string-object-javascript.md)  
  
## Vedere anche  
 [Metodo toString \(Object\)](../../javascript/reference/tostring-method-object-javascript.md)