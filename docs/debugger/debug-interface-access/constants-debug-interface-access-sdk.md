---
title: "Costanti (Debug Interface Access SDK) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "costanti, DIA SDK"
  - "DIA SDK, costanti"
ms.assetid: aca4ec77-bc08-4cdd-a6ce-8d4a28ea5ea3
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Costanti (Debug Interface Access SDK)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Queste costanti di stringa possono essere utilizzate per identificare le diverse sezioni di un file di database di debug del programma \(PDB\) con il DIA SDK.  
  
## Costanti  
 Di seguito sono dichiarati come macro C\/C\+\+.  
  
|Macro|Valore|  
|-----------|------------|  
|`DiaTable_Symbols`|" L " simbolo„|  
|`DiaTable_Sections`|" L " sezioni„|  
|`DiaTable_SrcFiles`|" L " SourceFiles„|  
|`DiaTable_LineNums`|" L " LineNumbers„|  
|`DiaTable_SegMap`|" L " SegmentMap„|  
|`DiaTable_Dbg`|" L " Dbg„|  
|`DiaTable_InjSrc`|" L " InjectedSource„|  
|`DiaTable_FrameData`|" L " FrameData„|  
  
## Esempio  
 Di seguito è riportato un esempio utilizzando uno di questi simboli:  
  
```cpp#  
HRESULT GetSymbolTable(IDiaEnumTables *pEnumTables, IDiaTable **pTable)  
{  
    HRESULT hr;  
    VARIANT var;  
    var.vt      = VT_BSTR;  
    var.bstrVal = SysAllocString( DiaTable_Symbols );  
    hr = pEnumTables->Item( var, pTable );  
    return(hr);  
}  
```  
  
## Requisiti  
 intestazione: dia2.h  
  
## Vedere anche  
 [Riferimento](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)   
 [Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [Interfacce \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md)