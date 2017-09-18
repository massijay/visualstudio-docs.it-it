---
title: "THREADPROPERTY_FIELDS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "THREADPROPERTY_FIELDS"
helpviewer_keywords: 
  - "Enumerazione THREADPROPERTY_FIELDS"
ms.assetid: 5b88acb9-03ea-4c29-a788-f0087dccbe23
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# THREADPROPERTY_FIELDS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Specifica le informazioni su un thread devono essere recuperate.  
  
## Sintassi  
  
```cpp#  
enum enum_THREADPROPERTY_FIELDS {   
   TPF_ID           = 0x0001,  
   TPF_SUSPENDCOUNT = 0x0002,  
   TPF_STATE        = 0x0004,  
   TPF_PRIORITY     = 0x0008,  
   TPF_NAME         = 0x0010,  
   TPF_LOCATION     = 0x0020,  
   TPF_ALLFIELDS    = 0xffffffff  
};  
typedef DWORD THREADPROPERTY_FIELDS;  
```  
  
```c#  
public enum enum_THREADPROPERTY_FIELDS {   
   TPF_ID           = 0x0001,  
   TPF_SUSPENDCOUNT = 0x0002,  
   TPF_STATE        = 0x0004,  
   TPF_PRIORITY     = 0x0008,  
   TPF_NAME         = 0x0010,  
   TPF_LOCATION     = 0x0020,  
   TPF_ALLFIELDS    = 0xffffffff  
};  
```  
  
## Membri  
 TPF\_ID  
 Inizializzare\/utilizzare il campo di `dwThreadId` [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) della struttura.  
  
 TPF\_SUSPENDCOUNT  
 Inizializzare\/utilizzare il campo di `dwSuspendCount` della struttura di `THREADPROPERTIE`Oggetti.  
  
 TPF\_STATE  
 Inizializzare\/utilizzare il campo di `dwThreadState` della struttura di `THREADPROPERTIE`Oggetti.  
  
 TPF\_PRIORITY  
 Inizializzare\/utilizzare il campo di `bstrPriority` della struttura di `THREADPROPERTIE`Oggetti.  
  
 TPF\_NAME  
 Inizializzare\/utilizzare il campo di `bstrName` della struttura di `THREADPROPERTIE`Oggetti.  
  
 TPF\_LOCATION  
 Inizializzare\/utilizzare il campo di `bstrLocation` della struttura di `THREADPROPERTIE`Oggetti.  
  
 TPF\_ALLFIELDS  
 specifica tutti i campi.  
  
## Note  
 Questi valori vengono passati come argomento al [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) metodo per indicare i campi [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) della struttura devono essere inizializzati.  
  
 Questi valori vengono utilizzati in membro di `dwFields` della struttura di `THREADPROPERTIES` per indicare quali campi vengono utilizzati e validi.  
  
 Questi flag possono essere combinate con `OR`bit per bit.  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)   
 [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)