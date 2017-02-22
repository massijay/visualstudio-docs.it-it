---
title: "Controllo del programma | Microsoft Docs"
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
  - "debug [debug SDK], controllo di esecuzione"
ms.assetid: 6be80904-e66c-4cae-8891-1113b799fb01
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# Controllo del programma
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Nel debug di Visual Studio, tutte esecuzione di istruzioni e routine continue seguenti si verificano a livello del programma:  
  
-   Impostare l'istruzione successiva, ovvero, impostando il computer dell'istruzione seguente essere eseguito in un ambiente specifico del frame  
  
-   Eseguire, ovvero, angolo per uscire dalla modalità di esecuzione di istruzioni  
  
-   Esecuzione di istruzioni all'istruzione seguente  
  
-   Continuando con la modalità di debug passo a passo corrente  
  
-   Lo shelving thread contenuto dal programma  
  
-   Riattivando i thread contenuto dal programma  
  
> [!NOTE]
>  Visualizzando lo stack di chiamate viene distribuito a livello di thread.  Per enumerare le informazioni del frame quando si visualizzano lo stack di chiamate per un thread, è necessario implementare tutti i metodi di interfaccia di [IEnumDebugFrameInfo2](../../extensibility/debugger/reference/ienumdebugframeinfo2.md) .  
  
## Metodi di controllo del programma  
 Nella tabella seguente sono elencati i metodi di [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) che devono essere implementati per un controllo come minimo funzionale \(DE\) di esecuzione e del motore di debug.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDebugProgram2:: di esecuzione](../../extensibility/debugger/reference/idebugprogram2-execute.md)|Esegue tutti i thread inclusi in un programma da uno stato interrotto.  obbligatorio per il controllo di esecuzione.|  
|[IDebugProgram2:: continuare](../../extensibility/debugger/reference/idebugprogram2-continue.md)|Esegue tutti i thread inclusi in un programma da uno stato interrotto.  obbligatorio per il controllo di esecuzione.|  
|[IDebugProgram2:: passaggio](../../extensibility/debugger/reference/idebugprogram2-step.md)|Esegue un'operazione sul thread specificato.  Esegue tutti gli altri thread contenuto dal programma.  obbligatorio per il controllo di esecuzione.|  
  
 Per i programmi multithreading, è inoltre necessario implementare il metodo di [IDebugProgram2:: EnumThreads](../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) e tutti i metodi di interfaccia di [IEnumDebugThreads2](../../extensibility/debugger/reference/ienumdebugthreads2.md) .  
  
## Vedere anche  
 [Controllo dell'esecuzione e la valutazione dello stato](../../extensibility/debugger/execution-control-and-state-evaluation.md)