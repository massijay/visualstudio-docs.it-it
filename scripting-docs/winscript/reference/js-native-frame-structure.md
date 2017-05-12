---
title: "Struttura JS_NATIVE_FRAME | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: JS_NATIVE_FRAME
apilocation: jscript9diag.dll
ms.assetid: 5afa2ee1-b3e2-47cb-b304-84f96e6fbb14
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Struttura JS_NATIVE_FRAME
Rappresenta uno stack frame.  
  
## Sintassi  
  
```  
typedef struct {  
    UINT64 InstructionOffset;  
    UINT64 ReturnOffset;  
    UINT64 FrameOffset;  
    UINT64 StackOffset;  
} JS_NATIVE_FRAME;  
```  
  
## Membri  
 `InstructionOffset`  
 Il puntatore all'istruzione.  
  
 `ReturnOffset`  
 L'indirizzo del mittente.  
  
 `FrameOffset`  
 Il puntatore al frame.  
  
 `StackOffset`  
 Il puntatore allo stack.  
  
## Note  
 Lo struct `JS_NATIVE_FRAME` è utilizzato dalla classe `IJsStackFrameEnumerator`.  
  
## Vedere anche  
 [Costanti, enumerazioni e strutture del debugger di script ActiveX](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)