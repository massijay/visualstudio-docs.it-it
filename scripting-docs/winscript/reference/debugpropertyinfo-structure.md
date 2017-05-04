---
title: "Struttura DebugPropertyInfo | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: DebugPropertyInfo
apilocation: scrobj.dll
helpviewer_keywords: 
  - "Struttura DebugPropertyInfo"
ms.assetid: 3246efbc-c212-4024-8f07-6414c2f85e75
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Struttura DebugPropertyInfo
Viene descritto un oggetto di una natura gerarchica con il nome, il tipo e il valore.  Viene utilizzata per descrivere le proprietà di debug delle variabili locali, parametri, variabili ed espressioni di controllo e registri.  
  
## Sintassi  
  
```  
typedef struct DebugPropertyInfo{  
   DBGPROP_INFO_FLAGS  dwValidFields;  
   BSTR  bstrName;  
   BSTR  bstrType;  
   BSTR  bstrValue;  
   BSTR  bstrFullName;  
   DBGPROP_ATTRIB_FLAGS  dwAttrib;  
   IDebugProperty*  pDebugProp;  
};  
```  
  
## Membri  
 dwValidFields  
 Un tipo di dati enumerato utilizzato per specificare quali campi vengono inizializzati.  
  
 bstrName  
 Il nome della proprietà all'interno di un contesto.  
  
 bstrType  
 Il tipo di proprietà, come stringa formattata.  
  
 bstrValue  
 Il valore della proprietà, come stringa formattata.  
  
 bstrFullName  
 Il nome completo della proprietà.  
  
 dwAttrib  
 Enumerazione che specifica i flag per la proprietà di debug attributi.  
  
 pDebugProp  
 `IDebugProperty` descritto le informazioni contenute in questa struttura `DebugPropertyInfo`.  
  
## Vedere anche  
 [Interfaccia IDebugProperty](../../winscript/reference/idebugproperty-interface.md)   
 [DBGPROP\_ATTRIB\_FLAGS](../../winscript/reference/dbgprop-attrib-flags.md)   
 [DBGPROP\_INFO\_FLAGS](../../winscript/reference/dbgprop-info-flags.md)