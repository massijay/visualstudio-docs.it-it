---
title: "PROGRAM_DESTROY_FLAGS | Microsoft Docs"
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
  - "Enumerazione PROGRAM_DESTROY_FLAGS"
ms.assetid: be00d4a3-d5b8-4159-b632-64577f534883
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# PROGRAM_DESTROY_FLAGS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Enumera i valori validi del programma eliminati i flag.  
  
## Sintassi  
  
```cpp#  
enum enum_PPROGRAM_DESTROY_FLAGS  
{  
   PROGRAM_DESTROY_CONTINUE_DEBUGGING = 0x1  
};  
typedef DWORD PROGRAM_DESTROY_FLAGS;  
```  
  
```c#  
public enum enum_PPROGRAM_DESTROY_FLAGS  
{  
   PROGRAM_DESTROY_CONTINUE_DEBUGGING = 0x1  
};  
```  
  
## termini  
 PROGRAM\_DESTROY\_CONTINUE\_DEBUGGING  
 Eliminare il programma, ma continuare il debug.  
  
## Note  
 L'enumerazione viene restituito dal [GetFlags](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2-getflags.md) metodo.  
  
## Requisiti  
 intestazione: Msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetFlags](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2-getflags.md)