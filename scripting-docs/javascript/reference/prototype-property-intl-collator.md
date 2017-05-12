---
title: "Propriet&#224; prototype (Intl.Collator) | Microsoft Docs"
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
ms.assetid: c1bbb523-fb55-4395-b357-34d91cf5bba0
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Propriet&#224; prototype (Intl.Collator)
Restituisce un riferimento al prototipo per un'utilità di confronto.  
  
## Sintassi  
  
```javascript  
collator.prototype  
```  
  
## Note  
 L'argomento `collator` è il nome di un'utilità di confronto.  
  
 Utilizzare la proprietà `prototype` per fornire un gruppo di funzioni di base a una classe di oggetti.  Le nuove istanze di un oggetto "ereditano" il funzionamento del prototipo assegnato all'oggetto.  
  
 Per aggiungere, ad esempio, un metodo all'oggetto `Intl.Collator` che restituisce il valore dell'elemento più grande del set, dichiarare la funzione, aggiungerla a `Intl.Collator.prototype`, quindi utilizzarla.  
  
## Requisiti  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]