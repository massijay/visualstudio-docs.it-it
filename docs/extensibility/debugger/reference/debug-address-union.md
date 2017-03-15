---
title: "DEBUG_ADDRESS_UNION | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DEBUG_ADDRESS_UNION"
helpviewer_keywords: 
  - "Unione DEBUG_ADDRESS_UNION"
ms.assetid: e3d11aab-de0d-4109-b5dc-11e07e64382d
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# DEBUG_ADDRESS_UNION
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Vengono descritti i diversi tipi degli indirizzi.  
  
## Sintassi  
  
```cpp  
typedef struct _tagDEBUG_ADDRESS_UNION {  
   ADDRESS_KIND dwKind;  
   union {  
      NATIVE_ADDRESS                  addrNative;  
      UNMANAGED_ADDRESS_THIS_RELATIVE addrThisRel;  
      UNMANAGED_ADDRESS_PHYSICAL      addrUPhysical;  
      METADATA_ADDRESS_METHOD         addrMethod;  
      METADATA_ADDRESS_FIELD          addrField;  
      METADATA_ADDRESS_LOCAL          addrLocal;  
      METADATA_ADDRESS_PARAM          addrParam;  
      METADATA_ADDRESS_ARRAYELEM      addrArrayElem;  
      METADATA_ADDRESS_RETVAL         addrRetVal;  
      DWORD                           unused;  
   } addr;  
} DEBUG_ADDRESS_UNION;  
```  
  
```c#  
public struct DEBUG_ADDRESS_UNION {  
   public ADDRESS_KIND dwKind;  
   public IntPtr       unionmember;  
}  
```  
  
## termini  
 dwKind  
 Un valore [ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md) dell'enumerazione, specificando come interpretare l'unione.  
  
 addr.addrNative  
 \[C\+\+ solo\] contiene [NATIVE\_ADDRESS](../../../extensibility/debugger/reference/native-address.md) la struttura se `dwKind` \= ADDRESS\_KIND\_NATIVE.  
  
 addr.addrThisRel  
 \[C\+\+ solo\] contiene[UNMANAGED\_ADDRESS\_THIS\_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md) la struttura se `dwKind` \= ADDRESS\_KIND\_UNMANAGED\_THIS\_RELATIVE.  
  
 addr.addUPhysical  
 \[C\+\+ solo\] contiene[UNMANAGED\_ADDRESS\_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md) la struttura se `dwKind` \= ADDRESS\_KIND\_UNMANAGED\_PHYSICAL.  
  
 addr.addrMethod  
 \[C\+\+ solo\] contiene[METADATA\_ADDRESS\_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md) la struttura se `dwKind` \= ADDRESS\_KIND\_METHOD.  
  
 addr.addrField  
 \[C\+\+ solo\] contiene[METADATA\_ADDRESS\_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md) la struttura se `dwKind` \= ADDRESS\_KIND\_FIELD.  
  
 addr.addrLocal  
 \[C\+\+ solo\] contiene[METADATA\_ADDRESS\_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md) la struttura se `dwKind` \= ADDRESS\_KIND\_LOCAL.  
  
 addr.addrParam  
 \[C\+\+ solo\] contiene[METADATA\_ADDRESS\_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md) la struttura se `dwKind` \= ADDRESS\_KIND\_PARAM.  
  
 addr.addrArrayElem  
 \[C\+\+ solo\] contiene[METADATA\_ADDRESS\_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md) la struttura se `dwKind` \= ADDRESS\_KIND\_ARRAYELEM.  
  
 addr.addrRetVal  
 \[C\+\+ solo\] contiene[METADATA\_ADDRESS\_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md) la struttura se `dwKind` \= ADDRESS\_KIND\_RETVAL.  
  
 addr.unused  
 \[C\+\+ solo\] spaziatura interna.  
  
 addr  
 \[C\+\+ solo\] nome dell'unione.  
  
 unionmember  
 \[Solo c\#\] questo valore deve essere effettuato il marshalling del tipo appropriato della struttura basato su `dwKind`.  Vedere le note per l'associazione tra `dwKind` e l'interpretazione dell'unione.  
  
## Note  
 Questa struttura fanno parte [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) della struttura e rappresenta uno tra diversi tipi diversi degli indirizzi \(la struttura di `DEBUG_ADDRESS` viene soddisfatta da una chiamata [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) al metodo\).  
  
 \[Solo c\#\] illustrato nella tabella come interpretare il membro di `unionmember` per ogni tipo di indirizzo.  Nell'esempio viene illustrato come eseguire questa operazione per un tipo di indirizzo.  
  
|`dwKind`|`unionmember` interpretata come|  
|--------------|-------------------------------------|  
|`ADDRESS_KIND_NATIVE`|[NATIVE\_ADDRESS](../../../extensibility/debugger/reference/native-address.md)|  
|`ADDRESS_KIND_UNMANAGED_THIS_RELATIVE`|[UNMANAGED\_ADDRESS\_THIS\_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md)|  
|`ADDRESS_KIND_UNMANAGED_PHYSICAL`|[UNMANAGED\_ADDRESS\_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md)|  
|`ADDRESS_KIND_METHOD`|[METADATA\_ADDRESS\_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md)|  
|`ADDRESS_KIND_FIELD`|[METADATA\_ADDRESS\_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md)|  
|`ADDRESS_KIND_LOCAL`|[METADATA\_ADDRESS\_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md)|  
|`ADDRESS_KIND_PARAM`|[METADATA\_ADDRESS\_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md)|  
|`ADDRESS_KIND_ARRAYELEM`|[METADATA\_ADDRESS\_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md)|  
|`ADDRESS_KIND_RETVAL`|[METADATA\_ADDRESS\_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md)|  
  
## Esempio  
 In questo esempio viene illustrato come interpretare un tipo di indirizzo \(`METADATA_ADDRESS_ARRAYELEM`\) della struttura di `DEBUG_ADDRESS_UNION` in c\#.  Gli elementi restanti possono essere interpretati esattamente allo stesso modo.  
  
```c#  
using System;  
using System.Runtime.Interop.Services;  
using Microsoft.VisualStudio.Debugger.Interop;  
  
namespace MyPackage  
{  
    public class MyClass  
    {  
        public void Interpret(DEBUG_ADDRESS_UNION dau)  
        {  
            if (dau.dwKind == (uint)enum_ADDRESS_KIND.ADDRESS_KIND_METADATA_ARRAYELEM)  
            {  
                 METADATA_ADDRESS_ARRAYELEM arrayElem =  
                     (METADATA_ADDRESS_ARRAYELEM)Marshal.PtrToStructure(dau.unionmember,  
                                 typeof(METADATA_ADDRESS_ARRAYELEM));  
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
 [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)   
 [ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md)   
 [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)