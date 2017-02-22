---
title: "Raggiungere un punto di interruzione | Microsoft Docs"
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
  - "debug [Debugging SDK], raggiungere punti di interruzione"
  - "punti di interruzione, premere"
ms.assetid: a77816e3-b15b-46a0-90cd-be7242e4d6c9
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# Raggiungere un punto di interruzione
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

L'esempio seguente viene illustrato il processo quando il motore di debug \(DE\) viene rilevato un punto di interruzione mentre è in esecuzione o di istruzioni:  
  
## Risoluzione dei problemi relativi al punto di interruzione di riga eseguita  
  
1.  Il DE invia un'interfaccia di [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) come **EVENT\_SYNCHRONIZATION\_STOP**.  
  
2.  L'amministratore \(SDM\) di debug della sessione chiama [IDebugBreakpointEvent2::: EnumBreakpoints](../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) per ottenere il punto di interruzione che è stato premuto.  
  
## Vedere anche  
 [Eventi di chiamata del Debugger](../../extensibility/debugger/calling-debugger-events.md)