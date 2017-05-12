---
title: "Metodo IJsDebugDataTarget::ReadMemory | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugDataTarget.ReadMemory
apilocation: jscript9diag.dll
ms.assetid: 664e0f7d-2007-45f4-b993-36fe8b1944e5
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Metodo IJsDebugDataTarget::ReadMemory
Legge la memoria del processo di destinazione.  
  
## Sintassi  
  
```  
HRESULT ReadMemory(  
   UINT64 address,  
   JsDebugReadMemoryFlags flags,  
   BYTE *pBuffer,  
   DWORD size,  
   DWORD *pBytesRead  
);  
```  
  
#### Parametri  
 `address`  
 \[in\] Indirizzo di base da cui leggere la memoria del processo di destinazione.  
  
 `flags`  
 \[in\] Flag che controllano il comportamento di ReadMemory.  
  
 `pBuffer`  
 \[out\] Buffer che riceve il contenuto dallo spazio degli indirizzi del processo di destinazione.  In caso di errore, il contenuto del buffer non è specificato.  
  
 `size`  
 \[in\] Numero di byte da leggere dal processo.  
  
 `pBytesRead`  
 \[out\] Indica il numero di byte letti dal processo di destinazione.  Se JsDebugAllowPartialRead non è specificato, in caso di esito positivo questo valore sarà sempre uguale alla dimensione di input.  Se JsDebugAllowPartialRead viene specificato, in caso di esito positivo questo valore sarà maggiore di zero.  
  
## Valore restituito  
  
## Note  
 Restituisce S\_OK se l'esito è positivo e i codici di errore vengono utilizzati per qualsiasi errore.  Restituisce E\_JsDEBUG\_INVALID\_MEMORY\_ADDRESS se l'indirizzo non è valido.  Per ulteriori informazioni, vedere JsDebugAllowPartialRead.  
  
## Requisiti  
 **Intestazione:** jscript9diag.h  
  
## Vedere anche  
 [Interfaccia IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)