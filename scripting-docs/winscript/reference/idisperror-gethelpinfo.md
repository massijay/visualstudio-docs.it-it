---
title: "IDispError::GetHelpInfo | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispError.GetHelpInfo
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDispError::GetHelpInfo"
ms.assetid: a146df13-eda4-4e56-8bf0-cf9886a2150f
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDispError::GetHelpInfo
Restituisce il percorso del file della Guida e dell'ID del contesto dell'argomento che viene illustrato l'errore, se possibile.  
  
## Sintassi  
  
```  
HRESULT GetHelpInfo(  
   BSTR*  pbstrFileName,  
   DWORD*  pdwContext  
);  
```  
  
#### Parametri  
 `pbstrFileName`  
 \[out\] stringa contenente il percorso completo del file della Guida.  Se non esiste alcun file della Guida o si verifica un errore, il valore restituito è NULL.  
  
 `pdwContext`  
 \[out\] ID del contesto della guida dell'errore.  Se non esiste alcun file della Guida \(se `pbstrFileName` è NULL\), questo parametro non ha alcun significato.  
  
## Valore restituito  
 Il metodo restituisce un tipo `HRESULT`.  I valori possibili sono, ma non sono limitati a, quelli nella tabella seguente.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
|`E_FAIL`|Un errore specifico di provider si è verificato.|  
|`E_INVALIDARG`|`pbstrFileName` o `pdwContext` è NULL.|  
|`E_OUTOFMEMORY`|Il provider non è in grado di allocare memoria sufficiente in cui restituire il percorso del file della Guida.|  
  
## Note  
 Questo metodo restituisce il percorso del file della Guida e dell'ID del contesto dell'argomento che viene illustrato l'errore, se possibile.  
  
> [!NOTE]
>  Il metodo non è implementato.  
  
## Vedere anche  
 [Interfaccia IDispError](../../winscript/reference/idisperror-interface.md)