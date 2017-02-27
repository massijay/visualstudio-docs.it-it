---
title: "IDebugWindowsComputerPort2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Interfaccia IDebugWindowsComputerPort2"
ms.assetid: 25f327b8-0303-4268-88d1-74df630436aa
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugWindowsComputerPort2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Consente di eseguire query per ottenere informazioni sul computer di destinazione.  
  
## Sintassi  
  
```  
IDebugWindowsComputerPort2 : IUnknown  
```  
  
## Note per gli implementatori  
 Questa interfaccia viene implementata dagli oggetti della porta di amministratore di debug della sessione.  
  
## Metodi  
 Nella tabella seguente sono elencati i metodi di `IDebugWindowsComputerPort2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetComputerInfo](../../../extensibility/debugger/reference/idebugwindowscomputerport2-getcomputerinfo.md)|Recupera le informazioni relative al computer in cui il debugger in esecuzione.|  
  
## Requisiti  
 intestazione: Msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll