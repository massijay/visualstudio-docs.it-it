---
title: "Metodo IJsDebugDataTarget::AllocateVirtualMemory | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugDataTarget.AllocateVirtualMemory
apilocation: jscript9diag.dll
ms.assetid: 1d3a77b0-c1de-4a0c-a759-3e0c68fd96dd
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Metodo IJsDebugDataTarget::AllocateVirtualMemory
Riserva e\/o impegna un'area di memoria all'interno dello spazio degli indirizzi virtuale del processo di destinazione.  
  
## Sintassi  
  
```  
HRESULT AllocateVirtualMemory(  
   UINT64 address,  
   DWORD size,  
   DWORD allocationType,  
   DWORD pageProtection,  
   UINT64 *pAllocatedAddress  
);  
```  
  
#### Parametri  
 `address`  
 \[in\] Indirizzo nel processo di destinazione in cui la memoria dovrebbe essere sottoposta a commit o riservata.  Questo valore è in genere zero, nel qual caso il sistema sceglie un indirizzo.  
  
 `size`  
 \[in\] Dimensione dell'area di memoria da allocare, in byte.  Verrà eseguito un arrotondamento automatico fino al bordo della pagina successiva.  
  
 `allocationType`  
 \[in\] Indica il tipo di allocazione da eseguire.  In genere è MEM\_COMMIT &#124; MEM\_RESERVE \(0x3000\) che riserva e impegna un'allocazione in una sola operazione.  
  
 `pageProtection`  
 \[in\] Protezione della memoria per l'area di pagine da allocare.  Se viene eseguito il commit delle pagine, è possibile specificare una delle costanti di protezione della memoria, ad esempio PAGE\_READWRITE, PAGE\_EXECUTE\).  
  
 `pAllocatedAddress`  
 \[out\] Indirizzo di base dell'area allocata delle pagine.  
  
## Valore restituito  
  
## Note  
 La funzione inizializza la memoria che assegna a zero, a meno che non sia utilizzato MEM\_RESET.  Per ulteriori informazioni, vedere l'API Win32 VirtualAlloc.  
  
## Requisiti  
 **Intestazione:** jscript9diag.h  
  
## Vedere anche  
 [Interfaccia IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)