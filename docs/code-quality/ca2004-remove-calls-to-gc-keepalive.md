---
title: "CA2004: Rimuovere le chiamate a GC.KeepAlive | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "RemoveCallsToGCKeepAlive"
  - "CA2004"
helpviewer_keywords: 
  - "RemoveCallsToGCKeepAlive"
  - "CA2004"
ms.assetid: bc543b5b-23eb-4b45-abc2-9325cd254ac2
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2004: Rimuovere le chiamate a GC.KeepAlive
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|RemoveCallsToGCKeepAlive|  
|CheckId|CA2004|  
|Categoria|Microsoft.Reliability|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 Le classi utilizzano `SafeHandle` ma contengono ancora chiamate a `GC.KeepAlive`.  
  
## Descrizione della regola  
 Se si effettua la conversione all'utilizzo di `SafeHandle`, rimuovere tutte le chiamate a `GC.KeepAlive` \(oggetto\).  In questo caso, non dovrebbe essere necessario per le classi chiamare `GC.KeepAlive`,  ``  presumendo che non dispongano di un finalizzatore ma si affidino a `SafeHandle` per completare l'handle del sistema operativo.  Anche se le conseguenze dell'uscita in una chiamata a `GC.KeepAlive` potrebbero essere trascurabili in termini di prestazioni, la percezione che una chiamata a `GC.KeepAlive` sia necessaria o sufficiente a risolvere un problema di durata che potrebbe non esistere più rende particolarmente difficile la gestione del codice.  
  
## Come correggere le violazioni  
 Rimuovere le chiamate a `GC.KeepAlive`.  
  
## Esclusione di avvisi  
 È possibile escludere questo avviso solo se non è tecnicamente corretto effettuare la conversione all'utilizzo di `SafeHandle` nella propria classe.