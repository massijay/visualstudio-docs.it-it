---
title: "IDebugPortSupplier3 | Microsoft Docs"
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
  - "IDebugPortSupplier3"
helpviewer_keywords: 
  - "Interfaccia IDebugPortSupplier3"
ms.assetid: e458cd02-2370-4435-8953-17d7a60ce152
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPortSupplier3
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questa interfaccia consente di un chiamante di determinare se un fornitore di porte possibile conservare le porte \(scrivendole su disco\) tra il debugger chiama quindi ottenere un elenco di quelli le porte mantenute.  
  
## Sintassi  
  
```  
IDebugPortSupplier3 : IDebugPortSupplier2  
```  
  
## Note per gli implementatori  
 Un fornitore di porte personalizzato implementa questa interfaccia per supportare le informazioni sulla porta salvare in modo permanente o di salvataggio su disco.  È necessario implementare questa interfaccia lo stesso oggetto [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) dell'interfaccia.  
  
## Note per i chiamanti  
 L [QueryInterface](/visual-cpp/atl/queryinterface)interfaccia di `IDebugPortSupplier2` per ottenere questa interfaccia.  
  
## Metodi nell'ordine di Vtable  
 Oltre ai metodi ereditati [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) dall'interfaccia, questa interfaccia supporta quanto segue:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[CanPersistPorts](../../../extensibility/debugger/reference/idebugportsupplier3-canpersistports.md)|Restituisce se il fornitore di porte può mantenere le porte \(scrivendole su disco\) tra il debugger chiama.|  
|[EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md)|Restituisce un oggetto che può essere utilizzato per enumerare da tutte le porte che sono state scritte su disco dal fornitore di porte.|  
  
## Note  
 Se un fornitore di porte può mantenere le porte tra le chiamate, deve implementare questa interfaccia.  Le porte devono essere caricate quando il fornitore di porte viene creata un'istanza di e viene scritto sul disco quando il fornitore di porte viene eliminato.  
  
 Il modulo di debug in genere non interagisce con un fornitore di porte e non si utilizzano per l'interfaccia.  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)