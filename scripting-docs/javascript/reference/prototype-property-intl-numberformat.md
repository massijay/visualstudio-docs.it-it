---
title: "Propriet&#224; prototype (Intl.NumberFormat) | Microsoft Docs"
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
ms.assetid: 7f6a7e26-108b-4b32-97c2-7f96b9252c50
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Propriet&#224; prototype (Intl.NumberFormat)
Restituisce un riferimento al prototipo per un formattatore.  
  
## Sintassi  
  
```javascript  
numberFormat.prototype  
```  
  
## Note  
 L'argomento `numberFormat` è il nome di un formattatore.  
  
 Utilizzare la proprietà `prototype` per fornire un gruppo di funzioni di base a una classe di oggetti.  Le nuove istanze di un oggetto "ereditano" il funzionamento del prototipo assegnato all'oggetto.  
  
 Per aggiungere, ad esempio, un metodo all'oggetto `Intl.NumberFormat` che restituisce il valore dell'elemento più grande del set, dichiarare la funzione, aggiungerla a `Intl.NumberFormat.prototype`, quindi utilizzarla.  
  
## Requisiti  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]