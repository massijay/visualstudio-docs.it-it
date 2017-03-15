---
title: "StackFrameTypeEnum | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "StackFrameTypeEnum (enumerazione)"
ms.assetid: 61e40163-eee0-4c1f-af47-cef3771bdc41
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# StackFrameTypeEnum
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

specifica il tipo di stack frame.  
  
## Sintassi  
  
```cpp  
enum StackFrameTypeEnum {  
   FrameTypeFPO,  
   FrameTypeTrap,  
   FrameTypeTSS,  
   FrameTypeStandard,  
   FrameTypeFrameData,  
   FrameTypeUnknown = -1  
};  
```  
  
## Elementi  
 `FrameTypeFPO`  
 Puntatore ai frame omesso, Informazioni aggiornate dell'omissione dei puntatori.  
  
 `FrameTypeTrap`  
 Il frame tuttavia del kernel.  
  
 `FrameTypeTSS`  
 Il frame tuttavia del kernel.  
  
 `FrameTypeStandard`  
 Stack frame standard di EBP.  
  
 `FrameTypeFrameData`  
 Puntatore ai frame omesso, Informazioni aggiornate di dati della pagina.  
  
 `FrameTypeUnknown`  
 Pagina che non dispone di alcune informazioni di debug.  
  
## Note  
 I valori in questa enumerazione restituiti da una chiamata a [IDiaStackFrame::get\_type](../../debugger/debug-interface-access/idiastackframe-get-type.md) metodo.  
  
## Requisiti  
 intestazione: cvconst.h  
  
## Vedere anche  
 [Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaStackFrame::get\_type](../../debugger/debug-interface-access/idiastackframe-get-type.md)