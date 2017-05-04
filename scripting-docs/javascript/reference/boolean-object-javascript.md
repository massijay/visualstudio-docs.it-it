---
title: "Oggetto Boolean (JavaScript) | Microsoft Docs"
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
  - "boolean_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Boolean (tipo di dati), Boolean (oggetto)"
  - "Boolean (oggetto)"
ms.assetid: d67748f2-7bf5-4889-8269-e777616cc5f0
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Oggetto Boolean (JavaScript)
Consente di creare un nuovo valore booleano.  
  
## Sintassi  
  
```  
  
boolObj = new Boolean([boolValue])  
```  
  
## Parametri  
 `boolObj`  
 Obbligatorio.  Nome della variabile a cui l'oggetto `Boolean` è assegnato.  
  
 `boolValue`  
 Facoltativo.  Valore booleano iniziale del nuovo oggetto.  Se `boolvalue` viene omesso oppure è `false`, 0, `null`, `NaN` o una stringa vuota, il valore iniziale dell'oggetto booleano è `false`.  In caso contrario, il valore iniziale è `true`.  
  
## Note  
 L'oggetto `Boolean` è un wrapper per il tipo di dati booleano.  [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] utilizza in modo implicito l'oggetto `Boolean` ogni volta che un tipo di dati booleano viene convertito in un oggetto `Boolean`.  
  
 Creare raramente un'istanza dell'oggetto `Boolean` in modo esplicito.  
  
## Proprietà  
 Nella tabella seguente sono elencate le proprietà dell'oggetto `Boolean`.  
  
|Proprietà|Descrizione|  
|---------------|-----------------|  
|[Proprietà constructor](../../javascript/reference/constructor-property-boolean.md)|Specifica la funzione che crea un valore booleano.|  
|[Proprietà prototype](../../javascript/reference/prototype-property-boolean.md)|Restituisce un riferimento al prototipo per un valore booleano.|  
  
<a name="js56jsobjarraymeth"></a>   
## Metodi  
 Nella tabella seguente sono elencati i metodi dell'oggetto `Boolean`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[Metodo toString](../../javascript/reference/tostring-method-boolean-1.md)|Restituisce una rappresentazione in forma di stringa di un valore booleano.|  
|[Metodo valueOf](../../javascript/reference/valueof-method-boolean.md)|Ottiene un riferimento al valore booleano.|  
  
## Requisiti  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]