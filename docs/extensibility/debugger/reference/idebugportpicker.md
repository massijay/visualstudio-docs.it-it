---
title: "IDebugPortPicker | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Interfaccia IDebugPortPicker"
ms.assetid: 8b7f6685-a3c5-4355-b706-c1b574f6ff84
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugPortPicker
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

rappresenta un'interfaccia utente personalizzata per selezionare la porta.  
  
## Sintassi  
  
```  
IDebugPortPicker : IUnknown  
```  
  
## Note per gli implementatori  
 Questa interfaccia viene implementata da fornitori di porte.  Un fornitore di porte definisce la selezione della porta esponendola come CLSID e scegliendo `metricPortPickerCLSID` metrica al CLSID esposto.  
  
## Metodi  
 Nella tabella seguente sono elencati i metodi di `IDebugPortPicker`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[DisplayPortPicker](../../../extensibility/debugger/reference/idebugportpicker-displayportpicker.md)|Visualizzare la finestra di dialogo specificata che consente di selezionare una porta.|  
|[SetSite](../../../extensibility/debugger/reference/idebugportpicker-setsite.md)|imposta il provider di servizi.|  
  
## Requisiti  
 intestazione: Msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll