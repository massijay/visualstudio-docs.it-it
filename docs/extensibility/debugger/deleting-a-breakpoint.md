---
title: "Eliminazione di un punto di interruzione | Microsoft Docs"
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
  - "punti di interruzione, l'eliminazione"
  - "debug [Debugging SDK], l'eliminazione dei punti di interruzione"
ms.assetid: 75a046cc-d20a-4c79-ad2d-1f18426ac5d0
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# Eliminazione di un punto di interruzione
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

L'esempio seguente viene illustrato il processo quando si eliminano di un punto di interruzione in sospeso:  
  
## processo di eliminazione  
 L'amministratore \(SDM\) di debug della sessione chiama il metodo di [IDebugPendingBreakpoint2:: Eliminazione](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md) per la rimozione del punto di interruzione in attesa e tutti i punti di interruzione associati limitano da.  
  
> [!NOTE]
>  Un singolo punto di interruzione associato anche possibile eliminare da una chiamata a [IDebugBoundBreakpoint2:: Eliminazione](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md).  
  
## Vedere anche  
 [Eventi di chiamata del Debugger](../../extensibility/debugger/calling-debugger-events.md)