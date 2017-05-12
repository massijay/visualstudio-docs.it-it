---
title: "IScriptEntry::GetText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptEntry.GetText
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptEntry::GetText"
ms.assetid: 105b8244-1972-4b39-ac18-965f1f345ef2
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IScriptEntry::GetText
Restituisce il testo che corrisponde al blocco di script `IScriptEntry`, o il codice sorgente contenuto nel gestore eventi `IScriptScriptlet`.  
  
## Sintassi  
  
```  
HRESULT GetText(  
   BSTR               *pbstr  
);  
```  
  
#### Parametri  
 `pbstr`  
 \[out\] il testo nel blocco di script `IScriptEntry`, o il codice sorgente contenuto nel gestore eventi `IScriptScriptlet`.  
  
## Valore restituito  
 Oggetto `HRESULT`.  I valori possibili sono, ma non sono limitati a, quelli nella tabella seguente.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## Note  
  
## Vedere anche  
 [Interfaccia IScriptEntry](../../winscript/reference/iscriptentry-interface.md)