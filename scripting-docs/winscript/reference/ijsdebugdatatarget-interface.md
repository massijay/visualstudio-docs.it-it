---
title: "Interfaccia IJsDebugDataTarget | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: a9b784d6-958f-4d55-b3f6-c2d6b260a16b
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Interfaccia IJsDebugDataTarget
Viene implementata dal debugger per fornire la funzionalità per accedere e modificare lo stato del processo di destinazione del debugger.  
  
## Sintassi  
  
```  
IJsDebugDataTarget : public IUnknown;  
```  
  
## Membri  
  
### Metodi pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[Metodo IJsDebugDataTarget::AllocateVirtualMemory](../../winscript/reference/ijsdebugdatatarget-allocatevirtualmemory-method.md)|Riserva e\/o impegna un'area di memoria all'interno dello spazio degli indirizzi virtuale del processo di destinazione.|  
|[Metodo IJsDebugDataTarget::CreateStackFrameEnumerator](../../winscript/reference/ijsdebugdatatarget-createstackframeenumerator-method.md)|Crea un enumeratore per gli stack frame.|  
|[Metodo IJsDebugDataTarget::FreeVirtualMemory](../../winscript/reference/ijsdebugdatatarget-freevirtualmemory-method.md)|Rilascia e\/o libera un'area di memoria all'interno dello spazio degli indirizzi virtuale del processo di destinazione.|  
|[Metodo IJsDebugDataTarget::GetThreadContext](../../winscript/reference/ijsdebugdatatarget-getthreadcontext-method.md)|Recupera il contesto del thread specificato.|  
|[Metodo IJsDebugDataTarget::GetTlsValue](../../winscript/reference/ijsdebugdatatarget-gettlsvalue-method.md)|Per il thread in fase di debug, recupera il valore nello slot dell'archiviazione locale del thread \(TLS\) per l'indice TLS specificato.|  
|[Metodo IJsDebugDataTarget::ReadBSTR](../../winscript/reference/ijsdebugdatatarget-readbstr-method.md)|Legge una stringa BSTR dalla destinazione del debug.|  
|[Metodo IJsDebugDataTarget::ReadMemory](../../winscript/reference/ijsdebugdatatarget-readmemory-method.md)|Legge la memoria del processo di destinazione.|  
|[Metodo IJsDebugDataTarget::ReadNullTerminatedString](../../winscript/reference/ijsdebugdatatarget-readnullterminatedstring-method.md)|Legge il numero di caratteri specificato dalla destinazione.|  
|[Metodo IJsDebugDataTarget::WriteMemory](../../winscript/reference/ijsdebugdatatarget-writememory-method.md)|Legge la memoria del processo di destinazione.|  
  
## Requisiti  
 **Intestazione:** jscript9diag.h  
  
## Vedere anche  
 [Riferimenti interfacce Windows Script](../../winscript/reference/windows-script-interfaces-reference.md)