---
title: "Oggetto Set (JavaScript) | Microsoft Docs"
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
  - "Set"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 4a4dd749-2a76-44fb-9cb0-a3ef317f75fb
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Oggetto Set (JavaScript)
Raccolta di valori univoci che possono essere di qualsiasi tipo.  
  
## Sintassi  
  
```  
setObj = new Set()  
  
```  
  
## Note  
 Se si prova ad aggiunge un valore non univoco a `Set`, il nuovo valore non verrà aggiunto alla raccolta.  
  
## Proprietà  
 Nella tabella seguente sono elencate le proprietà dell'oggetto `Set`.  
  
|Proprietà|Descrizione|  
|---------------|-----------------|  
|[Costruttore](../../javascript/reference/constructor-property-set.md)|Specifica la funzione che crea un set.|  
|[prototipo](../../javascript/reference/prototype-property-set.md)|Restituisce un riferimento al prototipo per un set.|  
|[size](../../javascript/reference/size-property-set-javascript.md)|Restituisce il numero di elementi in un set.|  
  
## Metodi  
 Nella tabella seguente sono elencati i metodi dell'oggetto `Set`:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[aggiunta](../../javascript/reference/add-method-set-javascript.md)|Aggiunge un elemento a un set.|  
|[clear](../../javascript/reference/clear-method-set-javascript.md)|Rimuove tutti gli elementi da un set.|  
|[elimina](../../javascript/reference/delete-method-set-javascript.md)|Rimuove un elemento specificato da un set.|  
|[forEach](../../javascript/reference/foreach-method-set-javascript.md)|Esegue l'azione specificata per ciascun elemento in un set.|  
|[has](../../javascript/reference/has-method-set-javascript.md)|Restituisce `true` se il set contiene un elemento specificato.|  
|[toString](../../javascript/reference/tostring-method-set-javascript.md)|Restituisce una rappresentazione di stringa di un set.|  
|[valueOf](../../javascript/reference/valueof-method-set-javascript.md)|Restituisce il valore primitivo dell'oggetto specificato.|  
  
## Esempio  
 Nell'esempio seguente viene illustrato come aggiungere dei membri a un oggetto Set e quindi recuperarli.  
  
```javascript  
var s = new Set();  
s.add("Thomas Jefferson");  
s.add(1776);  
s.add("founding father");  
  
s.forEach(function (item) {  
    document.write(item.toString() + ", ");  
});  
  
// Output:  
// Thomas Jefferson, 1776, founding father,  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]