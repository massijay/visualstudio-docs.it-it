---
title: "Concetti del debugger | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "debug [Debugging SDK]"
ms.assetid: 2d371d38-f1a0-4a9a-8ea3-100e8c0149b7
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# Concetti del debugger
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Per compilare il pacchetto Visual Studio debug, è necessario avere familiarità con i concetti di architettura utilizzati nella progettazione del pacchetto.  
  
## Argomenti della sezione  
 [Sessione di debug](../../extensibility/debugger/debug-session.md)  
 Viene illustrato il ruolo di una sessione nell'architettura di debug.  
  
 [Server](../../extensibility/debugger/servers-visual-studio-sdk.md)  
 Viene definito il concetto un server è in termini di eseguire il debug l'architettura, sia nel sunto che in termini fisici.  
  
 [Fornitori di porte](../../extensibility/debugger/port-suppliers.md)  
 Definisce l'operazione che un fornitore di porte è in termini di eseguire il debug dell'architettura.  
  
 [Porte](../../extensibility/debugger/ports.md)  
 Viene definito il concetto di porta è in termini di eseguire il debug dell'architettura.  
  
 [Processi](../../extensibility/debugger/processes.md)  
 Definisce l'operazione che un processo è in termini di eseguire il debug dell'architettura.  
  
 [Nodi di programma](../../extensibility/debugger/program-nodes.md)  
 Definisce un nodo di programma in termini di architettura di debug, inclusione come possibile identificarsi e processo che esegue in.  
  
 [Programs](../../extensibility/debugger/programs.md)  
 Definisce un programma in termini di eseguire il debug dell'architettura.  
  
 [Thread](../../extensibility/debugger/threads.md)  
 Definisce le caratteristiche dei thread in termini di architettura di debug.  
  
 [Stack frame](../../extensibility/debugger/stack-frames.md)  
 definisce uno stack frame in termini di architettura di debug.  uno stack frame è un'astrazione di uno stack che fornisce il contesto di esecuzione di un thread.  
  
 [Moduli](../../extensibility/debugger/modules.md)  
 Definisce un modulo, in termini di architettura di debug, come contenitore fisico del codice, ad esempio un file eseguibile o una DLL.  
  
 [Punti di interruzione](../../extensibility/debugger/breakpoints-visual-studio-sdk.md)  
 Definisce i tre tipi di punto di interruzione\-in corso, di soglia e errore\-nei termini dell'architettura di debug.  
  
## Sezioni correlate  
 [Contesti di debugger](../../extensibility/debugger/debugger-contexts.md)  
 Viene illustrato come il motore \(DE\) di debug viene eseguito simultaneamente all'interno del codice, la documentazione e i contesti di valutazione di espressioni.  Viene descritto, per ciascuno dei tre contesti, la posizione, al percorso, o di valutazione relativa a.  
  
 [Componenti del debugger](../../extensibility/debugger/debugger-components.md)  
 Viene fornita una panoramica dei componenti di debug di Visual Studio, che includono il motore di \(DE\) debug, l'analizzatore di espressioni \(EE\) e il gestore dei \(SH\) simboli.  
  
 [Attività di debug](../../extensibility/debugger/debugging-tasks.md)  
 Vengono forniti collegamenti alle varie attività di debug, come avviare un programma e valutazione delle espressioni.