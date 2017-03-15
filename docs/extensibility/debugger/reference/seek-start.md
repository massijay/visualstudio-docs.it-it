---
title: "SEEK_START | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SEEK_START"
helpviewer_keywords: 
  - "Enumerazione SEEK_START"
ms.assetid: 55bd8901-626e-428b-a263-23b14417f4c6
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# SEEK_START
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Specifica la posizione da cui iniziare la ricerca in un flusso del disassembly.  
  
## Sintassi  
  
```cpp#  
enum enum_SEEK_START {   
   SEEK_START_BEGIN       = 0x0001,  
   SEEK_START_END         = 0x0002,  
   SEEK_START_CURRENT     = 0x0003,  
   SEEK_START_CODECONTEXT = 0x0004,  
   SEEK_START_CODELOCID   = 0x0005  
};  
typedef DWORD SEEK_START;  
```  
  
```c#  
public enum enum_SEEK_START {   
   SEEK_START_BEGIN       = 0x0001,  
   SEEK_START_END         = 0x0002,  
   SEEK_START_CURRENT     = 0x0003,  
   SEEK_START_CODECONTEXT = 0x0004,  
   SEEK_START_CODELOCID   = 0x0005  
};  
```  
  
## Membri  
 SEEK\_START\_BEGIN  
 Avviata la ricerca all'inizio del documento corrente.  
  
 SEEK\_START\_END  
 Avviata la ricerca alla fine del documento corrente.  
  
 SEEK\_START\_CURRENT  
 Avviata la ricerca alla posizione corrente del documento corrente.  
  
 SEEK\_START\_CODECONTEXT  
 Avviata la ricerca al contesto di codice specificato del documento corrente.  
  
 SEEK\_START\_CODELOCID  
 Avviata la ricerca l'identificatore specificato posizione del codice.  Gli identificatori posizione del codice vengono ottenuti chiamando [GetCurrentLocation](../Topic/IDebugDisassemblyStream2::GetCurrentLocation.md).  
  
## Note  
 Passato come argomento [Ricerca](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md) al metodo.  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Ricerca](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)   
 [GetCurrentLocation](../Topic/IDebugDisassemblyStream2::GetCurrentLocation.md)