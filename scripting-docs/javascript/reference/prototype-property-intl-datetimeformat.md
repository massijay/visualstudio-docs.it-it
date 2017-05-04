---
title: "Propriet&#224; prototype (Intl.DateTimeFormat) | Microsoft Docs"
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
ms.assetid: e1e693ff-1775-407e-b655-18a60d238ded
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Propriet&#224; prototype (Intl.DateTimeFormat)
Restituisce un riferimento al prototipo per un formattatore.  
  
## Sintassi  
  
```javascript  
dateTimeFormat.prototype  
```  
  
## Note  
 L'argomento `dateTimeFormat` è il nome di un formattatore.  
  
 Utilizzare la proprietà `prototype` per fornire un gruppo di funzioni di base a una classe di oggetti.  Le nuove istanze di un oggetto "ereditano" il funzionamento del prototipo assegnato all'oggetto.  
  
 Per aggiungere, ad esempio, un metodo all'oggetto `Intl.DateTimeFormat` che restituisce il valore dell'elemento più grande del set, dichiarare la funzione, aggiungerla a `Intl.DateTimeFormat.prototype`, quindi utilizzarla.  
  
## Requisiti  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]