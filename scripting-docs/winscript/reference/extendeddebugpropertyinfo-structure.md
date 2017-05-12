---
title: "Struttura ExtendedDebugPropertyInfo | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: ExtendedDebugPropertyInfo
apilocation: scrobj.dll
helpviewer_keywords: 
  - "Struttura ExtendedDebugPropertyInfo"
ms.assetid: f2cf6477-454b-4d13-95da-ae4c90daa175
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Struttura ExtendedDebugPropertyInfo
Estende la struttura `DebugPropertyInfo` con i membri aggiuntivi per una funzionalità della proprietà estesa.  
  
## Sintassi  
  
```  
typedef struct ExtendedDebugPropertyInfo{  
   DBGPROP_INFO_FLAGS  dwValidFields;  
   LPOLESTR  bstrName;  
   LPOLESTR  bstrType;  
   LPOLESTR  bstrValue;  
   LPOLESTR  bstrFullName;  
   DBGPROP_ATTRIB_FLAGS  dwAttrib;  
   IDebugProperty*  pDebugProp;  
   DWORD  nDISPID;  
   DWORD  nType;  
   VARIANT  varValue;  
   ILockBytes*  plbValue;  
   IDebugExtendedProperty*  pDebugExtProp;  
};  
```  
  
## Membri  
 `dwValidFields`  
 Un tipo di dati enumerato utilizzato per specificare quali campi vengono inizializzati.  
  
 `bstrName`  
 Il nome della proprietà all'interno di un contesto.  
  
 `bstrType`  
 Il tipo di proprietà come stringa formattata.  
  
 `bstrValue`  
 Il valore della proprietà come stringa formattata.  
  
 `bstrFullName`  
 Il nome completo della proprietà.  
  
 `dwAttrib`  
 Enumerazione che specifica i flag per la proprietà di debug attributi.  
  
 `pDebugProp`  
 Oggetto di`IDebugProperty` che corrisponde a questo `ExtendedDebugPropertyInfo`.  
  
 `nDISPID`  
 ID dispatch  
  
 `nType`  
 Il tipo di proprietà estesa.  
  
 `varValue`  
 Il valore di proprietà estesa se è in grado di adattarsi alla VARIANT.  
  
 `plbValue`  
 I byte di dati del valore della proprietà.  
  
 `pDebugExtProp`  
 Oggetto di`IDebugExtendedProperty` che corrisponde a questo `ExtendedDebugPropertyInfo`.  
  
## Vedere anche  
 [Struttura DebugPropertyInfo](../../winscript/reference/debugpropertyinfo-structure.md)   
 [Interfaccia IDebugProperty](../../winscript/reference/idebugproperty-interface.md)   
 [Interfaccia IDebugExtendedProperty](../../winscript/reference/idebugextendedproperty-interface.md)   
 [DBGPROP\_ATTRIB\_FLAGS](../../winscript/reference/dbgprop-attrib-flags.md)   
 [DBGPROP\_INFO\_FLAGS](../../winscript/reference/dbgprop-info-flags.md)