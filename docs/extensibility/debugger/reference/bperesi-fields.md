---
title: "BPERESI_FIELDS | Microsoft Docs"
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
  - "BPERESI_FIELDS"
helpviewer_keywords: 
  - "Enumerazione BPERESI_FIELDS"
ms.assetid: dd7dd89c-1043-46a1-a929-099cc039c344
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# BPERESI_FIELDS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Specifica le informazioni da recuperare su una risoluzione non riuscita di un punto di interruzione.  
  
## Sintassi  
  
```cpp#  
enum enum_BPERESI_FIELDS {   
   PERESI_BPRESLOCATION = 0x0001,  
   BPERESI_PROGRAM      = 0x0002,  
   BPERESI_THREAD       = 0x0004,  
   BPERESI_MESSAGE      = 0x0008,  
   BPERESI_TYPE         = 0x0010,  
   BPERESI_ALLFIELDS    = 0xffffffff  
};  
typedef DWORD BPERESI_FIELDS;  
```  
  
```c#  
public enum enum_BPERESI_FIELDS {   
   PERESI_BPRESLOCATION = 0x0001,  
   BPERESI_PROGRAM      = 0x0002,  
   BPERESI_THREAD       = 0x0004,  
   BPERESI_MESSAGE      = 0x0008,  
   BPERESI_TYPE         = 0x0010,  
   BPERESI_ALLFIELDS    = 0xffffffff  
};  
```  
  
## Membri  
 PERESI\_BPRESLOCATION  
 Inizializzare\/utilizzare il campo di `bpResLocation` \(posizione di risoluzione del punto di interruzione\) [BP\_ERROR\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) della struttura.  
  
 BPERESI\_PROGRAM  
 Inizializzare\/utilizzare il campo di `pProgram` della struttura di `BP_ERROR_RESOLUTION_INFO` .  
  
 BPERESI\_THREAD  
 Inizializzare\/utilizzare il campo di `pThread` della struttura di `BP_ERROR_RESOLUTION_INFO` .  
  
 BPERESI\_MESSAGE  
 Inizializzare\/utilizzare il campo di `bstrMessage` della struttura di `BP_ERROR_RESOLUTION_INFO` .  
  
 BPERESI\_TYPE  
 Inizializzare\/utilizzare il campo di `dwType` \(tipo del punto di interruzione\) della struttura di `BP_ERROR_RESOLUTION_INFO` .  
  
 BPERESI\_ALLFIELDS  
 Inizializzare\/utilizza tutti i campi della struttura di `BP_ERROR_RESOLUTION_INFO` .  
  
## Note  
 Passato come parametro [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md) al metodo per indicare i campi [BP\_ERROR\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) della struttura devono essere inizializzati.  
  
 Questi valori vengono utilizzati per indicare i campi della struttura di `BP_ERROR_RESOLUTION_INFO` vengono utilizzati e validi a tale struttura viene restituita.  
  
 Questi valori possono essere combinate con `OR`bit per bit.  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP\_ERROR\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)   
 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)