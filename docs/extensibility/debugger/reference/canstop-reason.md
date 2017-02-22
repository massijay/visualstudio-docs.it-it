---
title: "CANSTOP_REASON | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CANSTOP_REASON"
helpviewer_keywords: 
  - "Enumerazione CANSTOP_REASON"
ms.assetid: 6da944eb-36cd-4a8c-8d71-544c775cfcc1
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# CANSTOP_REASON
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Utilizzato per determinare se un programma può interrompere l'esecuzione dopo il raggiungimento di un punto specifico nell'esecuzione.  
  
## Sintassi  
  
```cpp#  
enum enum_CANSTOP_REASON {   
   CANSTOP_ENTRYPOINT = 0x0000,  
   CANSTOP_STEPIN     = 0x0001  
};  
typedef DWORD CANSTOP_REASON;  
```  
  
```c#  
public enum enum_CANSTOP_REASON {   
   CANSTOP_ENTRYPOINT = 0x0000,  
   CANSTOP_STEPIN     = 0x0001  
};  
```  
  
## Membri  
 CANSTOP\_ENTRYPOINT  
 Specifica il punto di ingresso del programma specificato.  
  
 CANSTOP\_STEPIN  
 Specifica l'esecuzione di una funzione.  
  
## Note  
 Passato come argomento [GetReason](../Topic/IDebugCanStopEvent2::GetReason.md) al metodo per verificare con l'amministratore \(SDM\) di Debug della sessione se è corretto interrotti dopo il raggiungimento di un punto di ingresso del programma o dopo una funzione o un metodo.  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetReason](../Topic/IDebugCanStopEvent2::GetReason.md)