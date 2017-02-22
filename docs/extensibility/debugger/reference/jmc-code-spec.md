---
title: "JMC_CODE_SPEC | Microsoft Docs"
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
  - "JMC_CODE_SPEC"
helpviewer_keywords: 
  - "Struttura JMC_CODE_SPEC"
ms.assetid: d89498f1-4234-46d9-b4e2-abbcbca5068a
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# JMC_CODE_SPEC
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questa struttura viene utilizzata per impostare le informazioni di JustMyCode per un modulo.  
  
## Sintassi  
  
```cpp#  
typedef struct _JMC_CODE_SPEC {  
   BOOL fIsUserCode;  
   BSTR bstrModuleName;  
} JMC_CODE_SPEC;  
```  
  
```c#  
public struct JMC_CODE_SPEC {  
   public int    fIsUserCode;  
   public string bstrModuleName;  
};  
```  
  
## Membri  
 fIsUserCode  
 diverso da zero \(`TRUE`\) se il modulo deve essere considerato codice utente; in caso contrario, lo zero \(`FALSE`\) se il modulo deve essere considerato come codice esterno e non eseguire il debug.  
  
 bstrModuleName  
 Nome del modulo in questione.  
  
## Note  
 Questa struttura viene passata come elenco di tali strutture [SetJustMyCodeState](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md) al metodo.  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [SetJustMyCodeState](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md)