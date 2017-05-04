---
title: "Metodo IJsDebugDataTarget::GetTlsValue | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugDataTarget.GetTlsValue
apilocation: jscript9diag.dll
ms.assetid: db575be9-7b24-45c5-9008-e4f2f76d6757
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Metodo IJsDebugDataTarget::GetTlsValue
Per il thread in fase di debug, recupera il valore nello slot dell'archiviazione locale del thread \(TLS\) per l'indice TLS specificato.  
  
## Sintassi  
  
```  
HRESULT GetTlsValue(  
   DWORD threadId,  
   UINT32 tlsIndex,  
   UINT64 *pValue  
);  
```  
  
#### Parametri  
 `threadId`  
 \[in\] Thread in esecuzione nel processo di destinazione da cui leggere.  
  
 `tlsIndex`  
 \[in\] Indice TLS che è stato allocato quando il processo di destinazione ha chiamato la funzione TlsAlloc.  
  
 `pValue`  
 \[out\] Valore della dimensione del puntatore che è stato archiviato nello slot di TLS del thread.  Se il thread di destinazione è 32 bit, i 32 bit superiori di questo valore saranno pari a zero.  
  
## Valore restituito  
  
## Note  
 Ogni thread di un processo dispone del relativo slot per ciascun indice TLS.  
  
## Requisiti  
 **Intestazione:** jscript9diag.h  
  
## Vedere anche  
 [Interfaccia IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)