---
title: "IActiveScriptAuthor::GetChars | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthor.GetChars
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthor::GetChars"
ms.assetid: a73ba263-12f7-4d5f-b4c8-9ad7e2d5d3cb
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# IActiveScriptAuthor::GetChars
Restituisce il set di caratteri di completamento di un contesto di completamento richiesto.  
  
## Sintassi  
  
```  
HRESULT GetChars(  
   DWORD            fRequestedList,  
   BSTR             *pbstrChars  
);  
```  
  
#### Parametri  
 `fRequestedList`  
 \[in\] il contesto di completamento richiesto.  
  
|Costante|Valore|Descrizione|  
|--------------|------------|-----------------|  
|SCRIPT\_CMPL\_ENUM\_TRIGGER|0x0001|Richiede l'enumerazione di sinistra.|  
|SCRIPT\_CMPL\_MEMBER\_TRIGGER|0x0002|È necessario il contesto di completamento del membro.|  
|SCRIPT\_CMPL\_PARAM\_TRIGGER|0x0003|Richiede un elenco di parametri.|  
|SCRIPT\_CMPL\_COMMIT|0x0004|Richiede il completamento dell'elenco di parametri.|  
  
 `pbstrChars`  
 \[out\] i caratteri corrispondenti al contesto di completamento richiesto.  
  
|Parametro `fRequestedList`.|Caratteri restituiti|  
|---------------------------------|--------------------------|  
|SCRIPT\_CMPL\_ENUM\_TRIGGER|"."|  
|SCRIPT\_CMPL\_MEMBER\_TRIGGER|"\="|  
|SCRIPT\_CMPL\_PARAM\_TRIGGER|\(","|  
|SCRIPT\_CMPL\_COMMIT|"\(\)"|  
  
## Valore restituito  
 Oggetto `HRESULT`.  I valori possibili sono, ma non sono limitati a, quelli nella tabella seguente.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## Note  
  
## Vedere anche  
 [Interfaccia IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)