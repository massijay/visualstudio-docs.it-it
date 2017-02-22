---
title: "dwTYPE_KIND | Microsoft Docs"
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
  - "dwTYPE_KIND"
helpviewer_keywords: 
  - "Enumerazione dwTYPE_KIND"
ms.assetid: 6ff56b0f-c502-4e6c-9829-bfa05361b783
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# dwTYPE_KIND
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

specifica come interpretare il tipo [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) di oggetto.  
  
## Sintassi  
  
```cpp#  
enum enum_dwTYPE_KIND {  
   TYPE_KIND_METADATA = 0x0001,  
   TYPE_KIND_PDB      = 0x0002,  
   TYPE_KIND_BUILT    = 0x0003,  
};  
  
typedef DWORD dwTYPE_KIND;  
```  
  
```c#  
public enum enum_dwTYPE_KIND {  
   TYPE_KIND_METADATA = 0x0001,  
   TYPE_KIND_PDB      = 0x0002,  
   TYPE_KIND_BUILT    = 0x0003,  
};  
```  
  
#### Parametri  
 TYPE\_KIND\_METADATA  
 [TYPE\_INFO](../../../extensibility/debugger/reference/type-info.md) L'unione deve essere interpretata come [METADATA\_TYPE](../../../extensibility/debugger/reference/metadata-type.md) struttura.  
  
 TYPE\_KIND\_PDB  
 L'unione di `TYPE_INFO` deve essere interpretata come [PDB\_TYPE](../../../extensibility/debugger/reference/pdb-type.md) struttura.  
  
 TYPE\_KIND\_BUILT  
 L'unione di `TYPE_INFO` deve essere interpretata come [BUILT\_TYPE](../../../extensibility/debugger/reference/built-type.md) struttura.  
  
## Note  
 I valori dell'enumerazione vengono visualizzati nel campo di [TYPE\_INFO](../../../extensibility/debugger/reference/type-info.md)`dwKind` della struttura e vengono utilizzati per determinare come interpretare il membro di `type` .  La struttura di `TYPE_INFO` viene restituita da una chiamata [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md) al metodo.  
  
## Requisiti  
 intestazione: sh.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [TYPE\_INFO](../../../extensibility/debugger/reference/type-info.md)   
 [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)   
 [METADATA\_TYPE](../../../extensibility/debugger/reference/metadata-type.md)   
 [PDB\_TYPE](../../../extensibility/debugger/reference/pdb-type.md)   
 [BUILT\_TYPE](../../../extensibility/debugger/reference/built-type.md)