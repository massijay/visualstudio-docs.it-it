---
title: "IDebugPort2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPort2"
helpviewer_keywords: 
  - "Interfaccia IDebugPort2"
ms.assetid: 8fd87f05-a950-4d14-b925-98be29d4facc
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPort2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questa interfaccia rappresenta una porta di debug in un computer.  
  
## Sintassi  
  
```  
IDebugPort2 : IUnknown  
```  
  
## Note per gli implementatori  
 Un fornitore di porte personalizzato implementa questa interfaccia per rappresentare una porta di debug in un computer.  
  
 Se la porta supporta inviare gli eventi di porta, deve implementare anche l'interfaccia di <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> per supportare un'interfaccia di <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> che a sua volta fornisce [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) l'interfaccia.  
  
## Note per i chiamanti  
 Le chiamate a [GetPort](../../../extensibility/debugger/reference/idebugportsupplier2-getport.md) o [Aggiungi porta](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) restituiscono questa interfaccia, che rappresenta la porta richiesta.  
  
## Metodi nell'ordine di Vtable  
 Nella tabella seguente sono elencati i metodi di `IDebugPort2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetPortName](../../../extensibility/debugger/reference/idebugport2-getportname.md)|Restituisce il nome della porta.|  
|[GetPortId](../../../extensibility/debugger/reference/idebugport2-getportid.md)|Restituisce l'identificatore della porta.|  
|[GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)|restituisce la richiesta utilizzata per creare una porta \(se disponibile\).|  
|[GetPortSupplier](../Topic/IDebugPort2::GetPortSupplier.md)|restituisce il fornitore di porte per questa porta.|  
|[GetProcess](../Topic/IDebugPort2::GetProcess.md)|Restituisce un'interfaccia al processo specificato l'identificatore del processo.|  
|[EnumProcesses](../Topic/IDebugPort2::EnumProcesses.md)|Enumera i processi in esecuzione su una porta.|  
  
## Note  
 La porta locale consente di accedere a tutti i processi e programmi in esecuzione sul computer locale.  Altre porte potrebbero rappresentare una connessione di rete seriale a un dispositivo basato su windows CE, o una connessione di rete a un computer non DCOM.  L'interfaccia di `IDebugPort2` viene utilizzata per cercare il nome e l'identificatore di una porta, enumerare tutti elabora il funzionamento della porta e forniscono le funzionalità per avviare e interrompere i processi sulla porta.  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)