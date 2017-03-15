---
title: "DISASSEMBLY_STREAM_SCOPE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DISASSEMBLY_STREAM_SCOPE"
helpviewer_keywords: 
  - "Enumerazione DISASSEMBLY_STREAM_SCOPE"
ms.assetid: 43e2b364-cbbe-4755-a7e6-a03f3054c965
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# DISASSEMBLY_STREAM_SCOPE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Specifica l'ambito del flusso di disassembly.  
  
## Sintassi  
  
```cpp#  
enum enum_DISASSEMBLY_STREAM_SCOPE {   
   DSS_HUGE     = 0x10000000,  
   DSS_FUNCTION = 0x0001,  
   DSS_MODULE   = (DSS_HUGE) | 0x0002,  
   DSS_ALL      = (DSS_HUGE) | 0x0003  
};  
typedef DWORD DISASSEMBLY_STREAM_SCOPE;  
```  
  
```c#  
public enum enum_DISASSEMBLY_STREAM_SCOPE {   
   DSS_HUGE     = 0x10000000,  
   DSS_FUNCTION = 0x0001,  
   DSS_MODULE   = (DSS_HUGE) | 0x0002,  
   DSS_ALL      = (DSS_HUGE) | 0x0003  
};  
```  
  
## Membri  
 DSS\_HUGE  
 Specifica che smonta il contesto di codice sarebbe stato restituito di un client in genere desidererebbe per recuperare in un'unica chiamata.  
  
 DSS\_FUNCTION  
 Specifica che la funzione contenuta dal contesto di codice dovrebbe essere smontata.  Specifica che il flusso di disassembly rappresenta una funzione, una volta restituito dal [GetScope](../Topic/IDebugDisassemblyStream2::GetScope.md) metodo.  
  
 DSS\_MODULE  
 Una volta restituito dal metodo di `IDebugDisassemblyStream2::GetScope` , specifica che il flusso di disassembly rappresenta un modulo.  
  
 DSS\_ALL  
 Specifica il disassembly per l'intero spazio degli indirizzi.  
  
## Note  
 Passato come argomento [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md) al metodo e restituito dal [GetScope](../Topic/IDebugDisassemblyStream2::GetScope.md) metodo.  
  
 Questi valori possono essere combinate con `OR`bit per bit.  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)   
 [GetScope](../Topic/IDebugDisassemblyStream2::GetScope.md)