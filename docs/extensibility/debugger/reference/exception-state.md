---
title: "EXCEPTION_STATE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EXCEPTION_STATE"
helpviewer_keywords: 
  - "Enumerazione EXCEPTION_STATE"
ms.assetid: 597f4f4c-9b70-485c-b5dc-3c2e3aecc664
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# EXCEPTION_STATE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Specifica lo stato dell'eccezione.  
  
## Sintassi  
  
```cpp#  
enum enum_EXCEPTION_STATE {   
   EXCEPTION_NONE                          = 0x0000,  
   EXCEPTION_STOP_FIRST_CHANCE             = 0x0001,  
   EXCEPTION_STOP_SECOND_CHANCE            = 0x0002,  
   EXCEPTION_STOP_USER_FIRST_CHANCE        = 0x0010,  
   EXCEPTION_STOP_USER_UNCAUGHT            = 0x0020,  
   EXCEPTION_STOP_ALL                      = 0x00FF,  
   EXCEPTION_CANNOT_BE_CONTINUED           = 0x0100,  
  
   // These are for exception types only  
   EXCEPTION_CODE_SUPPORTED                = 0x1000,  
   EXCEPTION_CODE_DISPLAY_IN_HEX           = 0x2000,  
   EXCEPTION_JUST_MY_CODE_SUPPORTED        = 0x4000,  
   EXCEPTION_MANAGED_DEBUG_ASSISTANT       = 0x8000,  
  
   // These are no longer used  
   EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT      = 0x0004,  
   EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT     = 0x0008,  
   EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT = 0x0040,  
   EXCEPTION_STOP_USER_UNCAUGHT_USE_PARENT     = 0x0080,  
};  
typedef DWORD EXCEPTION_STATE;  
```  
  
```c#  
public enum enum_EXCEPTION_STATE {   
   EXCEPTION_NONE                          = 0x0000,  
   EXCEPTION_STOP_FIRST_CHANCE             = 0x0001,  
   EXCEPTION_STOP_SECOND_CHANCE            = 0x0002,  
   EXCEPTION_STOP_USER_FIRST_CHANCE        = 0x0010,  
   EXCEPTION_STOP_USER_UNCAUGHT            = 0x0020,  
   EXCEPTION_STOP_ALL                      = 0x00FF,  
   EXCEPTION_CANNOT_BE_CONTINUED           = 0x0100,  
  
   // These are for exception types only  
   EXCEPTION_CODE_SUPPORTED                = 0x1000,  
   EXCEPTION_CODE_DISPLAY_IN_HEX           = 0x2000,  
   EXCEPTION_JUST_MY_CODE_SUPPORTED        = 0x4000,  
   EXCEPTION_MANAGED_DEBUG_ASSISTANT       = 0x8000,  
  
   // These are no longer used  
   EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT      = 0x0004,  
   EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT     = 0x0008,  
   EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT = 0x0040,  
   EXCEPTION_STOP_USER_UNCAUGHT_USE_PARENT     = 0x0080,  
};  
```  
  
## Membri  
 EXCEPTION\_NONE  
 Non arrestarsi l'eccezione.  
  
 EXCEPTION\_STOP\_FIRST\_CHANCE  
 L'arresto di primo infornamento dell'eccezione.  In descrivere un evento di eccezione, questo flag indica che l'evento dell'eccezione è un evento di eccezioni first\-chance.  
  
 EXCEPTION\_STOP\_SECOND\_CHANCE  
 Interruzione su come infornamento dell'eccezione.  In descrivere un evento di eccezione, indica che l'evento dell'eccezione è un evento second\-chance di eccezione.  
  
 EXCEPTION\_STOP\_USER\_FIRST\_CHANCE  
 Interruzione alla prima infornamento di un'eccezione in modalità utente.  In descrivere un evento di eccezione, indica che l'evento dell'eccezione è un evento di eccezione utente di eccezioni first\-chance.  
  
 EXCEPTION\_STOP\_USER\_UNCAUGHT  
 Interrompere l'esecuzione quando un'eccezione in modalità utente non viene intercettata.  In descrivere un evento di eccezione, indica che l'evento dell'eccezione è un evento non intercettata di eccezione in modalità utente.  
  
 EXCEPTION\_STOP\_ALL  
 interruzione su qualsiasi eccezione.  Non utilizzato quando viene descritto un evento di eccezione.  
  
 \_BE\_CONTINUED OF EXCEPTION\_CAN NOT  
 In descrivere un evento di eccezione, indica che l'eccezione non è possibile continuare da.  
  
 EXCEPTION\_CODE\_SUPPORTED  
 Indica che l'eccezione contiene codice che lo supporta.  Utilizzato per la visualizzazione dell'eccezione  
  
 EXCEPTION\_CODE\_DISPLAY\_IN\_HEX  
 Indica che il codice dell'eccezione deve essere visualizzato in.  Utilizzato per la visualizzazione dell'eccezione.  
  
 EXCEPTION\_JUST\_MY\_CODE\_SUPPORTED  
 Indica che il codice dell'eccezione supporta JustMyCode.  Utilizzato per la visualizzazione dell'eccezione.  
  
 EXCEPTION\_MANAGED\_DEBUG\_ASSISTANT  
 Indica che il debugger di codice gestito deve gestire le eccezioni.  Se non impostata, il debugger predefinito gestisce le eccezioni.  Ciò viene passata [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md) al metodo e non viene [EXCEPTION\_INFO](../../../extensibility/debugger/reference/exception-info.md) utilizzata nella struttura.  
  
 EXCEPTION\_STOP\_FIRST\_CHANCE\_USE\_PARENT  
 OBSOLETO, NOT UTILIZZARE.  
  
 EXCEPTION\_STOP\_SECOND\_CHANCE\_USE\_PARENT  
 OBSOLETO, NOT UTILIZZARE.  
  
 EXCEPTION\_STOP\_USER\_FIRST\_CHANCE\_USE\_PARENT  
 OBSOLETO, NOT UTILIZZARE.  
  
 EXCEPTION\_STOP\_USER\_SECOND\_CHANCE\_USE\_PARENT  
 OBSOLETO, NOT UTILIZZARE.  
  
## Note  
 Utilizzato come membro di `dwState` [EXCEPTION\_INFO](../../../extensibility/debugger/reference/exception-info.md) della struttura per indicare lo stato dell'eccezione e le operazioni che è possibile eseguire a questo argomento.  
  
 Questi valori vengono passati [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md) al metodo per impostare lo stato di tutte le eccezioni.  
  
 Questi flag possono essere combinati con un OR bit per bit.  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [EXCEPTION\_INFO](../../../extensibility/debugger/reference/exception-info.md)   
 [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)