---
title: "FRAMEINFO | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "FRAMEINFO"
helpviewer_keywords: 
  - "Struttura FRAMEINFO"
ms.assetid: 95001b89-dddb-45bb-889d-8327994e38a5
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# FRAMEINFO
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Viene descritto uno stack frame.  
  
## Sintassi  
  
```cpp#  
typedef struct tagFRAMEINFO {   
   FRAMEINFO_FLAGS    m_dwValidFields;  
   BSTR               m_bstrFuncName;  
   BSTR               m_bstrReturnType;  
   BSTR               m_bstrArgs;  
   BSTR               m_bstrLanguage;  
   BSTR               m_bstrModule;  
   UINT64             m_addrMin;  
   UINT64             m_addrMax;  
   IDebugStackFrame2* m_pFrame;  
   IDebugModule2*     m_pModule;  
   BOOL               m_fHasDebugInfo;  
   BOOL               m_fStaleCode;  
   BOOL               m_fAnnotatedFrame;  
} FRAMEINFO;  
```  
  
```c#  
public struct FRAMEINFO {   
   public uint              m_dwValidFields;  
   public string            m_bstrFuncName;  
   public string            m_bstrReturnType;  
   public string            m_bstrArgs;  
   public string            m_bstrLanguage;  
   public string            m_bstrModule;  
   public ulong             m_addrMin;  
   public ulong             m_addrMax;  
   public IDebugStackFrame2 m_pFrame;  
   public IDebugModule2     m_pModule;  
   public int               m_fHasDebugInfo;  
   public int               m_fStaleCode;  
   public int               m_fAnnotatedFrame;  
} FRAMEINFO;  
```  
  
## Membri  
 m\_dwValidFields  
 Una combinazione di flag [FRAMEINFO\_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md) dall'enumerazione che specifica quali campi vengono riempiti.  
  
 m\_bstrFuncName  
 Il nome della funzione associato allo stack frame.  
  
 m\_bstrReturnType  
 Il tipo restituito associato allo stack frame.  
  
 m\_bstrArgs  
 Gli argomenti alla funzione associata allo stack frame.  
  
 m\_bstrLanguage  
 Il linguaggio in cui la funzione viene distribuita.  
  
 m\_bstrModule  
 Il nome del modulo associato allo stack frame.  
  
 m\_addrMin  
 L'indirizzo fisico minimo dello stack.  
  
 m\_addrMAX  
 L'indirizzo fisico massimo dello stack.  
  
 m\_pFrame  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) l'oggetto che rappresenta questo stack frame.  
  
 m\_pFrame  
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) l'oggetto che rappresenta il modulo che contiene questo stack frame.  
  
 m\_fHasDebugInfo  
 Diverso da zero \(`TRUE`\) se le informazioni di debug sono presenti nel frame specificato.  
  
 m\_fHasDebugInfo  
 Diverso da zero \(`TRUE`\) se lo stack frame viene associato al codice non è più valido.  
  
 m\_fHasDebugInfo  
 Diverso da zero \(`TRUE`\) se lo stack frame viene annotata dall'amministratore di debug della sessione \(SDM\).  
  
## Note  
 Questa struttura viene passata [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md) al metodo da riempire.  Questa struttura è contenuta in un elenco che è contenuto [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) nell'interfaccia che, a sua volta, viene restituita da una chiamata [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) al metodo.  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [FRAMEINFO\_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)   
 [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)   
 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)