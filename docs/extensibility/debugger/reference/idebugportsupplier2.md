---
title: "IDebugPortSupplier2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPortSupplier2"
helpviewer_keywords: 
  - "Interfaccia IDebugPortSupplier2"
ms.assetid: 37067324-2ea6-4a01-8829-a6e9c7a70068
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPortSupplier2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Buchi di alimentazioni di questa interfaccia alla sessione di debug l'amministratore \(SDM\).  
  
## Sintassi  
  
```  
IDebugPortSupplier2 : IUnknown  
```  
  
## Note per gli implementatori  
 un fornitore di porte personalizzato implementa questa interfaccia per rappresentare un fornitore di porte.  
  
## Note per i chiamanti  
 Una chiamata a `CoCreateInstance` con `GUID` di un fornitore di porte restituisce questa interfaccia \(si tratta della modalità tipica ottenere questa interfaccia\).  Di seguito è riportato un esempio:  
  
```cpp#  
IDebugPortSupplier2 *GetPortSupplier(GUID *pPortSupplierGuid)  
{  
    IDebugPortSupplier2 *pPS = NULL;  
    if (pPortSupplierGuid != NULL) {  
        CComPtr<IDebugPortSupplier2> spPortSupplier;  
        spPortSupplier.CoCreateInstance(*pPortSupplierGuid);  
        if (spPortSupplier != NULL) {  
            pPS = spPortSupplier.Detach();  
        }  
    }  
    return (pPS);  
}  
```  
  
 Una chiamata [GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md) a restituisce questa interfaccia, che rappresenta il fornitore di porte corrente utilizzato da [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)].  
  
 [GetPortSupplier](../Topic/IDebugPort2::GetPortSupplier.md) restituisce questa interfaccia, che rappresenta il fornitore di porte che ha creato la porta.  
  
 [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md) rappresenta un elenco delle interfacce di `IDebugPortSupplier` \(l'interfaccia di `IEnumDebugPortSuppliers` viene ottenuta da [EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md), che rappresenta tutti fornitori di porte registrati con [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]\).  
  
 Il modulo di debug in genere non interagisce con un fornitore di porte.  
  
## Metodi nell'ordine di Vtable  
 Nella tabella seguente sono elencati i metodi di `IDebugPortSupplier2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetPortSupplierName](../../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md)|Ottiene il nome del fornitore di porte.|  
|[GetPortSupplierId](../Topic/IDebugPortSupplier2::GetPortSupplierId.md)|Ottiene l'identificatore del fornitore di porte.|  
|[GetPort](../../../extensibility/debugger/reference/idebugportsupplier2-getport.md)|ottiene una porta da un fornitore di porte.|  
|[EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)|Enumera le porte già esistenti.|  
|[CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md)|Verifica che un fornitore di porte supporta le nuove porte di aggiunta.|  
|[Aggiungi porta](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)|aggiunge una porta.|  
|[RemovePort](../../../extensibility/debugger/reference/idebugportsupplier2-removeport.md)|rimuove una porta.|  
  
## Note  
 Un fornitore di porte possibile identificarsi per nome e l'ID, aggiungere e rimuovere le porte e enumerare tutte le porte richieste dal fornitore di porte di.  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetPortSupplier](../Topic/IDebugPort2::GetPortSupplier.md)   
 [GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)   
 [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)