---
title: "IDebugProperty3 | Microsoft Docs"
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
  - "IDebugProperty3"
helpviewer_keywords: 
  - "Interfaccia IDebugProperty3"
ms.assetid: 8f9be68d-4490-4eca-8f6b-8a10ed77e226
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProperty3
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questa interfaccia fornisce supporto per:  
  
-   Recuperando una stringa arbitrariamente lungo associata alla proprietà.  
  
-   Associando un ID univoco alla proprietà.  
  
-   Per recuperare un elenco di visualizzatori personalizzati per la proprietà.  
  
-   Impostare il valore di una proprietà con la possibilità di segnalare errori risultanti  
  
## Sintassi  
  
```  
IDebugProperty3 : IDebugProperty2  
```  
  
## Note per gli implementatori  
 Il motore \(DE\) di debug implementa questa interfaccia lo stesso oggetto che implementa [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) per fornire il supporto per le stringhe lunghe, la proprietà ID e i visualizzatori personalizzati.  
  
## Note per i chiamanti  
 chiamata [QueryInterface](/visual-cpp/atl/queryinterface) su un'interfaccia di `IDebugProperty2` per ottenere questa interfaccia.  
  
## Metodi nell'ordine di Vtable  
 Oltre ai metodi ereditati da `IDebugProperty2`, l'interfaccia `IDebugProperty3` espone i metodi seguenti.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetStringCharLength](../../../extensibility/debugger/reference/idebugproperty3-getstringcharlength.md)|Restituisce la lunghezza della stringa associata alla proprietà.|  
|[GetStringChars](../Topic/IDebugProperty3::GetStringChars.md)|Restituisce la stringa in un buffer fornito dall'utente.|  
|[CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)|crea un ID univoco per questa proprietà.|  
|[DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)|Elimina ID univoco per questa proprietà.|  
|[GetCustomViewerCount](../Topic/IDebugProperty3::GetCustomViewerCount.md)|Restituisce il numero di visualizzatori personalizzati che questa proprietà può essere visualizzata con.|  
|[GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)|Restituisce l'elenco dei visualizzatori personalizzati che questa proprietà può essere visualizzata con.|  
|[SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)|Imposta il valore di questa proprietà, restituendo un messaggio di errore se qualsiasi elemento si errato.|  
  
## Note  
 [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md) è il modo preferito per l'amministratore \(SDM\) di debug della sessione di impostare un valore della proprietà.  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)