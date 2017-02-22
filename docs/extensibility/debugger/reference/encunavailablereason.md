---
title: "EncUnavailableReason | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EncUnavailableReason"
helpviewer_keywords: 
  - "Enumerazione EncUnavailableReason"
ms.assetid: c10aa4c0-d7e0-4de1-b8ff-7e050985eb12
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# EncUnavailableReason
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

`This is for internal use only!` rappresenta le ragioni per cui **Modifica e continuazione** non è disponibile.  
  
## Sintassi  
  
```cpp#  
enum tagEncUnavailableReason {  
   ENCUN_NONE,  
   ENCUN_INTEROP,  
   ENCUN_SQLCLR,  
   ENCUN_MINIDUMP,  
   ENCUN_EMBEDDED,  
   ENCUN_ATTACH,  
   ENCUN_WIN64  
};  
typedef enum tagEncUnavailableReason EncUnavailableReason;  
```  
  
```c#  
public enum EncUnavailableReason {  
   ENCUN_NONE,  
   ENCUN_INTEROP,  
   ENCUN_SQLCLR,  
   ENCUN_MINIDUMP,  
   ENCUN_EMBEDDED,  
   ENCUN_ATTACH,  
   ENCUN_WIN64  
};  
```  
  
#### Parametri  
 ENCUN\_NONE  
 Nessuna motivo per cui specifica la Modifica e continuazione non è disponibile.  
  
 ENCUN\_INTEROP  
 In Modifica e continuazione non è disponibile durante la chiamata di interoperabilità.  
  
 ENCUN\_SQLCLR  
 In Modifica e continuazione non è disponibile durante la chiamata di routine SQL che utilizza Common Language \(CLR\) Runtime.  
  
 ENCUN\_MINIDUMP  
 In Modifica e continuazione non è disponibile durante l'elaborazione di un mini\-dump.  
  
 ENCUN\_EMBEDDED  
 In Modifica e continuazione non è disponibile quando elabora il codice incorporato.  
  
 ENCUN\_ATTACH  
 In Modifica e continuazione non è disponibile perché la sessione è stata associata a, non avviato da, il debugger.  
  
 ENCUN\_WIN64  
 In Modifica e continuazione non è disponibile durante l'elaborazione il codice Windows a 64 bit.  
  
## Note  
 Questa enumerazione è solo per utilizzo interno da [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)].  [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md) I metodi e [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md) come implementati da un fornitore di porte personalizzato deve sempre restituire `E_NOTIMPL`.  
  
## Requisiti  
 intestazione: msdbg.idl  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)   
 [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)