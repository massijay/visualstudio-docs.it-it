---
title: "IDispError::GetSource | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispError.GetSource
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDispError::GetSource"
ms.assetid: 20def54c-a67c-4102-babf-6f0704e5fc5c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDispError::GetSource
Restituisce il ProgID dipendente dal linguaggio per la classe o l'applicazione che ha generato l'errore.  
  
## Sintassi  
  
```  
HRESULT GetSource(  
   BSTR*  pbstrSource  
);  
```  
  
#### Parametri  
 `pbstrSource`  
 \[out\] stringa contenente un ProgID, nel form `progname.objectname`.  
  
## Valore restituito  
 Il metodo restituisce un tipo `HRESULT`.  I valori possibili sono, ma non sono limitati a, quelli nella tabella seguente.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## Note  
 Questo metodo viene utilizzato per determinare la classe o dell'applicazione in cui si è verificata l'eccezione.  Il ProgID non può essere restituito nel linguaggio specificato dall'identificatore delle impostazioni locali \(LCID\) fornito al momento della chiamata.  
  
> [!NOTE]
>  Il metodo non è implementato.  
  
## Vedere anche  
 [Interfaccia IDispError](../../winscript/reference/idisperror-interface.md)