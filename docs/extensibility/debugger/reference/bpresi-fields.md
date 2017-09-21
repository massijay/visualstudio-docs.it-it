---
title: "BPRESI_FIELDS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BPRESI_FIELDS"
helpviewer_keywords: 
  - "Enumerazione BPRESI_FIELDS"
ms.assetid: 99f17b1e-3e67-4f85-89d6-5c6cf45c8008
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# BPRESI_FIELDS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Specifica le informazioni da recuperare sulla corretta risoluzione di un punto di interruzione.  
  
## Sintassi  
  
```cpp#  
enum enum_BPRESI_FIELDS {   
   BPRESI_BPRESLOCATION = 0x0001,  
   BPRESI_PROGRAM       = 0x0002,  
   BPRESI_THREAD        = 0x0004,  
   BPRESI_ALLFIELDS     = 0xffffffff  
};  
typedef DWORD BPRESI_FIELDS;  
```  
  
```c#  
public enum enum_BPRESI_FIELDS {   
   BPRESI_BPRESLOCATION = 0x0001,  
   BPRESI_PROGRAM       = 0x0002,  
   BPRESI_THREAD        = 0x0004,  
   BPRESI_ALLFIELDS     = 0xffffffff  
};  
```  
  
## Membri  
 BPRESI\_BPRESLOCATION  
 Inizializzare\/utilizzare il campo di `bpResLocation` \(posizione di risoluzione del punto di interruzione\) [BP\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) della struttura.  
  
 BPRESI\_PROGRAM  
 Inizializzare\/utilizzare il campo di `pProgram` della struttura di `BP_RESOLUTION_INFO` .  
  
 BPRESI\_THREAD  
 Inizializzare\/utilizzare il campo di `pThread` della struttura di `BP_RESOLUTION_INFO` .  
  
 BPRESI\_ALLFIELDS  
 specifica tutti i campi.  
  
## Note  
 Passato [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) al metodo per indicare i campi [BP\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) della struttura devono essere inizializzati.  
  
 Questi flag vengono inoltre utilizzati per indicare i campi della struttura di `BP_RESOLUTION_INFO` vengono utilizzati e validi a tale struttura viene restituita.  
  
 Questi valori possono essere combinate con `OR`bit per bit.  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)   
 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)