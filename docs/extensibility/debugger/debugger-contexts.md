---
title: "Contesti di debugger | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "contesti [debug SDK], debug"
ms.assetid: 79808036-b680-4e4c-9c61-4ed43aa11323
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# Contesti di debugger
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

In [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] che esegue il debug, il motore di \(DE\) debug viene eseguito simultaneamente all'interno di diversi contesti diversi, come segue:  
  
-   Il contesto di codice, che specifica la posizione corrente in un flusso di esecuzione del programma.  
  
-   Il contesto o la posizione della documentazione, che descrivono la posizione corrente all'interno di un documento di origine.  
  
-   Il contesto di valutazione di un'espressione, che descrive il contesto in cui la valutazione delle espressioni di sviluppo.  
  
## Argomenti della sezione  
 [contesto di codice](../../extensibility/debugger/code-context.md)  
 Viene descritto il contesto di codice come indirizzo nel flusso di istruzioni di un programma in odierne architetture in fase di esecuzione con i linguaggi non tradizionali, in cui il codice non può essere rappresentato dalle istruzioni, ma alcuni altri metodi.  
  
 [Percorso del documento](../../extensibility/debugger/document-position.md)  
 Definisce la posizione del documento in debug di Visual Studio tramite un'api di una posizione in un file di origine come noto all'IDE.  
  
 [Contesto del documento](../../extensibility/debugger/document-context.md)  
 Vengono fornite informazioni sul contesto del documento rappresenta in debug di Visual Studio relativamente a un file di origine.  Inoltre descritto come il gestore dei simboli esegue il mapping di un contesto di codice al contesto della documentazione.  
  
 [Contesto di valutazione di espressioni](../../extensibility/debugger/expression-evaluation-context.md)  
 Fornisce informazioni su un contesto di valutazione di espressioni in Visual Studio.  Ad esempio, un contesto di valutazione di espressioni associato a uno stack frame fornisce contesto per esaminare le variabili locali, i parametri dei metodi e i membri della classe.  
  
## Sezioni correlate  
 [concetti di debug](../../extensibility/debugger/debugger-concepts.md)  
 Vengono descritti i concetti di architettura di debug principali.  
  
 [componenti di debug](../../extensibility/debugger/debugger-components.md)  
 Viene fornita una panoramica dei componenti di debug di Visual Studio, che includono il motore di \(DE\) debug, l'analizzatore di espressioni \(EE\) e il gestore dei \(SH\) simboli.  
  
 [Attività di debug](../../extensibility/debugger/debugging-tasks.md)  
 Vengono forniti collegamenti alle varie attività di debug, come avviare un programma e valutazione delle espressioni.