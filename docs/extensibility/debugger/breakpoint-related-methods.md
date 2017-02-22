---
title: "Metodi correlati al punto di interruzione | Microsoft Docs"
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
  - "debug dei metodi di punto di interruzione [debug SDK]"
  - "punti di interruzione, metodi"
ms.assetid: a6f77bf0-bf81-443f-8683-5f12075bbe10
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# Metodi correlati al punto di interruzione
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Il modulo \(DE\) di debug deve supportare l'impostazione dei punti di interruzione.  il debug di Visual Studio supporta i seguenti tipi di punti di interruzione:  
  
-   Modalità associata  
  
     Obbligatorio con l'interfaccia utente e correttamente associato a una posizione specificata di codice  
  
-   in corso  
  
     Obbligatorio con l'interfaccia utente ma non ancora associato alle effettive istruzioni  
  
## Descrizione  
 Ad esempio, di un punto di interruzione in attesa si verifica quando le istruzioni non sono ancora caricate.  Quando il codice viene caricato, in attesa dei punti di interruzione provare a eseguire l'associazione al codice nella posizione prescritta, ovvero, alle istruzioni break inserire nel codice.  Gli eventi vengono inviati al gestore di debug della sessione \(SDM\) per indicare l'esito positivo dell'associazione o per informare che si siano verificati errori obbligatori.  
  
 Di un punto di interruzione in attesa gestisce inoltre il proprio elenco interno dei punti di interruzione associati corrispondenti.  Uno in attesa del punto di interruzione può causare l'inserimento di molti punti di interruzione nel codice.  L'interfaccia utente di debug di Visual Studio mostrata una visualizzazione struttura ad albero dei punti di interruzione corrente e dei relativi punti di interruzione associati corrispondenti.  
  
 La creazione e l'utilizzo dei punti di interruzione in corso richiedono l'implementazione del metodo di [IDebugEngine2:: CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) nonché dei seguenti metodi delle interfacce di [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) .  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|Determina se specificato in attesa del punto di interruzione può essere associato a un percorso di codice.|  
|[Bind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|Associa specificato in attesa del punto di interruzione a uno o più percorsi di codice.|  
|[GetState](../Topic/IDebugPendingBreakpoint2::GetState.md)|Ottiene lo stato di un punto di interruzione in attesa.|  
|[GetBreakpointRequest](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|Ottiene la richiesta del punto di interruzione utilizzata per creare un punto di interruzione in attesa.|  
|[Abilita](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|Alternare lo stato attivato di un punto di interruzione in attesa.|  
|[EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|Enumera i punti di interruzione limitano da un punto di interruzione in attesa.|  
|[EnumErrorBreakpoints](../Topic/IDebugPendingBreakpoint2::EnumErrorBreakpoints.md)|Enumera i punti di interruzione di errori risultanti da un punto di interruzione in attesa.|  
|[Delete](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|Eliminazione di un punto di interruzione in attesa e tutti i punti di interruzione limitano da.|  
  
 Per enumerare i punti di interruzione associati e i punti di interruzione di errori, è necessario implementare tutti i metodi di [IEnumDebugBoundBreakpoints2](../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md) e di [IEnumDebugErrorBreakpoints2](../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md).  
  
 In attesa dei punti di interruzione che associano a un percorso di codice richiedono l'implementazione dei metodi di [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) .  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetPendingBreakpoint](../Topic/IDebugBoundBreakpoint2::GetPendingBreakpoint.md)|Ottiene il punto di interruzione in attesa che contiene un punto di interruzione.|  
|[GetState](../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)|Ottiene lo stato di un punto di interruzione associato.|  
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)|Ottiene la risoluzione del punto di interruzione che descrive un punto di interruzione.|  
|[Abilita](../../extensibility/debugger/reference/idebugboundbreakpoint2-enable.md)|abilita o disabilita un punto di interruzione.|  
|[Delete](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)|Elimina un punto di interruzione associato.|  
  
 Le informazioni di richiesta e di risoluzione richiedono l'implementazione dei metodi di [IDebugBreakpointResolution2](../../extensibility/debugger/reference/idebugbreakpointresolution2.md) .  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetBreakpointType](../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)|Ottiene il tipo del punto di interruzione rappresentato da una risoluzione.|  
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)|Ottiene le informazioni di risoluzione del punto di interruzione che descrivono un punto di interruzione.|  
  
 La risoluzione degli errori che possono verificarsi durante l'associazione richiede l'implementazione dei metodi di [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) .  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)|Ottiene il punto di interruzione in attesa che contiene un punto di interruzione di errori.|  
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md)|Ottiene la risoluzione degli errori del punto di interruzione che descrive un punto di interruzione di errori.|  
  
 La risoluzione degli errori che possono verificarsi durante l'associazione anche richiede i seguenti metodi di [IDebugErrorBreakpointResolution2](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md).  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetBreakpointType](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md)|ottiene il tipo di punto di interruzione.|  
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)|ottiene le informazioni di risoluzione di un punto di interruzione.|  
  
 Per visualizzare il codice sorgente in un punto di interruzione è necessario implementare i metodi di [IDebugStackFrame2:: GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) e\/o metodi di [IDebugStackFrame2:: GetCodeContext](../Topic/IDebugStackFrame2::GetCodeContext.md).  
  
## Vedere anche  
 [Controllo dell'esecuzione e la valutazione dello stato](../../extensibility/debugger/execution-control-and-state-evaluation.md)