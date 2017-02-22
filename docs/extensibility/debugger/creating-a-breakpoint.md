---
title: "Creazione di un punto di interruzione | Microsoft Docs"
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
  - "punti di interruzione, creazione"
  - "debug [Debugging SDK], creazione di punti di interruzione"
ms.assetid: 6f9f87bb-192e-45e0-9a7a-ffe729e87f7d
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# Creazione di un punto di interruzione
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

L'esempio seguente viene illustrato il processo di creazione di un punto di interruzione.  
  
## Metodi nella creazione del punto di interruzione  
 Quando il modulo che è necessario associare un punto di interruzione viene caricato, l'amministratore \(SDM\) di debug della sessione vengono chiamati i metodi seguenti:  
  
1.  [IDebugPendingBreakpoint2:: Attivare](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)  
  
2.  [IDebugPendingBreakpoint2:: virtualizzare](../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md)  
  
3.  [IDebugPendingBreakpoint2:: CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)  
  
    > [!NOTE]
    >  **CanBind** viene chiamato solo quando un utente esegue un punto di interruzione dalla finestra punti di interruzione.  
  
4.  [IDebugPendingBreakpoint2:: associazione](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)  
  
5.  [IDebugPendingBreakpoint2:: EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)  
  
## Vedere anche  
 [Eventi di chiamata del Debugger](../../extensibility/debugger/calling-debugger-events.md)