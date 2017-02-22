---
title: "Errori di punto di interruzione | Microsoft Docs"
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
  - "punti di interruzione, errori"
  - "debug degli errori del punto di interruzione [debug SDK]"
  - "errori [Debugging SDK]"
ms.assetid: 79221c6b-a924-4c8e-a778-e312e4e0c0c8
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# Errori di punto di interruzione
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

L'esempio seguente viene illustrato il processo quando un punto di interruzione tenta di eseguire l'associazione al codice ma a non riuscita:  
  
## Risoluzione dei problemi di un errore del punto di interruzione  
  
1.  Il motore \(DE\) di debug invia [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) gestione \(SDM\) di debug della sessione.  
  
2.  Lo SDM chiama [IDebugBreakpointErrorEvent2:: GetErrorBreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md) \(IDebugErrorBreakpoint2 \*\* `ppErrorBP`\) per ottenere il punto di interruzione di errori.  
  
3.  Lo SDM chiama [IDebugErrorBreakpoint2:: GetPendingBreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md) per ottenere il punto di interruzione in attesa in cui il punto di interruzione di errori proviene.  
  
4.  Lo SDM chiama [IDebugErrorBreakpoint2:: GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) per ottenere la ragione per cui il punto di interruzione di errori non riuscire l'associazione.  
  
## Vedere anche  
 [Eventi di chiamata del Debugger](../../extensibility/debugger/calling-debugger-events.md)