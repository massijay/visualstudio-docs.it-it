---
title: "CONTEXT_INFO_FIELDS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CONTEXT_INFO_FIELDS"
helpviewer_keywords: 
  - "Enumerazione CONTEXT_INFO_FIELDS"
ms.assetid: ef436bd3-738e-47e8-828c-8febce752439
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# CONTEXT_INFO_FIELDS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Specifica le informazioni da recuperare su un contesto di memoria.  
  
## Sintassi  
  
```cpp#  
enum enum_CONTEXT_INFO_FIELDS {   
   CIF_MODULEURL =       0x00000001,  
   CIF_FUNCTION =        0x00000002,  
   CIF_FUNCTIONOFFSET =  0x00000004,  
   CIF_ADDRESS =         0x00000008,  
   CIF_ADDRESSOFFSET =   0x00000010,  
   CIF_ADDRESSABSOLUTE = 0x00000020,  
   CIF_ALLFIELDS =       0x0000003f  
};  
typedef DWORD CONTEXT_INFO_FIELDS;  
```  
  
```c#  
public enum enum_CONTEXT_INFO_FIELDS {  
   CIF_MODULEURL =       0x00000001,  
   CIF_FUNCTION =        0x00000002,  
   CIF_FUNCTIONOFFSET =  0x00000004,  
   CIF_ADDRESS =         0x00000008,  
   CIF_ADDRESSOFFSET =   0x00000010,  
   CIF_ADDRESSABSOLUTE = 0x00000020,  
   CIF_ALLFIELDS =       0x0000003f  
};  
```  
  
## Membri  
 CIF\_MODULEURL  
 Inizializzare\/utilizzare il campo di `bstrModuleUrl` [CONTEXT\_INFO](../../../extensibility/debugger/reference/context-info.md) della struttura.  
  
 CIF\_FUNCTION  
 Inizializzare\/utilizzare il campo di `bstrFunction` della struttura di `CONTEXT_INFO` .  
  
 CIF\_FUNCTIONOFFSET  
 Inizializzare\/utilizzare il campo di `posFunctionOffset` della struttura di `CONTEXT_INFO` .  
  
 CIF\_ADDRESS  
 Inizializzare\/utilizzare il campo di `bstrAddress` della struttura di `CONTEXT_INFO` .  
  
 CIF\_ADDRESSOFFSET  
 Inizializzare\/utilizzare il campo di `bstrAddressOffset` della struttura di `CONTEXT_INFO` .  
  
 CIF\_ALLFIELDS  
 Inizializzare\/utilizza tutti i campi della struttura di `CONTEXT_INFO` .  
  
## Note  
 Questi valori vengono passati a un parametro [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md) al metodo per indicare i campi [CONTEXT\_INFO](../../../extensibility/debugger/reference/context-info.md) della struttura devono essere inizializzati.  
  
 Questi flag vengono inoltre utilizzati per indicare i campi della struttura di `CONTEXT_INFO` vengono utilizzati e validi quando la struttura viene restituita.  
  
 Questi valori possono essere combinati con un OR bit per bit.  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [CONTEXT\_INFO](../../../extensibility/debugger/reference/context-info.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)