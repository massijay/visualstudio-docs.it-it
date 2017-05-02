---
title: "Interfaccia IDebugAsyncOperation | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "Interfaccia IDebugAsyncOperation"
ms.assetid: ebb2ea75-1443-4d8a-812d-171a166f5f9d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Interfaccia IDebugAsyncOperation
L'amministratore processo di debug implementa l'interfaccia `IDebugAsyncOperation`.  Un motore di linguaggio chiama il metodo `IDebugApplication::CreateAsyncDebugOperation` per ottenere un riferimento a questa interfaccia.  Il motore di linguaggio può utilizzare l'interfaccia `IDebugAsyncOperation` per fornire l'accesso asincrono a un'operazione sincrona di debug.  
  
 Oltre ai metodi ereditati da `IUnknown`, l'interfaccia `IDebugAsyncOperation` espone i metodi seguenti.  
  
## Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDebugAsyncOperation::GetSyncDebugOperation](../../winscript/reference/idebugasyncoperation-getsyncdebugoperation.md)|Restituisce l'operazione di debug sincrona associata all'oggetto.|  
|[IDebugAsyncOperation::Start](../../winscript/reference/idebugasyncoperation-start.md)|Provoca l'operazione asincrona l'avvio.|  
|[IDebugAsyncOperation::Abort](../../winscript/reference/idebugasyncoperation-abort.md)|Annullare l'operazione.|  
|[IDebugAsyncOperation::QueryIsComplete](../../winscript/reference/idebugasyncoperation-queryiscomplete.md)|Determina se l'operazione di debug è stata completata.|  
|[IDebugAsyncOperation::GetResult](../../winscript/reference/idebugasyncoperation-getresult.md)|Fornisce il parametro dell'oggetto di ritorno e valore restituito dall'operazione sincrona di debug.|