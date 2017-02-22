---
title: "IDebugBreakpointChecksumRequest2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Interfaccia IDebugBreakpointChecksumRequest2"
ms.assetid: 9cfdbca5-052c-48e9-8411-e2e9e4065d00
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugBreakpointChecksumRequest2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Rappresenta un checksum del documento per una richiesta del punto di interruzione.  
  
## Sintassi  
  
```  
IDebugBreakpointChecksumRequest2 : IUnknown  
```  
  
## Note per gli implementatori  
 Viene implementata dal pacchetto di [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Debug e utilizzato dai motori di debug.  
  
## Metodi  
 Nella tabella seguente sono elencati i metodi di `IDebugBreakpointChecksumRequest2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetChecksum](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2-getchecksum.md)|Recupera il checksum del documento per una richiesta del punto di interruzione fornita l'identificatore univoco dell'algoritmo di checksum da utilizzare.|  
|[IsChecksumEnabled](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2-ischecksumenabled.md)|determina se il checksum è abilitato per questo documento.|  
  
## Requisiti  
 intestazione: Msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll