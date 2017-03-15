---
title: "BPREQI_FIELDS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BPREQI_FIELDS"
helpviewer_keywords: 
  - "Enumerazione BPREQI_FIELDS"
ms.assetid: 679e771e-4a79-484e-af37-f962ef4aa245
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# BPREQI_FIELDS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Specifica le informazioni da recuperare su una richiesta del punto di interruzione.  
  
## Sintassi  
  
```cpp  
enum enum_BPREQI_FIELDS {   
   BPREQI_BPLOCATION   = 0x0001,  
   BPREQI_LANGUAGE     = 0x0002,  
   BPREQI_PROGRAM      = 0x0004,  
   BPREQI_PROGRAMNAME  = 0x0008,  
   BPREQI_THREAD       = 0x0010,  
   BPREQI_THREADNAME   = 0x0020,  
   BPREQI_PASSCOUNT    = 0x0040,  
   BPREQI_CONDITION    = 0x0080,  
   BPREQI_FLAGS        = 0x0100,  
   BPREQI_ALLOLDFIELDS = 0x01ff  
   BPREQI_VENDOR       = 0x0200,   // BP_REQUEST_INFO2 only  
   BPREQI_CONSTRAINT   = 0x0400,   // BP_REQUEST_INFO2 only  
   BPREQI_TRACEPOINT   = 0x0800,   // BP_REQUEST_INFO2 only  
   BPREQI_ALLFIELDS    = 0x0fff    // BP_REQUEST_INFO2 only  
};  
typedef DWORD BPREQI_FIELDS;  
```  
  
```c#  
public enum enum_BPREQI_FIELDS {   
   BPREQI_BPLOCATION   = 0x0001,  
   BPREQI_LANGUAGE     = 0x0002,  
   BPREQI_PROGRAM      = 0x0004,  
   BPREQI_PROGRAMNAME  = 0x0008,  
   BPREQI_THREAD       = 0x0010,  
   BPREQI_THREADNAME   = 0x0020,  
   BPREQI_PASSCOUNT    = 0x0040,  
   BPREQI_CONDITION    = 0x0080,  
   BPREQI_FLAGS        = 0x0100,  
   BPREQI_ALLOLDFIELDS = 0x01ff  
   BPREQI_VENDOR       = 0x0200,   // BP_REQUEST_INFO2 only  
   BPREQI_CONSTRAINT   = 0x0400,   // BP_REQUEST_INFO2 only  
   BPREQI_TRACEPOINT   = 0x0800,   // BP_REQUEST_INFO2 only  
   BPREQI_ALLFIELDS    = 0x0fff    // BP_REQUEST_INFO2 only  
};  
```  
  
## Membri  
 BPREQI\_BPLOCATION  
 Inizializzare\/utilizzare il campo di `bpLocation` \(posizione del punto di interruzione\) di [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md) o [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) struttura.  
  
 BPREQI\_LANGUAGE  
 Inizializzare\/utilizzare il campo di `guidLanguage` della struttura di `BP_REQUEST_INFO2` o di `BP_REQUEST_INFO` .  
  
 BPREQI\_PROGRAM  
 Inizializzare\/utilizzare il campo di `pProgram` della struttura di `BP_REQUEST_INFO2` o di `BP_REQUEST_INFO` .  
  
 BPREQI\_PROGRAMNAME  
 Inizializzare\/utilizzare il campo di `bstrProgramName` della struttura di `BP_REQUEST_INFO2` o di `BP_REQUEST_INFO` .  
  
 BPREQI\_THREAD  
 Inizializzare\/utilizzare il campo di `pThread` della struttura di `BP_REQUEST_INFO2` o di `BP_REQUEST_INFO` .  
  
 BPREQI\_THREADNAME  
 Inizializzare\/utilizzare il campo di `bstrThreadName` della struttura di `BP_REQUEST_INFO2` o di `BP_REQUEST_INFO` .  
  
 BPREQI\_PASSCOUNT  
 Inizializzare\/utilizzare il campo di `bpPassCount` della struttura di `BP_REQUEST_INFO2` o di `BP_REQUEST_INFO` .  
  
 BPREQI\_CONDITION  
 Inizializzare\/utilizzare il campo di `bpCondition` \(condizione del punto di interruzione\) della struttura di `BP_REQUEST_INFO2` o di `BP_REQUEST_INFO` .  
  
 BPREQI\_FLAGS  
 Inizializzare\/utilizzare il campo di `dwFlags` della struttura di `BP_REQUEST_INFO2` o di `BP_REQUEST_INFO` .  
  
 BPREQI\_ALLOLDFIELDS  
 Inizializzare\/utilizzare tutti i campi della struttura di `BP_REQUEST_INFO` .  
  
 BPREQI\_VENDOR  
 Inizializzare\/utilizzare il campo di `guidVendor` della struttura di `BP_REQUEST_INFO2` .  
  
 BPREQI\_CONSTRAINT  
 Inizializzare\/utilizzare il campo di `bstrConstraint` della struttura di `BP_REQUEST_INFO2` .  
  
 BPREQI\_TRACEPOINT  
 Inizializzare\/utilizzare il campo di `bstrTracepoint` della struttura di `BP_REQUEST_INFO2` .  
  
 BPREQI\_ALLFIELDS  
 Specifica tutti i campi della struttura di `BP_REQUEST_INFO2` .  
  
## Note  
 Passato come argomento [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md) ai metodi [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md) e per specificare i campi di [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md) e [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) struttura deve essere inizializzato.  
  
 Questi flag vengono inoltre utilizzati per indicare i campi di strutture di `BP_REQUEST_INFO2` e di `BP_REQUEST_INFO` vengono utilizzati e validi a ogni struttura viene restituita.  
  
 Questi valori possono essere combinate con `OR`bit per bit.  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)   
 [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)