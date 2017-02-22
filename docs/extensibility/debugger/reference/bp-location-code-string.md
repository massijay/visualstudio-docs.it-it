---
title: "BP_LOCATION_CODE_STRING | Microsoft Docs"
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
  - "BP_LOCATION_CODE_STRING"
helpviewer_keywords: 
  - "Struttura BP_LOCATION_CODE_STRING"
ms.assetid: a4cd71c6-5052-45fe-907b-ebc6ca1df2e4
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# BP_LOCATION_CODE_STRING
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Utilizzato per impostare i punti di interruzione di codice in base a una stringa che l'utente può immettere dall'ambiente di sviluppo \(IDE\) integrato.  
  
## Sintassi  
  
```cpp#  
typedef struct _BP_LOCATION_CODE_STRING {   
   BSTR bstrContext;  
   BSTR bstrCodeExpr;  
} BP_LOCATION_CODE_STRING;  
```  
  
## Membri  
 `bstrContext`  
 Il contesto del punto di interruzione nel codice, in genere un nome di funzione o di metodo come indicato in uno stack di chiamate.  
  
 `bstrCodeExpr`  
 La stringa che gli utenti in per descrivere il punto di interruzione di codice.  
  
## Note  
 Questa struttura è un membro [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md) della struttura come parte di unione.  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md)