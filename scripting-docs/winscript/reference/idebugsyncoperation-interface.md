---
title: "Interfaccia IDebugSyncOperation | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "Interfaccia IDebugSyncOperation"
ms.assetid: 8d714492-1836-462c-980a-c99e91a2c81b
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Interfaccia IDebugSyncOperation
Consente a un modulo di gestione di script sottrarre un'operazione \(come valutazione di un'espressione\) che deve essere eseguito come annidato in un thread bloccato particolare.  L'interfaccia fornisce inoltre un meccanismo per annullare operazioni insensibili.  
  
 Oltre ai metodi ereditati da `IUnknown`, l'interfaccia `IDebugSyncOperation` espone i metodi seguenti.  
  
## Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDebugSyncOperation::GetTargetThread](../../winscript/reference/idebugsyncoperation-gettargetthread.md)|Restituisce il thread dell'applicazione di destinazione per l'operazione sincrona.|  
|[IDebugSyncOperation::Execute](../../winscript/reference/idebugsyncoperation-execute.md)|In modo sincrono esegue l'operazione e restituisce.|  
|[IDebugSyncOperation::InProgressAbort](../../winscript/reference/idebugsyncoperation-inprogressabort.md)|Annullare l'operazione in corso in un altro thread.|