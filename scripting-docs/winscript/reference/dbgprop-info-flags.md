---
title: "DBGPROP_INFO_FLAGS | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: DBGPROP_INFO_FLAGS
apilocation: scrobj.dll
f1_keywords: 
  - "DBGPROP_INFO_FLAGS"
helpviewer_keywords: 
  - "DBGPROP_INFO_FLAGS"
ms.assetid: e9450a21-a802-4c3e-8b3d-8e202f555de1
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# DBGPROP_INFO_FLAGS
Utilizzata per specificare i campi `DebugPropertyInfo`  
  
## Sintassi  
  
```  
enum {  
   DBGPROP_INFO_NAME  =0x001,  
   DBGPROP_INFO_TYPE  =0x002,  
   DBGPROP_INFO_VALUE  =0x004,  
   DBGPROP_INFO_FULLNAME  =0x020,  
   DBGPROP_INFO_ATTRIBUTES  =0x008,  
   DBGPROP_INFO_DEBUGPROP  =0x010,  
   DBGPROP_INFO_AUTOEXPAND  =0x8000000  
};  
```  
  
## Membri  
 DBGPROP\_INFORMATION\_NAME  
 Inizializza il campo `bstrName`.  
  
 DBGPROP\_INFORMATION\_TYPE  
 Inizializza il campo `bstrType`.  
  
 DBGPROP\_INFORMATION\_VALUE  
 Inizializza il campo `bstrValue`.  
  
 DBGPROP\_INFORMATION\_FULLNAME  
 Inizializza il campo `bstrFullName`.  
  
 DBGPROP\_INFORMATION\_ATTRIBUTES  
 Inizializza il campo `dwAttrib`.  
  
 DBGPROP\_INFORMATION\_DEBUGPROP  
 Inizializza il campo `pDebugProp` contenente un'interfaccia `IDebugProperty`.  
  
 DBGPROP\_INFORMATION\_AUTOEXPAND  
 Specifica che il campo di valore deve contenere il valore automaticamente espanso, se disponibile, per questo tipo di oggetto.  
  
## Vedere anche  
 [Struttura DebugPropertyInfo](../../winscript/reference/debugpropertyinfo-structure.md)   
 [Interfaccia IDebugProperty](../../winscript/reference/idebugproperty-interface.md)