---
title: "Nodi di programma | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "nodi di programma, il contesto di debug"
  - "debug [Debugging SDK], programmare nodi"
  - "nodi di programma, aggiunta"
  - "nodi di programma, sostituendo"
ms.assetid: 1c5a5c13-c14d-42c3-af11-4c63f1032c8d
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Nodi di programma
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

In termini di architettura del debugger, **un nodo di programma**:  
  
-   È una descrizione semplice di un programma.  
  
-   Può identificarsi e il processo che esegue in e può essere associato a, essere rimosso da e descrivere il motore di debug \(DE\) che lo ha creato, se presente.  
  
-   è rappresentato [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) da un'interfaccia, in genere creata da un DE o da una porta.  I nodi di programma vengono aggiunti a una porta chiamando [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md).  Quando un nodo di programma viene aggiunto a una porta, viene aggiunto al processo che contiene il programma in questo nodo del programma rappresenta.  
  
 Prima o quindi il termine di una sessione di debug viene avviata, a seconda dell'implementazione del pacchetto di debug, nodi di programma vengono utilizzati per creare programmi corrispondenti.  Quando un processo viene eseguita una query per i programmi, i programmi vengono enumerati, uno per ogni nodo del programma.  
  
 Prima che un programma sia associato a, l'ide necessita solo di una descrizione semplice programma.  Queste informazioni possono essere ottenute dal nodo del programma.  Il programma viene aggiunto una volta a, l'ide deve visualizzare informazioni più dettagliate, come un elenco di tutti i thread del programma.  Queste informazioni vengono ottenute dal programma stesso.  
  
## Vedere anche  
 [Programs](../../extensibility/debugger/programs.md)   
 [Processi](../../extensibility/debugger/processes.md)   
 [Il motore di debug](../../extensibility/debugger/debug-engine.md)   
 [Concetti del debugger](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)