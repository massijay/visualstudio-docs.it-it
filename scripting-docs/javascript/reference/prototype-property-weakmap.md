---
title: "Propriet&#224; prototype (WeakMap) | Microsoft Docs"
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
ms.assetid: d28b8a9b-38c9-443d-9586-7cc74784bd99
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Propriet&#224; prototype (WeakMap)
Restituisce un riferimento al prototipo per un oggetto `WeakMap`.  
  
## Sintassi  
  
```javascript  
weakmap.prototype  
```  
  
## Note  
 L'argomento `weakmap` è il nome di un oggetto `WeakMap`.  
  
 Utilizzare la proprietà `prototype` per fornire un gruppo di funzioni di base a una classe di oggetti.  Le nuove istanze di un oggetto "ereditano" il funzionamento del prototipo assegnato all'oggetto.  
  
 Per aggiungere, ad esempio, un metodo all'oggetto `WeakMap` che restituisce il valore dell'elemento più grande di `WeakMap`, dichiarare la funzione, aggiungerla a `WeakMap.prototype`, quindi utilizzarla.  
  
## Requisiti  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]