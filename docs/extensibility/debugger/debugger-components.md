---
title: "Componenti del debugger | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "debug [Visual Studio], componenti"
  - "componenti di debug [Visual Studio SDK]"
  - "debug [debug SDK], componenti"
ms.assetid: 8b8ab77f-a134-495c-be42-3bc51aa62dfb
caps.latest.revision: 30
caps.handback.revision: 30
ms.author: "gregvanl"
manager: "ghogen"
---
# Componenti del debugger
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Il debugger di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] viene implementato come VSPackage e gestisce l'intera sessione di debug.  La sessione di debug include i seguenti elementi:  
  
-   **pacchetto di Debug:** Il debugger di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fornisce la stessa interfaccia utente qualsiasi cosa sta eseguendo il debug.  
  
-   **Amministratore \(SDM\) di debug della sessione:** Fornisce un'interfaccia di programmazione coerente al debugger di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] per la gestione dei vari motori di debug.  Viene implementata da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
-   **Amministratore \(PDM\) del processo di debug:** Gestisce, per tutte le istanze in esecuzione di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], un elenco di tutti i programmi che possono essere o che il debug.  Viene implementata da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
-   **motore di debug \(DE\):** È responsabile di monitorare un programma sottoposto a debug, specificando lo stato del programma in esecuzione a SDM e al PDM e interazione con l'analizzatore di espressioni e il provider dei simboli per fornire un'analisi in tempo reale dello stato della memoria e variabili di un programma.  Viene implementata da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] \(per i linguaggi che supporta\) e da fornitori di terze parti che desiderano supportare il proprio runtime.  
  
-   **analizzatore di espressioni \(EE\):** Fornisce il supporto per le variabili e le espressioni in modo dinamico di valutazione fornite dall'utente quando un programma è stato interrotto a un punto specifico.  Viene implementata da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] \(per i linguaggi che supporta\) e da fornitori di terze parti che desiderano supportare i propri linguaggi.  
  
-   **Provider \(SP\) del simbolo:** Anche detta gestore dei simboli, i simboli di debug di un programma a un'istanza in esecuzione del programma in modo che possa fornire informazioni significative ad esempio di debug e di valutazione livelli dell'origine dell'espressione\).  Viene implementata da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] \(per i simboli di Common Language Runtime CLR \[\] e il formato di file di simboli del database di programma \(PDB\)\] e fornitori di terze parti che dispongono di un proprio metodo privato di archiviare le informazioni di debug.  
  
 Nel diagramma seguente viene illustrata la relazione tra questi elementi del debugger di Visual Studio.  
  
 ![Panoramica dei componenti del debug](../../extensibility/debugger/media/dbugcompovrview.png "DBugCompOvrview")  
  
## Argomenti della sezione  
 [Eseguire il debug del pacchetto](../../extensibility/debugger/debug-package.md)  
 Viene descritto il pacchetto di debug, che viene eseguita in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sgusciano e gestire un'interfaccia utente.  
  
 [Gestione di Debug di processi](../../extensibility/debugger/process-debug-manager.md)  
 Vengono forniti cenni preliminari sulle funzionalità di PDM, ovvero gestione dei processi che è possibile eseguire il debug.  
  
 [Gestione sessione di Debug](../../extensibility/debugger/session-debug-manager.md)  
 Definisce lo SDM, che fornisce una visualizzazione unificata della sessione di debug all'IDE.  Lo SDM gestisce il DE.  
  
 [Il motore di debug](../../extensibility/debugger/debug-engine.md)  
 Vengono illustrati i servizi di debug che il DE v5.0.  
  
 [Modalità operative](../../extensibility/debugger/operational-modes.md)  
 Viene fornita una panoramica delle tre modalità in cui l'ide possa funzionare: modalità progettazione, modalità di esecuzione e modalità di interruzione.  I meccanismi di transizione vengono illustrati.  
  
 [Analizzatore di espressioni](../../extensibility/debugger/expression-evaluator.md)  
 Viene illustrato lo scopo dell'EE in fase di esecuzione.  
  
 [Provider di simboli](../../extensibility/debugger/symbol-provider.md)  
 Viene illustrato come, all'implementazione, il provider del simbolo di valuta le variabili ed espressioni.  
  
 [Tipo visualizzatore e Visualizzatore personalizzato](../../extensibility/debugger/type-visualizer-and-custom-viewer.md)  
 Viene spiegato cosa un visualizzatore di tipo e un visualizzatore personalizzate sono e il ruolo l'analizzatore di espressioni fornisce il supporto di entrambi.  
  
## Sezioni correlate  
 [Concetti del debugger](../../extensibility/debugger/debugger-concepts.md)  
 Vengono descritti i concetti di architettura di debug principali.  
  
 [Contesti di debugger](../../extensibility/debugger/debugger-contexts.md)  
 Viene illustrato come il DE lavora contemporaneamente all'interno del codice, la documentazione e i contesti di valutazione di espressioni.  Viene descritto, per ciascuno dei tre contesti, la posizione, al percorso, o di valutazione relativa a.  
  
 [Attività di debug](../../extensibility/debugger/debugging-tasks.md)  
 Vengono forniti collegamenti alle varie attività di debug, come avviare un programma e valutazione delle espressioni.  
  
## Vedere anche  
 [Introduzione](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)