---
title: "Propriet&#224; prototype (Set) | Microsoft Docs"
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
ms.assetid: a075d5a6-e502-4636-85fc-1af001b8ac35
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Propriet&#224; prototype (Set)
Restituisce un riferimento al prototipo per un set.  
  
## Sintassi  
  
```javascript  
set.prototype  
```  
  
## Note  
 L'argomento `set` è il nome di un set.  
  
 Utilizzare la proprietà `prototype` per fornire un gruppo di funzioni di base a una classe di oggetti.  Le nuove istanze di un oggetto "ereditano" il funzionamento del prototipo assegnato all'oggetto.  
  
 Per aggiungere, ad esempio, un metodo all'oggetto `Set` che restituisce il valore dell'elemento più grande del set, dichiarare la funzione, aggiungerla a `Set.prototype`, quindi utilizzarla.  
  
## Requisiti  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]