---
title: "Associazione dei punti di interruzione | Microsoft Docs"
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
  - "punti di interruzione, l'associazione"
ms.assetid: 70737387-c52f-4dae-8865-77d4b203bf25
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# Associazione dei punti di interruzione
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Se che un utente ha impostato un punto di interruzione, forse premere F9, l'ide formula la richiesta e inserisce la sessione di debug per creare il punto di interruzione.  
  
## impostare un punto di interruzione  
 Impostare un punto di interruzione è un processo in due fasi, perché il codice o i dati interessati dal punto di interruzione non può essere disponibili.  Innanzitutto, il punto di interruzione deve essere descritto quindi, mentre il codice o i dati diventino disponibili, deve essere associato a tali codice o dati, come segue:  
  
1.  Il punto di interruzione è richiesto dai motori di debug rilevanti \(DEs\) e quindi il punto di interruzione verrà associato al codice o ai dati mentre diventa disponibile.  
  
2.  La richiesta del punto di interruzione viene inviata la sessione di debug, che lo invia a qualsiasi DES rilevante.  Qualsiasi DE che sceglie per gestire il punto di interruzione viene creato un corrispondente in attesa del punto di interruzione.  
  
3.  La sessione di debug raccoglie i punti di interruzione in attesa e li invia di nuovo al pacchetto di debug \(il componente di debug di Visual Studio\).  
  
4.  Il pacchetto di debug richiesto la sessione di debug per associare il punto di interruzione in sospeso al codice o ai dati.  La sessione di debug invia la richiesta a qualsiasi DES rilevante.  
  
5.  Se il DE possibile associare il punto di interruzione, invia un evento associato il punto di interruzione della sessione di debug.  In caso contrario, invia un evento di errore del punto di interruzione invece.  
  
## In attesa dei punti di interruzione  
 Di un punto di interruzione in attesa può essere associato a più percorsi di codice.  Ad esempio, una riga di codice sorgente per il modello c\+\+ possibile associare a ogni sequenza di codice generata dal modello.  La sessione di debug possibile utilizzare un evento associato il punto di interruzione per enumerare i contesti di codice limita a un punto di interruzione quando l'evento è stato inviato.  Più contesti di codice possono essere associati più avanti, in modo da DE possibile inviare gli eventi associati del punto di interruzione in per ogni richiesta di associazione.  Tuttavia, un DE deve inviare solo un evento di errore del punto di interruzione per richiesta di associazione.  
  
## Implementazione  
 A livello di codice, il pacchetto di debug chiama il gestore di debug della sessione \(SDM\) e gli fornisce [IDebugBreakpointRequest2](../../extensibility/debugger/reference/idebugbreakpointrequest2.md) un'interfaccia che esegue il wrapping [BP\_REQUEST\_INFO](../../extensibility/debugger/reference/bp-request-info.md) di una struttura, che descrive il punto di interruzione da impostare.  Sebbene i punti di interruzione possono essere di molti form, infine risolvono a un codice o a un contesto dati.  
  
 Lo SDM passa questa chiamata a ogni DE rilevante chiamando il [CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) metodo.  Se il DE sceglie di gestire il punto di interruzione, crea e restituisce [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) un'interfaccia.  Lo SDM raccoglie queste interfacce e le passa al pacchetto di debug come singola interfaccia di `IDebugPendingBreakpoint2` .  
  
 finora, nessun evento è stato generato.  
  
 Il pacchetto di debug quindi tenta di associare il punto di interruzione in sospeso al codice o ai dati chiamando [Operazione di binding](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md), che viene implementato da DE.  
  
 Se il punto di interruzione verrà associato, il DE invia [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) un'interfaccia eventi al pacchetto di debug.  Il pacchetto di debug utilizza questa interfaccia per enumerare tutti i contesti di codice \(o di un contesto dati\) associati al punto di interruzione chiamando [EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md), che restituisce una o [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) più interfacce.  [GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md) L'interfaccia restituisce [IDebugBreakpointResolution2](../../extensibility/debugger/reference/idebugbreakpointresolution2.md) un'interfaccia e [GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) restituisce [BP\_RESOLUTION\_INFO](../../extensibility/debugger/reference/bp-resolution-info.md) un che contiene il codice o il contesto dati.  
  
 Se il DE non è possibile associare il punto di interruzione, invia una singola [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) interfaccia eventi al pacchetto di debug.  Il pacchetto di debug recupera il tipo di errore \(errore o avviso\) e il messaggio informativo chiamando [GetErrorBreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md), seguito da [GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) e [GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md).  Ciò restituisce [BP\_ERROR\_RESOLUTION\_INFO](../../extensibility/debugger/reference/bp-error-resolution-info.md) una struttura che contiene il tipo e il messaggio di errore.  
  
 Se un DE gestisce un punto di interruzione non può essere associato, restituisce un errore di tipo `BPET_TYPE_ERROR`.  Il pacchetto di debug risponde visualizzare una finestra di dialogo errori e l'ide appoggia un glifo di esclamazione nel glifo di un punto di interruzione a sinistra della riga di codice sorgente.  
  
 Se un DE gestisce un punto di interruzione, non può eseguire l'associazione, ma un altro DE possibile associare, restituisce un avviso.  L'ide risponde inserendo un glifo dell'applicazione nel glifo di un punto di interruzione a sinistra della riga di codice sorgente.  
  
## Vedere anche  
 [Attività di debug](../../extensibility/debugger/debugging-tasks.md)