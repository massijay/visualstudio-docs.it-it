---
title: "MODULE_FLAGS | Microsoft Docs"
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
  - "MODULE_FLAGS"
helpviewer_keywords: 
  - "Enumerazione MODULE_FLAGS"
ms.assetid: 0e555b42-b846-4dbb-812e-8e3d11c85b2d
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# MODULE_FLAGS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

utilizzato per descrivere un modulo.  
  
## Sintassi  
  
```cpp#  
enum enum_MODULE_FLAGS {   
   MODULE_FLAG_NONE        = 0x0000,  
   MODULE_FLAG_SYSTEM      = 0x0001,  
   MODULE_FLAG_SYMBOLS     = 0x0002,  
   MODULE_FLAG_64BIT       = 0x0004,  
   MODULE_FLAG_OPTIMIZED   = 0x0008,  
   MODULE_FLAG_UNOPTIMIZED = 0x0010  
};  
typedef DWORD MODULE_FLAGS;  
```  
  
```c#  
public enum enum_MODULE_FLAGS {   
   MODULE_FLAG_NONE        = 0x0000,  
   MODULE_FLAG_SYSTEM      = 0x0001,  
   MODULE_FLAG_SYMBOLS     = 0x0002,  
   MODULE_FLAG_64BIT       = 0x0004,  
   MODULE_FLAG_OPTIMIZED   = 0x0008,  
   MODULE_FLAG_UNOPTIMIZED = 0x0010  
};  
```  
  
## Membri  
 MODULE\_FLAG\_NONE  
 non specifica modulo.  
  
 MODULE\_FLAG\_SYSTEM  
 specifica un modulo di sistema.  
  
 MODULE\_FLAG\_SYMBOLS  
 Specifica un modulo del simbolo.  
  
 MODULE\_FLAG\_64BIT  
 Specifica un modulo a 64 bit.  
  
 MODULE\_FLAG\_OPTIMIZED  
 specifica il modulo è stato ottimizzato.  Questo stato viene riprodotto nella finestra di **moduli** .  
  
 MODULE\_FLAG\_UNOPTIMIZED  
 specifica il modulo non è stato ottimizzato.  Questo stato viene riprodotto nella finestra di **moduli** .  Questo è lo stato predefinito.  
  
## Note  
 Utilizzato per il membro di `m_dwModuleFlags` [MODULE\_INFO](../../../extensibility/debugger/reference/module-info.md) della struttura.  
  
 Questi flag possono essere combinate con `OR`bit per bit.  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [MODULE\_INFO](../../../extensibility/debugger/reference/module-info.md)