---
title: "BP_LOCATION | Microsoft Docs"
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
  - "BP_LOCATION"
helpviewer_keywords: 
  - "Unione BP_LOCATION"
ms.assetid: ed1e874c-f289-4c31-8b6c-04dde03ad0f5
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# BP_LOCATION
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Specifica il tipo di struttura utilizzato per descrivere la posizione del punto di interruzione.  
  
## Sintassi  
  
```cpp#  
typedef struct _BP_LOCATION {  
   BP_LOCATION_TYPE bpLocationType;  
   union {  
      BP_LOCATION_CODE_FILE_LINE   bplocCodeFileLine;  
      BP_LOCATION_CODE_FUNC_OFFSET bplocCodeFuncOffset;  
      BP_LOCATION_CODE_CONTEXT     bplocCodeContext;  
      BP_LOCATION_CODE_STRING      bplocCodeString;  
      BP_LOCATION_CODE_ADDRESS     bplocCodeAddress;  
      BP_LOCATION_DATA_STRING      bplocDataString;  
      BP_LOCATION_RESOLUTION       bplocResolution;  
      DWORD                        unused;  
   } bpLocation;  
} BP_LOCATION;  
```  
  
```c#  
public struct BP_LOCATION {  
   public uint   bpLocationType;  
   public IntPtr unionmember1;  
   public IntPtr unionmember2;  
   public IntPtr unionmember3;  
   public IntPtr unionmember4;  
};  
```  
  
## Membri  
 `bpLocationType`  
 Un valore [BP\_LOCATION\_TYPE](../../../extensibility/debugger/reference/bp-location-type.md) dell'enumerazione utilizzata per interpretare l'unione di `bpLocation` o i membri di `unionmemberX` .  
  
 `bpLocation`.`bplocCodeFileLine`  
 \[C\+\+ solo\] contiene [BP\_LOCATION\_CODE\_FILE\_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md) la struttura se `bpLocationType` \= `BPLT_CODE_FILE_LINE`.  
  
 `bpLocation.bplocCodeFuncOffset`  
 \[C\+\+ solo\] contiene [BP\_LOCATION\_CODE\_FUNC\_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md) la struttura se `bpLocationType` \= `BPLT_CODE_FUNC_OFFSET`.  
  
 `bpLocation.bplocCodeContext`  
 \[C\+\+ solo\] contiene [BP\_LOCATION\_CODE\_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md) la struttura se `bpLocationType` \= `BPLT_CODE_CONTEXT`.  
  
 `bpLocation.bplocCodeString`  
 \[C\+\+ solo\] contiene [BP\_LOCATION\_CODE\_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md) la struttura se `bpLocationType` \= `BPLT_CODE_STRING`.  
  
 `bpLocation.bplocCodeAddress`  
 \[C\+\+ solo\] contiene [BP\_LOCATION\_CODE\_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md) la struttura se `bpLocationType` \= `BPLT_CODE_ADDRESS`.  
  
 `bpLocation.bplocDataString`  
 \[C\+\+ solo\] contiene [BP\_LOCATION\_DATA\_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md) la struttura se `bpLocationType` \= `BPLT_DATA_STRING`.  
  
 `bpLocation.bplocResolution`  
 \[C\+\+ solo\] contiene [BP\_LOCATION\_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md) la struttura se `bpLocationType` \= `BPLT_RESOLUTION`.  
  
 `unionmember1`  
 \[Solo c\#\] vedere le note su come interpretare.  
  
 `unionmember2`  
 \[Solo c\#\] vedere le note su come interpretare.  
  
 `unionmember3`  
 \[Solo c\#\] vedere le note su come interpretare.  
  
 `unionmember4`  
 \[Solo c\#\] vedere le note su come interpretare.  
  
## Note  
 Questa struttura è un membro [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md) e [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) strutture.  
  
 \[Solo c\#\] i membri di `unionmemberX` vengono interpretati nella seguente tabella.  Cercare nella colonna sinistra per il valore e l'aspetto di `bpLocationType` tra le altre colonne per determinare quale ogni membro di `unionmemberX` rappresenta e il marshalling `unionmemberX` di conseguenza.  Vedere l'esempio di una modalità dello schermo interpretino una parte di questa struttura in c\#.  
  
|`bpLocationType`|`unionmember1`|`unionmember2`|`unionmember3`|`unionmember4`|  
|----------------------|--------------------|--------------------|--------------------|--------------------|  
|`BPLT_CODE_FILE_LINE`|`string` \(un contesto\)|[IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)|\-|\-|  
|`BPLT_CODE_FUNC_OFFSET`|`string` \(un contesto\)|[IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)|\-|\-|  
|`BPLT_CODE_CONTEXT`|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|\-|\-|\-|  
|`BPLT_CODE_STRING`|`string` \(un contesto\)|`string` \(espressione condizionale\)|\-|\-|  
|`BPLT_CODE_ADDRESS`|`string` \(un contesto\)|`string` \(modulo URL\)|`string` \(nome di funzione\)|`string` \(indirizzo\)|  
|`BPLT_DATA_STRING`|[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)|`string` \(un contesto\)|`string` \(espressione di dati\)|`uint` \(numero di elementi\)|  
|`BPLT_RESOLUTION`|[IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)|\-|\-|\-|  
  
## Esempio  
 In questo esempio viene illustrato come interpretare la struttura di `BP_LOCATION` in c\# per il tipo di `BPLT_DATA_STRING` .  In questo particolare tipo come interpretare tutti e quattro i membri di `unionmemberX` in tutti i formati possibili \(oggetto, stringa e number\).  
  
```c#  
using System;  
using System.Runtime.Interop.Services;  
using Microsoft.VisualStudio.Debugger.Interop;  
  
namespace MyPackage  
{  
    public class MyClass  
    {  
        public void Interpret(BP_LOCATION bp)  
        {  
            if (bp.bpLocationType == (uint)enum_BP_LOCATION_TYPE.BPLT_DATA_STRING)  
            {  
                 IDebugThread2 pThread = (IDebugThread2)Marshal.GetObjectForIUnknown(bp.unionmember1);  
                 string context = Marshal.PtrToStringBSTR(bp.unionmember2);  
                 string dataExpression = Marshal.PtrToStringBSTR(bp.unionmember3);  
                 uint numElements = (uint)Marshal.ReadInt32(bp.unionmember4);  
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
 [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP\_LOCATION\_CODE\_FILE\_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md)   
 [BP\_LOCATION\_CODE\_FUNC\_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md)   
 [BP\_LOCATION\_CODE\_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md)   
 [BP\_LOCATION\_CODE\_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md)   
 [BP\_LOCATION\_CODE\_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md)   
 [BP\_LOCATION\_DATA\_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md)   
 [BP\_LOCATION\_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md)