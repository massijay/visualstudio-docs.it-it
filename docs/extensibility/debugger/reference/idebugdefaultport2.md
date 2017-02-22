---
title: "IDebugDefaultPort2 | Microsoft Docs"
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
  - "IDebugDefaultPort2"
helpviewer_keywords: 
  - "Interfaccia IDebugDefaultPort2"
ms.assetid: 7b3452af-9a96-4c4c-9946-4339b72d3d7b
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugDefaultPort2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questa interfaccia dispone di diversi metodi per accedere al server di una porta e le funzionalità di notifica.  
  
## Sintassi  
  
```  
IDebugDefaultPort2 : IDebugPort2  
```  
  
## Note per gli implementatori  
 Visual Studio implementa questa interfaccia per rappresentare la porta di debug per accedere ai programmi.  Un fornitore di porte personalizzato anche possibile implementare questa interfaccia se gestisce il debug remoto.  
  
## Note per i chiamanti  
 Un argomento ai [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md) metodi e fornisce l'interfaccia.  La [QueryInterface](/visual-cpp/atl/queryinterface) [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) [QueryInterface](/visual-cpp/atl/queryinterface) chiamata [QueryInterface](/visual-cpp/atl/queryinterface) a un'interfaccia inoltre possibile ottenere questa interfaccia.  
  
## Metodi nell'ordine di Vtable  
 Oltre ai metodi definiti in [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md), l'interfaccia implementa i metodi seguenti:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetPortNotify](../Topic/IDebugDefaultPort2::GetPortNotify.md)|Ottiene l'interfaccia di notifica della porta da questa porta.|  
|[Metodo GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)|Ottiene l'interfaccia al server che ospita la porta.|  
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugdefaultport2-queryislocal.md)|Determina se questa porta è in esecuzione nel computer locale.|  
  
## Note  
 Il nome “`IDebugDefaultPort2`„ è un bit di una definizione appropriata, che non rappresenta una porta predefinita.  Potrebbe essere chiamato “IDebugPort3„.  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)