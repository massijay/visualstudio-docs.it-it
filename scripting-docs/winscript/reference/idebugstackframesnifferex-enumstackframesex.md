---
title: "IDebugStackFrameSnifferEx::EnumStackFramesEx | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugStackFrameSnifferEx.EnumStackFramesEx
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugStackFrameSnifferEx::EnumStackFramesEx"
ms.assetid: b656b581-aff0-4984-8d8a-a1c7a8e6558a
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugStackFrameSnifferEx::EnumStackFramesEx
Restituisce un enumeratore stack frame del thread corrente.  
  
## Sintassi  
  
```  
HRESULT EnumStackFramesEx(  
   DWORD_PTR                dwSpMin,  
   IEnumDebugStackFrames**  ppedsf  
);  
```  
  
#### Parametri  
 `dwSpMin`  
 \[in\] il limite inferiore di indirizzi per l'enumerazione degli stack frame.  
  
 `ppedsf`  
 \[out\] enumeratore stack frame del thread corrente.  
  
## Valore restituito  
 Il metodo restituisce un tipo `HRESULT`.  I valori possibili sono, ma non sono limitati a, quelli nella tabella seguente.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## Note  
 L'enumeratore lo stack frame e restituisce i frame che inizia all'inizio dello stack, con il frame recentemente premuto.  L'enumeratore contiene solo gli stack frame con gli indirizzi maggiore o uguale a `dwSpMin`.  
  
## Vedere anche  
 [Interfaccia IDebugStackFrameSnifferEx](../../winscript/reference/idebugstackframesnifferex-interface.md)