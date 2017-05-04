---
title: "IDebugDocumentInfo::GetName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentInfo.GetName
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentInfo::GetName"
ms.assetid: c25d73da-99b6-4c9f-82af-182b4853f81c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentInfo::GetName
Restituisce il nome specificato di documento.  
  
## Sintassi  
  
```  
HRESULT GetName(  
   DOCUMENTNAMETYPE  dnt,  
   BSTR*             pbstrName  
);  
```  
  
#### Parametri  
 `dnt`  
 \[in\] tipo di nome documento da restituire.  
  
 `pbstrName`  
 \[out\] stringa contenente il nome.  
  
## Valore restituito  
 Il metodo restituisce un tipo `HRESULT`.  I valori possibili sono, ma non sono limitati a, quelli nella tabella seguente.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
|`E_FAIL`|Il nome specificato di documento non è noto.|  
  
## Note  
 Questo metodo restituisce il nome specificato di documento.  
  
## Vedere anche  
 [Interfaccia IDebugDocumentInfo](../../winscript/reference/idebugdocumentinfo-interface.md)   
 [Enumerazione DOCUMENTNAMETYPE](../../winscript/reference/documentnametype-enumeration.md)