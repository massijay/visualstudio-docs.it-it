---
title: "TYPE_INFO | Microsoft Docs"
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
  - "TYPE_INFO"
helpviewer_keywords: 
  - "Struttura TYPE_INFO"
ms.assetid: d725cb68-a565-49d1-a16f-ff0445c587a0
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# TYPE_INFO
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questa struttura specifica i vari tipi di informazioni su un tipo di campo.  
  
## Sintassi  
  
```cpp#  
struct _tagTYPE_INFO_UNION {  
   dwTYPE_KIND dwKind;  
   union {  
      METADATA_TYPE typeMeta;  
      PDB_TYPE      typePdb;  
      BUILT_TYPE    typeBuilt;  
      DWORD         unused;  
   } type;  
} TYPE_INFO;  
```  
  
```c#  
public struct TYPE_INFO {  
   public uint   dwKind;  
   public IntPtr unionmember;  
};  
```  
  
#### Parametri  
 dwKind  
 Un valore [dwTYPE\_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) dell'enumerazione che determina come interpretare l'unione.  
  
 type.typeMeta  
 \[C\+\+ solo\] contiene [METADATA\_TYPE](../../../extensibility/debugger/reference/metadata-type.md) una struttura se `dwKind` è `TYPE_KIND_METADATA`.  
  
 type.typePdb  
 \[C\+\+ solo\] contiene [PDB\_TYPE](../../../extensibility/debugger/reference/pdb-type.md) una struttura se `dwKind` è `TYPE_KIND_PDB`.  
  
 type.typeBuilt  
 \[C\+\+ solo\] contiene [BUILT\_TYPE](../../../extensibility/debugger/reference/built-type.md) una struttura se `dwKind` è `TYPE_KIND_BUILT`.  
  
 type.unused  
 riempimento inutilizzato.  
  
 type  
 Nome dell'unione.  
  
 unionmember  
 \[Solo c\#\] il marshalling questo al tipo appropriato della struttura basato su `dwKind`.  
  
## Note  
 Questa struttura viene passata [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md) al metodo in cui viene soddisfatta.  Come contenuto della struttura viene interpretato è basato sul campo di `dwKind` .  
  
> [!NOTE]
>  \[C\+\+ solo\] se `dwKind` equivale a `TYPE_KIND_BUILT`, è necessario rilasciare l'oggetto sottostante [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) quando si elimina la struttura di `TYPE_INFO` .  Questa operazione viene eseguita chiamando `typeInfo.type.typeBuilt.pUnderlyingField->Release()`.  
  
 \[Solo c\#\] illustrato nella tabella come interpretare il membro di `unionmember` per ogni tipo di elemento.  Nell'esempio viene illustrato come eseguire questa operazione per un tipo di elemento.  
  
|`dwKind`|`unionmember` interpretata come|  
|--------------|-------------------------------------|  
|`TYPE_KIND_METADATA`|[METADATA\_TYPE](../../../extensibility/debugger/reference/metadata-type.md)|  
|`TYPE_KIND_PDB`|[PDB\_TYPE](../../../extensibility/debugger/reference/pdb-type.md)|  
|`TYPE_KIND_BUILT`|[BUILT\_TYPE](../../../extensibility/debugger/reference/built-type.md)|  
  
## Esempio  
 In questo esempio viene illustrato come interpretare il membro di `unionmember` della struttura di `TYPE_INFO` in c\#.  Questo esempio mostra l'interpretazione di un solo tipo \(`TYPE_KIND_METADATA`\) ma gli altri sono interpretati esattamente allo stesso modo.  
  
```c#  
using System;  
using System.Runtime.Interop.Services;  
using Microsoft.VisualStudio.Debugger.Interop;  
  
namespace MyPackage  
{  
    public class MyClass  
    {  
        public void Interpret(TYPE_INFO ti)  
        {  
            if (ti.dwKind == (uint)enum_dwTypeKind.TYPE_KIND_METADATA)  
            {  
                 METADATA_TYPE dataType = (METADATA_TYPE)Marshal.PtrToStructure(ti.unionmember,  
                                               typeof(METADATA_TYPE));  
            }  
        }  
    }  
}  
```  
  
## Requisiti  
 intestazione: sh.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [dwTYPE\_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)   
 [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)   
 [METADATA\_TYPE](../../../extensibility/debugger/reference/metadata-type.md)   
 [PDB\_TYPE](../../../extensibility/debugger/reference/pdb-type.md)   
 [BUILT\_TYPE](../../../extensibility/debugger/reference/built-type.md)