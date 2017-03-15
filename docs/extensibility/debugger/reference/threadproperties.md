---
title: "THREADPROPERTIES | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "THREADPROPERTIES"
helpviewer_keywords: 
  - "Struttura THREADPROPERTIES"
ms.assetid: 7d397207-db03-4ec0-9f79-3794056ed89f
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# THREADPROPERTIES
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Vengono descritte le proprietà di un thread.  
  
## Sintassi  
  
```cpp#  
typedef struct _tagTHREADPROPERTIES {   
   THREADPROPERTY_FIELDS dwFields;  
   DWORD                 dwThreadId;  
   DWORD                 dwSuspendCount;  
   DWORD                 dwThreadState;  
   BSTR                  bstrPriority;  
   BSTR                  bstrName;  
   BSTR                  bstrLocation;  
} THREADPROPERTIES;  
```  
  
```c#  
public struct THREADPROPERTIES {   
   public uint   dwFields;  
   public uint   dwThreadId;  
   public uint   dwSuspendCount;  
   public uint   dwThreadState;  
   public string bstrPriority;  
   public string bstrName;  
   public string bstrLocation;  
};  
```  
  
## Membri  
 dwFields  
 Una combinazione di flag [THREADPROPERTY\_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md) dall'enumerazione, descrivente di sistema in questa struttura è valida.  
  
 dwThreadId  
 ID del thread  
  
 dwSuspendCount  
 Il conteggio di sospensione del thread.  
  
 dwThreadState  
 Un valore [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md) dell'enumerazione che indica lo stato del thread in esecuzione.  
  
 bstrPriority  
 Una stringa che specifica la priorità dei thread; ad esempio, “sul normale„, “il normale„, o “l'ora critico„.  
  
 bstName  
 Il nome del thread.  
  
 bstrLocation  
 Il percorso del thread \(in genere lo stack frame in primo piano\), in genere espresso come nome del metodo in cui l'esecuzione non verrà interrotta.  
  
## Note  
 Questa struttura viene soddisfatta da una chiamata [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) al metodo.  Le informazioni così restituite in genere utilizzate in popolare la finestra di **thread** .  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)   
 [THREADPROPERTY\_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md)   
 [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md)