---
title: "BP_LOCATION_CODE_FILE_LINE | Microsoft Docs"
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
  - "BP_LOCATION_CODE_FILE_LINE"
helpviewer_keywords: 
  - "Struttura BP_LOCATION_CODE_FILE_LINE"
ms.assetid: 3ff32032-d412-44d3-91bf-870cc354a09e
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# BP_LOCATION_CODE_FILE_LINE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Contiene i dati per la posizione di un punto di interruzione a una riga specifica in un file di origine del codice.  
  
## Sintassi  
  
```cpp#  
typedef struct _BP_LOCATION_CODE_FILE_LINE {   
   BSTR                     bstrContext;  
   IDebugDocumentPosition2* pDocPos;  
} BP_LOCATION_CODE_FILE_LINE;  
```  
  
## Membri  
 `bstrContext`  
 Il contesto del punto di interruzione, in genere un nome di funzione o di metodo come indicato in uno stack di chiamate.  
  
 `pDocPos`  
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md) L'oggetto che rappresenta la posizione del punto di interruzione.  
  
## Note  
 Questa struttura è un membro [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md) della struttura come parte di unione.  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)