---
title: "BUILT_TYPE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BUILT_TYPE"
helpviewer_keywords: 
  - "Struttura BUILT_TYPE"
ms.assetid: cc02c32c-0f65-4210-ad25-a9b1899066e8
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# BUILT_TYPE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questa struttura specifica le informazioni su un tipo di campo utilizzato dai metadati.  
  
## Sintassi  
  
```cpp#  
typedef struct _tagTYPE_BUILT {  
   ULONG32      ulAppDomainID;  
   GUID         guidModule;  
   IDebugField* pUnderlyingField;  
} BUILT_TYPE;  
```  
  
```c#  
public struct BUILT_TYPE {  
   public uint        ulAppDomainID;  
   public Guid        guidModule;  
   public IDebugField pUnderlyingField;  
};  
```  
  
#### Parametri  
 ulAppDomainID  
 ID dell'applicazione da cui il simbolo è stato acquistato.  Viene utilizzato per identificare in modo univoco un'istanza dell'applicazione.  
  
 guidModule  
 Il GUID del modulo che contiene questo campo.  
  
 pUnderlyingField  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) Un oggetto che identifica il campo sottostante associato a questo campo generato.  
  
## Note  
 Questa struttura viene visualizzata come parte dell'[TYPE\_INFO](../../../extensibility/debugger/reference/type-info.md) unione nella struttura quando il campo di `dwKind` della struttura di `TYPE_INFO` è impostato su `TYPE_KIND_BUILT` \(un valore [dwTYPE\_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) dell'enumerazione\).  
  
## Requisiti  
 intestazione: sh.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [TYPE\_INFO](../../../extensibility/debugger/reference/type-info.md)   
 [dwTYPE\_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)