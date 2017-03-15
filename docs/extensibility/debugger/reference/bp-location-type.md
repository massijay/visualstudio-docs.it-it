---
title: "BP_LOCATION_TYPE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BP_LOCATION_TYPE"
helpviewer_keywords: 
  - "Struttura BP_LOCATION_TYPE"
ms.assetid: 0248430a-3b61-4809-87a9-e9b6bb7d1130
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# BP_LOCATION_TYPE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Specifica il tipo di posizione del punto di interruzione per una richiesta del punto di interruzione.  
  
## Sintassi  
  
```cpp#  
enum enum_BP_LOCATION_TYPE {   
   BPLT_NONE               = 0x00000000,  
   BPLT_FILE_LINE          = 0x00010000,  
   BPLT_FUNC_OFFSET        = 0x00020000,  
   BPLT_CONTEXT            = 0x00030000,  
   BPLT_STRING             = 0x00040000,  
   BPLT_ADDRESS            = 0x00050000,  
   BPLT_RESOLUTION         = 0x00060000,  
   BPLT_CODE_FILE_LINE     = BPT_CODE | BPLT_FILE_LINE,  
   BPLT_CODE_FUNC_OFFSET   = BPT_CODE | BPLT_FUNC_OFFSET,  
   BPLT_CODE_CONTEXT       = BPT_CODE | BPLT_CONTEXT,  
   BPLT_CODE_STRING        = BPT_CODE | BPLT_STRING,  
   BPLT_CODE_ADDRESS       = BPT_CODE | BPLT_ADDRESS ,  
   BPLT_DATA_STRING        = BPT_DATA | BPLT_STRING,  
   BPLT_TYPE_MASK          = 0x0000FFFF,  
   BPLT_LOCATION_TYPE_MASK = 0xFFFF0000  
};  
typedef DWORD BP_LOCATION_TYPE;  
```  
  
```c#  
public enum enum_BP_LOCATION_TYPE {   
   BPLT_NONE               = 0x00000000,  
   BPLT_FILE_LINE          = 0x00010000,  
   BPLT_FUNC_OFFSET        = 0x00020000,  
   BPLT_CONTEXT            = 0x00030000,  
   BPLT_STRING             = 0x00040000,  
   BPLT_ADDRESS            = 0x00050000,  
   BPLT_RESOLUTION         = 0x00060000,  
   BPLT_CODE_FILE_LINE     = BPT_CODE | BPLT_FILE_LINE,  
   BPLT_CODE_FUNC_OFFSET   = BPT_CODE | BPLT_FUNC_OFFSET,  
   BPLT_CODE_CONTEXT       = BPT_CODE | BPLT_CONTEXT,  
   BPLT_CODE_STRING        = BPT_CODE | BPLT_STRING,  
   BPLT_CODE_ADDRESS       = BPT_CODE | BPLT_ADDRESS ,  
   BPLT_DATA_STRING        = BPT_DATA | BPLT_STRING,  
   BPLT_TYPE_MASK          = 0x0000FFFF,  
   BPLT_LOCATION_TYPE_MASK = 0xFFFF0000  
};  
```  
  
## Membri  
 BPLT\_NONE  
 Non specifica posizione del punto di interruzione.  
  
 BPLT\_FILE\_LINE  
 Specifica il tipo di posizione del punto di interruzione come un file.  
  
 BPLT\_FUNC\_OFFSET  
 Specifica il tipo di posizione del punto di interruzione come un offset di funzione.  
  
 BPLT\_CONTEXT  
 Specifica il tipo di posizione del punto di interruzione come contesto.  
  
 BPLT\_STRING  
 Specifica il tipo di posizione del punto di interruzione come stringa.  
  
 BPLT\_ADDRESS  
 Specifica il tipo di posizione del punto di interruzione come indirizzo.  
  
 BPLT\_RESOLUTION  
 Specifica il tipo di posizione del punto di interruzione come risoluzione.  
  
 BPLT\_CODE\_FILE\_LINE  
 Specifica il tipo di posizione del punto di interruzione di riga di codice sorgente.  
  
 BPLT\_CODE\_FUNC\_OFFSET  
 Specifica il tipo di posizione del punto di interruzione come un offset di funzione di codice.  
  
 BPLT\_CODE\_CONTEXT  
 Specifica il tipo di posizione del punto di interruzione come contesto di codice.  
  
 BPLT\_CODE\_STRING  
 Specifica il tipo di posizione del punto di interruzione come stringa di codice.  
  
 BPLT\_CODE\_ADDRESS  
 Specifica il tipo di posizione del punto di interruzione come indirizzo di codice.  
  
 BPLT\_DATA\_STRING  
 Specifica il tipo di posizione del punto di interruzione come una stringa di dati.  
  
 BPLT\_TYPE\_MASK  
 Specifica una maschera di bit, in modo che il tipo del punto di interruzione può essere estrattoe dal valore.  
  
 BPLT\_LOCATION\_TYPE\_MASK  
 Specifica una maschera di bit, in modo che il tipo di posizione del punto di interruzione può essere estrattoe dal valore.  
  
## Note  
 Passato come parametro [GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md) al metodo.  
  
 Un tipo di posizione del punto di interruzione è costituito da un tipo di punto di interruzione e di un tipo di posizione.  Ciò significa che un tipo di posizione del punto di interruzione non è mai un solo tipo del punto di interruzione, ad esempio`BPT_CODE`\) o un tipo di percorso \(ad esempio,`BPLT_FILE_LINE`\).  Le costanti predefinite per qualsiasi posizione del punto di interruzione sono attualmente supportati sono inclusi in questa enumerazione \(`BPLT_CODE_FILE_LINE` con `BPLT_DATA_STRING`\).  
  
 `BPT_CODE` e `BPT_DATA` sono membri dell'enumerazione [BP\_TYPE](../../../extensibility/debugger/reference/bp-type.md).  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md)   
 [BP\_TYPE](../../../extensibility/debugger/reference/bp-type.md)