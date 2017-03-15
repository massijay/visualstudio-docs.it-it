---
title: "IDebugField::GetExtendedInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugField::GetExtendedInfo"
helpviewer_keywords: 
  - "Metodo IDebugField::GetExtendedInfo"
ms.assetid: 46c0dd4d-4fd5-4efd-a908-71e4248e8e8d
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugField::GetExtendedInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questo metodo recupera le informazioni estese su un campo.  
  
## Sintassi  
  
```cpp#  
HRESULT GetExtendedInfo(   
   REFGUID guidExtendedInfo,  
   BYTE**  prgBuffer,  
   DWORD*  pdwLen  
);  
```  
  
```c#  
int GetExtendedInfo(  
   ref Guid guidExtendedInfo,   
   IntPtr[] prgBuffer,   
   ref uint pdwLen  
);  
```  
  
#### Parametri  
 `guidExtendedInfo`  
 \[in\]  Selezionare le informazioni da restituire.  I valori validi sono:  
  
|Valore|Descrizione|  
|------------|-----------------|  
|`guidConstantValue`|il valore come sequenza di byte.|  
|`guidConstantType`|Il tipo come firma del tipo.|  
  
 `prgBuffer`  
 \[out\]  Restituisce informazioni estese.  
  
 `pdwLen`  
 \[in, out\]  Restituisce le dimensioni delle informazioni estese, in byte.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 Attualmente, questo metodo restituisce solo il tipo o il valore di costante.  Il chiamante deve liberare il buffer restituito in `prgBuffer` chiamando la funzione di `CoTaskMemFree` di COM \(C\+\+\) o <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> \(c\#\).  
  
## Vedere anche  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)