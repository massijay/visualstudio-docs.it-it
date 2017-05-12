---
title: "Interfaccia IDebugApplicationThreadEvents110 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "Interfaccia IDebugApplicationThreadEvents110"
ms.assetid: 91a98b0e-7c81-4118-af75-82f75fd4f25a
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Interfaccia IDebugApplicationThreadEvents110
Aggiunge più eventi dei thread.  Questi eventi sono solo locali.  È possibile sottoscrivere relativi solo nel processo sottoposto a debug, [IConnectionPoint](http://go.microsoft.com/fwlink/?LinkId=232738) utilizzando consigliare i metodi di unadvise l'applicazione di PDM thread gli oggetti \(che implementano [Interfaccia IDebugApplicationThread](../../winscript/reference/idebugapplicationthread-interface.md)\).  Si verificano sul thread che provengono da.  
  
> [!IMPORTANT]
>  L'interfaccia viene implementata da PDM v11.0 e maggiore.  Trovato in activdbg100.h.  
  
## Metodi  
 L'interfaccia `IDebugActivationThreadEvents110` espone i metodi riportati di seguito.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDebugApplicationThreadEvents110 ::OnBeginThreadRequest](../../winscript/reference/idebugapplicationthreadevents110-onbeginthreadrequest.md)|Una chiamata nel thread utilizzando la commutazione di thread PDM ha avviato.|  
|[IDebugApplicationThreadEvents110::OnResumeFromBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onresumefrombreakpoint.md)|Il thread sta riattivando da un punto di interruzione e sarà attivo nuovamente.|  
|[IDebugApplicationThreadEvents110::OnSuspendForBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onsuspendforbreakpoint.md)|Il thread è sospendendo per un punto di interruzione e gestire le chiamate che richiedono il thread completo di essere sospeso.|  
|[IDebugApplicationThreadEvents110::OnThreadRequestComplete](../../winscript/reference/idebugapplicationthreadevents110-onthreadrequestcomplete.md)|Una chiamata nel thread utilizzando la commutazione di thread PDM ha completato.|