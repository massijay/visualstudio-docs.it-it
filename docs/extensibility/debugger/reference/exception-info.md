---
title: "EXCEPTION_INFO | Microsoft Docs"
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
  - "EXCEPTION_INFO"
helpviewer_keywords: 
  - "Struttura EXCEPTION_INFO"
ms.assetid: d046957a-b97d-420b-b46b-c67cbaef709e
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# EXCEPTION_INFO
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Viene descritta un'eccezione o un errore di runtime generato dal programma sottoposto a debug.  
  
## Sintassi  
  
```cpp#  
typedef struct tagEXCEPTION_INFO {   
   IDebugProgram2* pProgram;  
   BSTR            bstrProgramName;  
   BSTR            bstrExceptionName;  
   DWORD           dwCode;  
   EXCEPTION_STATE dwState;  
   GUID            guidType;  
} EXCEPTION_INFO;  
```  
  
```c#  
public struct EXCEPTION_INFO {   
   public IDebugProgram2 pProgram;  
   public string         bstrProgramName;  
   public string         bstrExceptionName;  
   public uint           dwCode;  
   public uint           dwState;  
   public Guid           guidType;  
};  
```  
  
## Membri  
 pProgram  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) L'oggetto che rappresenta il programma in cui si è verificata l'eccezione.  
  
 bstrProgramName  
 Il nome del programma in cui si è verificata l'eccezione.  
  
 bstrExceptionName  
 Nome dell'eccezione.  
  
 dwCode  
 Il codice di identificazione di eccezione o errore di runtime.  
  
 dwState  
 Un valore [EXCEPTION\_STATE](../../../extensibility/debugger/reference/exception-state.md) dell'enumerazione che definisce lo stato dell'eccezione.  
  
 guidType  
 L'identificatore del linguaggio di GUID, `guidLang` o `guidEng`.  
  
## Note  
 Questa struttura passata come parametro [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md) e [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md) ai metodi.  Questa struttura viene passata [GetException](../Topic/IDebugExceptionEvent2::GetException.md) al metodo da riempire.  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [EXCEPTION\_STATE](../../../extensibility/debugger/reference/exception-state.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)   
 [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)   
 [GetException](../Topic/IDebugExceptionEvent2::GetException.md)