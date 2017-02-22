---
title: "IDebugSourceServerModule | Microsoft Docs"
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
  - "Interfaccia IDebugSourceServerModule"
ms.assetid: 38213060-451d-46e6-8b4a-efc123e01a2c
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugSourceServerModule
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Rappresenta le informazioni del server di origine contenute in un file PDB.  
  
## Sintassi  
  
```  
IDebugSourceServerModule : IUnknown  
```  
  
## Note per gli implementatori  
 Questa interfaccia viene implementata in moduli di gestione del debugger e viene utilizzata dall'interfaccia utente del debugger.  
  
## Metodi  
 Nella tabella seguente sono elencati i metodi di `IDebugSourceServerModule`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetSourceServerData](../../../extensibility/debugger/reference/idebugsourceservermodule-getsourceserverdata.md)|Recupera una matrice di informazioni del server di origine.|  
  
## Requisiti  
 intestazione: Msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll