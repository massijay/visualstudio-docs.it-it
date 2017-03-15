---
title: "PROCESS_INFO_FIELDS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "PROCESS_INFO_FIELDS"
helpviewer_keywords: 
  - "Enumerazione PROCESS_INFO_FIELDS"
ms.assetid: 0d9cc345-3d3a-44d8-ae15-a67acb97a828
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# PROCESS_INFO_FIELDS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Specifica il tipo di informazioni per recuperare un processo.  
  
## Sintassi  
  
```cpp#  
enum enum_PROCESS_INFO_FIELDS {   
   PIF_FILE_NAME             = 0x00000001,  
   PIF_BASE_NAME             = 0x00000002,  
   PIF_TITLE                 = 0x00000004,  
   PIF_PROCESS_ID            = 0x00000008,  
   PIF_SESSION_ID            = 0x00000010,  
   PIF_ATTACHED_SESSION_NAME = 0x00000020,  
   PIF_CREATION_TIME         = 0x00000040,  
   PIF_FLAGS                 = 0x00000080,  
   PIF_ALL                   = 0x000000ff  
};  
typedef DWORD PROCESS_INFO_FIELDS;  
```  
  
```c#  
public enum enum_PROCESS_INFO_FIELDS {   
   PIF_FILE_NAME             = 0x00000001,  
   PIF_BASE_NAME             = 0x00000002,  
   PIF_TITLE                 = 0x00000004,  
   PIF_PROCESS_ID            = 0x00000008,  
   PIF_SESSION_ID            = 0x00000010,  
   PIF_ATTACHED_SESSION_NAME = 0x00000020,  
   PIF_CREATION_TIME         = 0x00000040,  
   PIF_FLAGS                 = 0x00000080,  
   PIF_ALL                   = 0x000000ff  
};  
```  
  
## Membri  
 PIF\_FILE\_NAME  
 Inizializzare\/utilizzare il campo di `bstrFileName` [PROCESS\_INFO](../../../extensibility/debugger/reference/process-info.md) della struttura.  
  
 PIF\_BASE\_NAME  
 Inizializzare\/utilizzare il campo di `bstrBaseName` della struttura di `PROCESS_INFO` .  
  
 PIF\_TITLE  
 Inizializzare\/utilizzare il campo di `bstrTitle` della struttura di `PROCESS_INFO` .  
  
 PIF\_PROCESS\_ID  
 Inizializzare\/utilizzare il campo di `ProcessId` della struttura di `PROCESS_INFO` .  
  
 PIF\_SESSION\_ID  
 Inizializzare\/utilizzare il campo di `dwSessionId` della struttura di `PROCESS_INFO` .  
  
 PIF\_ATTACHED\_SESSION\_NAME  
 Inizializzare\/utilizzare il campo di `bstrAttachedSessionName` della struttura di `PROCESS_INFO` .  
  
 PIF\_CREATION\_TIME  
 Inizializzare\/utilizzare il campo di `CreationTime` della struttura di `PROCESS_INFO` .  
  
 PIF\_FLAGS  
 Inizializzare\/utilizzare il campo di `Flags` della struttura di `PROCESS_INFO` .  
  
 PIF\_ALL  
 Compilare tutti i campi.  
  
## Note  
 Passato [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md) al metodo per indicare i campi [PROCESS\_INFO](../../../extensibility/debugger/reference/process-info.md) della struttura devono essere inizializzati.  
  
 Utilizzata anche nel campo di `Fields` della struttura di `PROCESS_INFO` per indicare quali campi vengono utilizzati e validi.  
  
 Questi flag possono essere combinate con `OR`bit per bit.  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [PROCESS\_INFO](../../../extensibility/debugger/reference/process-info.md)