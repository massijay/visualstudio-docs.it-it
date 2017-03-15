---
title: "BP_RESOLUTION_LOCATION | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BP_RESOLUTION_LOCATION"
helpviewer_keywords: 
  - "Struttura BP_RESOLUTION_LOCATION"
ms.assetid: 21dc5246-69c1-43e3-855c-9cd4e596c0e6
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# BP_RESOLUTION_LOCATION
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Specifica la struttura della posizione di risoluzione del punto di interruzione.  
  
## Sintassi  
  
```cpp#  
struct _BP_RESOLUTION_LOCATION {  
   BP_TYPE bpType;  
   union {  
      BP_RESOLUTION_CODE bpresCode;  
      BP_RESOLUTION_DATA bpresData;  
      int                unused;  
   } bpResLocation;  
} BP_RESOLUTION_LOCATION;  
```  
  
```c#  
public struct BP_RESOLUTION_LOCATION {  
   public uint bpType;  
   public IntPtr unionmember1;  
   public IntPtr unionmember2;  
   public IntPtr unionmember3;  
   public uint   unionmember4;  
};  
```  
  
## Membri  
 `bpType`  
 Un valore [BP\_TYPE](../../../extensibility/debugger/reference/bp-type.md) dell'enumerazione che specifica come interpretare l'unione di `bpResLocation` o i membri di `unionmemberX` .  
  
 `bpResLocation.bpresCode`  
 \[C\+\+ solo\] contiene [BP\_RESOLUTION\_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md) la struttura se `bpType` \= `BPT_CODE`.  
  
 `bpResLocation.bpresData`  
 \[C\+\+ solo\] contiene [BP\_RESOLUTION\_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md) la struttura se `bpType` \= `BPT_DATA`.  
  
 `bpResLocation.unused`  
 \[C\+\+ solo\] segnaposto di Su.  
  
 `unionmember1`  
 \[Solo c\#\] vedere le note su come interpretare.  
  
 `unionmember2`  
 \[Solo c\#\] vedere le note su come interpretare.  
  
 `unionmember3`  
 \[Solo c\#\] vedere le note su come interpretare.  
  
 `unionmember4`  
 \[Solo c\#\] vedere le note su come interpretare.  
  
## Note  
 Questa struttura è un membro [BP\_ERROR\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) e [BP\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) strutture.  
  
 \[Solo c\#\] i membri di `unionmemberX` vengono interpretati nella seguente tabella.  Cercare nella colonna sinistra per il valore di `bpType` e tramite per determinare quale ogni membro di `unionmemberX` rappresenta e il marshalling `unionmemberX` di conseguenza.  Vedere l'esempio di una modalità dello schermo interpretino questa struttura in c\#.  
  
|`bpLocationType`|`unionmember1`|`unionmember2`|`unionmember3`|`unionmember4`|  
|----------------------|--------------------|--------------------|--------------------|--------------------|  
|`BPT_CODE`|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|\-|\-|\-|  
|`BPT_DATA`|`string` \(espressione di dati\)|`string` \(nome di funzione\)|`string` \(nome dell'immagine\)|`enum_BP_RES_DATA_FLAGS`|  
  
## Esempio  
 In questo esempio viene illustrato come interpretare la struttura di `BP_RESOLUTION_LOCATION` in c\#.  
  
```c#  
using System;  
using System.Runtime.Interop.Services;  
using Microsoft.VisualStudio.Debugger.Interop;  
  
namespace MyPackage  
{  
    public class MyClass  
    {  
        public void Interpret(BP_RESOLUTION_LOCATION bprl)  
        {  
            if (bprl.bpType == (uint)enum_BP_TYPE.BPT_CODE)  
            {  
                 IDebugCodeContext2 pContext = (IDebugCodeContext2)Marshal.GetObjectForIUnknown(bp.unionmember1);  
            }  
            else if (bprl.bpType == (uint)enum_BP_TYPE.BPT_DATA)  
            {  
                 string dataExpression = Marshal.PtrToStringBSTR(bp.unionmember3);  
                 string functionName = Marshal.PtrToStringBSTR(bp.unionmember2);  
                 string imageName = Marshal.PtrToStringBSTR(bp.unionmember3);  
                 enum_BP_RES_DATA_FLAGS numElements = (enum_BP_RES_DATA_FLAGS)bp.unionmember4;  
            }  
        }  
    }  
}  
```  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP\_TYPE](../../../extensibility/debugger/reference/bp-type.md)   
 [BP\_ERROR\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)   
 [BP\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)   
 [BP\_RESOLUTION\_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md)   
 [BP\_RESOLUTION\_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md)   
 [BP\_RES\_DATA\_FLAGS](../../../extensibility/debugger/reference/bp-res-data-flags.md)