---
title: "DEBUG_REFERENCE_INFO | Microsoft Docs"
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
  - "DEBUG_REFERENCE_INFO"
helpviewer_keywords: 
  - "Struttura DEBUG_REFERENCE_INFO"
ms.assetid: 24b83d00-d756-42a1-8083-730f998761dc
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# DEBUG_REFERENCE_INFO
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

descrive un riferimento.  
  
## Sintassi  
  
```cpp#  
typedef struct tagDEBUG_REFERENCE_INFO {   
   DEBUGREF_INFO_FLAGS dwFields;  
   BSTR                bstrName;  
   BSTR                bstrType;  
   BSTR                bstrValue;  
   DBG_ATTRIB_FLAGS    dwAttrib;  
   REFERENCE_TYPE.     dwRefType;  
   IDebugReference2*   m_pReference;  
} DEBUG_REFERENCE_INFO;  
```  
  
```c#  
public struct DEBUG_REFERENCE_INFO {   
   public uint             dwFields;  
   public string           bstrName;  
   public string           bstrType;  
   public string           bstrValue;  
   public ulong            dwAttrib;  
   public uint.            dwRefType;  
   public IDebugReference2 m_pReference;  
};  
```  
  
## Membri  
 dwFields  
 Una combinazione di flag [DEBUGREF\_INFO\_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md) dall'enumerazione che specifica quali campi vengono compilati.  
  
 bstrName  
 Il nome definito [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) dall'utente dell'oggetto.  
  
 bstrType  
 Il tipo di riferimento come stringa formattata.  
  
 bstrValue  
 il valore di riferimento come stringa formattata  
  
 dwAttrib  
 Una combinazione di flag [DBG\_ATTRIB\_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) dall'enumerazione che specifica i flag per la proprietà di debug attributi e.  
  
 dwRefType  
 Un valore [REFERENCE\_TYPE](../../../extensibility/debugger/reference/reference-type.md) dell'enumerazione che specifica se il tipo di riferimento è forte o debole.  
  
 m\_pReference  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) un oggetto che specifica le informazioni di riferimento.  
  
## Note  
 Questa struttura viene passata a una chiamata [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md) al metodo da riempire.  Questa struttura viene restituita come parte di un elenco [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md) dall'interfaccia che, a sua volta, viene restituita da una chiamata [EnumChildren](../Topic/IDebugReference2::EnumChildren.md) al metodo.  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [DEBUGREF\_INFO\_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)   
 [DBG\_ATTRIB\_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)   
 [REFERENCE\_TYPE](../../../extensibility/debugger/reference/reference-type.md)   
 [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)   
 [EnumChildren](../Topic/IDebugReference2::EnumChildren.md)   
 [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)