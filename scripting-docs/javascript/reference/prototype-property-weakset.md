---
title: "Propriet&#224; prototype (WeakSet) | Microsoft Docs"
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
ms.assetid: 950e15a2-2f56-4cb9-8e48-020efd97f938
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Propriet&#224; prototype (WeakSet)
Restituisce un riferimento al prototipo per un oggetto `WeakSet`.  
  
## Sintassi  
  
```javascript  
weakset.prototype  
```  
  
## Note  
 L'argomento `weakset` è il nome di un set.  
  
 Usare la proprietà `prototype` per fornire un set di funzionalità di base a una classe di oggetti.  Le nuove istanze di un oggetto "ereditano" il comportamento del prototipo assegnato all'oggetto.  
  
 Ad esempio, per aggiungere un metodo all'oggetto `WeakSet` che restituisce il valore dell'elemento più grande del set, dichiarare la funzione, aggiungerla a `WeakSet.prototype` e quindi usarla.  
  
## Requisiti  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]