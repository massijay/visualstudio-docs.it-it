---
title: "Common Language Runtime e la valutazione di espressioni | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "debug [debug SDK], la valutazione di espressioni"
  - "valutazione dell'espressione e common language runtime"
ms.assetid: b36c1eb5-1aaf-48a6-b287-ee7a273d2b1c
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# Common Language Runtime e la valutazione di espressioni
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  In Visual Studio 2015, questa modalità di implementazione di analizzatori di espressioni è deprecata. Per informazioni sull'implementazione analizzatori di espressioni CLR, vedere [gli analizzatori di espressioni CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [esempio analizzatore di espressioni gestite](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 I compilatori, ad esempio Visual Basic e c\# \(pronunciato C sharp\), destinati a Common Language Runtime \(CLR\), produrre linguaggio MSIL \(Microsoft Intermediate\), che è successiva compilate in codice nativo. CLR fornisce un motore di debug \(DE\) per il debug del codice risulta. Se si prevede di integrare il linguaggio di programmazione proprietario nell'IDE di Visual Studio, è possibile scegliere di compilare in codice MSIL e pertanto non sarà necessario scrivere il proprio DE. Tuttavia, è necessario scrivere un analizzatore di espressioni \(EE\) che è in grado di valutazione di espressioni all'interno del contesto del linguaggio di programmazione.  
  
## Discussione  
 Le espressioni di linguaggio di computer in genere vengono analizzate per produrre un set di oggetti dati e un set di operatori utilizzati per modificarli. L'espressione "A \+ B" potrebbe essere analizzata per applicare l'operatore di addizione \(\+\) per i dati degli oggetti, ad esempio, "A" e "B", potrebbero verificarsi in un altro oggetto dati. Set totale di oggetti dati, operatori e le associazioni sono spesso rappresentate in un programma come una struttura ad albero, con gli operatori ai nodi dell'albero e gli oggetti dati nelle filiali. Un'espressione che è stato suddiviso in formato struttura ad albero viene spesso definita una struttura ad albero analizzato.  
  
 Una volta un'espressione è stata analizzata, un provider di simboli \(SP\) viene chiamato per valutare ogni oggetto dati. Se, ad esempio, "A" è definito sia in più di un metodo, quindi la domanda "Quale A?" è necessario rispondere prima che è possibile ottenere il valore dell'oggetto. La risposta restituita dalla stored procedure è simile a "Il terzo elemento sullo stack frame quinto" o "A 50 byte oltre l'inizio della memoria statica allocata a questo metodo".  
  
 Oltre a produrre codice MSIL per il programma stesso, i compilatori CLR possono inoltre generare informazioni di debug molto descrittive che viene scritto in un file di DataBase di programma \(PDB\). Fino a quando il compilatore di linguaggio proprietaria produce informazioni di debug nello stesso formato come i compilatori CLR, SP di CLR è in grado di identificare che del linguaggio denominato oggetti dati. Dopo aver individuato un oggetto dati denominato, l'analizzatore di Espressioni utilizza un oggetto di associazione per associare l'oggetto dati \(o associare\) nell'area di memoria che contiene il valore di tale oggetto. Il DE può quindi ottenere o impostare un nuovo valore per l'oggetto dati.  
  
 Un compilatore proprietario può fornire informazioni di debug mediante la chiamata di CLR il `ISymbolWriter` interfaccia \(definito in .NET Framework nello spazio dei nomi `System.Diagnostics.SymbolStore`\). Compilazione in MSIL e scrivendo le informazioni di debug tramite queste interfacce, è possibile utilizzare un compilatore proprietario di dice di CLR e i provider di servizi. Questo semplifica notevolmente l'integrazione di un linguaggio proprietario nell'IDE di Visual Studio.  
  
 Quando il DE CLR chiama l'analizzatore di Espressioni proprietarie per valutare un'espressione, il DE fornisce l'analizzatore di Espressioni con interfacce di un Service Pack e un oggetto di associazione. Di conseguenza, la scrittura di un mezzo di motore di debug basata su CLR è necessario solo implementare le interfacce dell'analizzatore di espressioni espressione appropriata. Common Language Runtime gestisce l'associazione e il simbolo per la gestione.  
  
## Vedere anche  
 [Scrittura di un analizzatore di espressioni CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)