---
title: "Metodo IJsDebugDataTarget::WriteMemory | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugDataTarget.WriteMemory
apilocation: jscript9diag.dll
ms.assetid: 0d3c04c3-9ef8-4842-a145-3d29bca75062
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Metodo IJsDebugDataTarget::WriteMemory
Legge la memoria del processo di destinazione.  
  
## Sintassi  
  
```  
HRESULT WriteMemory(  
   UINT64 address,  
   const BYTE *pMemory,  
   DWORD size  
);  
```  
  
#### Parametri  
 `address`  
 \[in\] Indirizzo di base da cui scrivere nella memoria del processo di destinazione.  
  
 `pMemory`  
 \[in\] Dati da scrivere nello spazio degli indirizzi del processo specificato.  
  
 `size`  
 \[in\] Numero di byte da scrivere nel processo.  
  
## Valore restituito  
  
## Note  
 Prima di trasferire i dati, il sistema verifica che tutti i dati nell'indirizzo di base e in memoria della dimensione specificata siano accessibili per l'accesso in scrittura e se non sono accessibili, la funzione genera un errore E\_JsDEBUG\_INVALID\_MEMORY\_ADDRESS.  
  
## Requisiti  
 **Intestazione:** jscript9diag.h  
  
## Vedere anche  
 [Interfaccia IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)