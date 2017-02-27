---
title: "IDebugProgramDestroyEventFlags2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Interfaccia IDebugProgramDestroyEventFlags2"
ms.assetid: d384ff71-dc71-40b9-a871-801f8b6a3418
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# IDebugProgramDestroyEventFlags2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Consente a un modulo di debug per eseguire l'override del comportamento predefinito dell' interfaccia utente di [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]al termine di una sessione di debug.  
  
## Sintassi  
  
```  
IDebugProgramDestroyEventFlags2 : IUnknown  
```  
  
## Note per gli implementatori  
 Questa interfaccia viene implementata dai motori di debug.  È utile per gli host che possono creare ed eliminare più programmi sulla durata di un processo.  
  
## Metodi  
 Nella tabella seguente sono elencati i metodi di `IDebugProgramDestroyEventFlags2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetFlags](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2-getflags.md)|Recupera il programma eliminati i flag.|  
  
## Note  
 Il comportamento predefinito dell'interfaccia utente di  [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] è di tornare a programmi della modalità progettazione dopo tutti ha inviato un programma eliminato l'evento.  Questa interfaccia consente a un modulo di debug per modificare tale comportamento.  
  
## Requisiti  
 intestazione: Msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll