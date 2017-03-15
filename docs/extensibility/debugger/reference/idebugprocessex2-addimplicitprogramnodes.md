---
title: "IDebugProcessEx2::AddImplicitProgramNodes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcessEx2::AddImplicitProgramNodes"
helpviewer_keywords: 
  - "Metodo IDebugProcessEx2::AddImplicitProgramNodes"
ms.assetid: 8b491b00-f9e7-45b3-9115-fe58c3464289
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProcessEx2::AddImplicitProgramNodes
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questo metodo aggiunge un nodo di programma per ogni modulo di debug \(DE\) specificato.  
  
## Sintassi  
  
```cpp#  
HRESULT AddImplicitProgramNodes(  
   REFGUID guidLaunchingEngine,  
   GUID*   rgguidSpecificEngines,  
   DWORD   celtSpecificEngines  
);  
```  
  
```c#  
int AddImplicitProgramNodes(  
   ref Guid guidLaunchingEngine,  
   Guid[]   rgguidSpecificEngines,  
   uint     celtSpecificEngines  
);  
```  
  
#### Parametri  
 `guidLaunchingEngine`  
 \[in\]  `GUID` di un DE che deve essere utilizzato per avviare i programmi \(e viene utilizzato per aggiungere i propri nodi di programma\).  
  
 `rgguidSpecificEngines`  
 \[in\]  La matrice di `GUID`oggetti di nodi di programma DES per il quale verrà aggiunto.  
  
 `celtSpecificEngines`  
 \[in\]  Il numero di `GUID`oggetti nella matrice di `rgguidSpecificEngines` .  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 [Nodi di programma](../../../extensibility/debugger/program-nodes.md) verrà aggiunto per ogni DE elencato in `rgguidSpecificEngines`\- escluso il motore l'avvio automatico \(come `guidLaunchingEngine`fornito in\), che verrà utilizzato per aggiungere il relativo nodo del programma quando vara un programma.  
  
## Vedere anche  
 [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)   
 [Nodi di programma](../../../extensibility/debugger/program-nodes.md)