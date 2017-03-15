---
title: "DA0010: Funzione GetHashCode dispendiosa | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.rules.DAExpensiveGetHashCode"
  - "vs.performance.DA0010"
  - "vs.performance.rules.DA0010"
  - "vs.performance.10"
ms.assetid: 3987e21a-5b4f-45e4-8a33-6b3f0a472c08
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# DA0010: Funzione GetHashCode dispendiosa
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|ID regola|DA0010|  
|Category|Utilizzo di .NET Framework|  
|Metodi di profilatura|Campionamento<br /><br /> Memoria .NET|  
|Messaggio|Le funzioni GetHashCode dovrebbero essere semplici e non allocare memoria.  Se possibile, ridurre la complessità della funzione di codice hash.|  
|Tipo messaggio|Avviso|  
  
## Causa  
 Le chiamate al metodo GetHashCode del tipo costituiscono una percentuale significativa dei dati di profilatura oppure il metodo alloca memoria.  
  
## Descrizione della regola  
 L'hashing è una tecnica per individuare rapidamente un determinato elemento in una grande raccolta.  Poiché le tabelle hash possono essere molto grandi e devono poter supportare frequenze di accesso molto elevate, le tabelle hash devono essere estremamente efficienti.  Un'implicazione di questo requisito è che i metodi GetHashCode in .NET Framework non devono allocare memoria.  L'allocazione di memoria aumenta il carico sul Garbage Collector e, se diventa necessario eseguire la procedura di Garbage Collection a seguito della richiesta di allocazione, espone il metodo a possibili ritardi.  
  
## Come correggere le violazioni  
 Ridurre la complessità del metodo.