---
title: "MESSAGETYPE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MESSAGETYPE"
helpviewer_keywords: 
  - "Enumerazione MESSAGETYPE"
ms.assetid: 800cc77d-3c27-4763-a9df-552a9384bd49
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# MESSAGETYPE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Specifica il tipo di messaggio e il motivo.  
  
## Sintassi  
  
```cpp#  
enum enum_MESSAGETYPE {   
   MT_OUTPUTSTRING      = 0x0000001,  
   MT_MESSAGEBOX        = 0x00000002,  
   MT_TYPE_MASK         = 0x000000FF,  
   MT_REASON_EXCEPTION  = 0x00000100,  
   MT_REASON_TRACEPOINT = 0x00000200,  
   MT_REASON_MASK       = 0x0000FF00  
};  
typedef DWORD MESSAGETYPE;  
```  
  
```c#  
public enum enum_MESSAGETYPE {   
   MT_OUTPUTSTRING      = 0x0000001,  
   MT_MESSAGEBOX        = 0x00000002,  
   MT_TYPE_MASK         = 0x000000FF,  
   MT_REASON_EXCEPTION  = 0x00000100,  
   MT_REASON_TRACEPOINT = 0x00000200,  
   MT_REASON_MASK       = 0x0000FF00  
};  
```  
  
## Membri  
 MT\_OUTPUTSTRING  
 Indica che il messaggio deve essere inviato alla finestra di output.  Ciò si escludono a vicenda da `MT_MESSAGEBOX`.  
  
 MT\_MESSAGEBOX  
 Indica che il messaggio deve essere visualizzato in una finestra di messaggio.  Ciò si escludono a vicenda da `MT_OUTPUTSTRING`.  
  
 MT\_TYPE\_MASK  
 Un valore di maschera per isolare la destinazione per il messaggio.  
  
 MT\_REASON\_EXCEPTION  
 Indica che una finestra di messaggio viene indicanda da un'eccezione.  Ciò si escludono a vicenda da `MT_REASON_TRACEPOINT`.  
  
 MT\_REASON\_TRACEPOINT  
 Indica che una finestra di messaggio viene indicanda come conseguenza di raggiungere un punto di analisi.  Ciò si escludono a vicenda a `MT_REASON_EXCEPTION`.  
  
 MT\_REASON\_MASK  
 Un valore di maschera per isolare il motivo del messaggio che viene visualizzato.  
  
## Note  
 Questi valori vengono restituiti [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md) dai metodi e [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md) .  
  
 Uno dei valori di motivo può essere combinato con uno dei valori di destinazione di output mediante `OR`bit per bit.  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)   
 [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md)