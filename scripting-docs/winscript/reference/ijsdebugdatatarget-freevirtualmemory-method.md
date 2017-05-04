---
title: "Metodo IJsDebugDataTarget::FreeVirtualMemory | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugDataTarget.FreeVirtualMemory
apilocation: jscript9diag.dll
ms.assetid: ea54bad3-9ae3-436b-974d-70fc7fffefd6
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Metodo IJsDebugDataTarget::FreeVirtualMemory
Rilascia e\/o libera un'area di memoria all'interno dello spazio degli indirizzi virtuale del processo di destinazione.  
  
## Sintassi  
  
```  
HRESULT FreeVirtualMemory(  
   UINT64 address,  
   DWORD size,  
   DWORD freeType  
);  
```  
  
#### Parametri  
 `address`  
 \[in\] Indirizzo nel processo di destinazione in cui la memoria dovrebbe essere liberata.  
  
 `size`  
 \[in\] Numero di byte da liberare.  Per rilasciare un'area della memoria, questo valore deve essere zero.  
  
 `freeType`  
 \[in\] Indica il tipo di operazione da eseguire per liberare spazio.  In genere è MEM\_RELEASE \(0x8000\), che rilascia l'area di pagine specificata.  Dopo l'operazione le pagine sono in stato libero.  È possibile utilizzare MEM\_DECOMMIT \(0x4000\) anziché liberare le pagine senza rilasciarle.  
  
## Valore restituito  
  
## Note  
 Per ulteriori informazioni, vedere l'API Win32 VirtualFree.  
  
## Requisiti  
 **Intestazione:** jscript9diag.h  
  
## Vedere anche  
 [Interfaccia IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)