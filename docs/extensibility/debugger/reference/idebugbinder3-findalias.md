---
title: "IDebugBinder3::FindAlias | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBinder3::FindAlias"
helpviewer_keywords: 
  - "Metodo IDebugBinder3::FindAlias"
ms.assetid: b8333701-2718-4983-8513-0875fb7cb730
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugBinder3::FindAlias
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questo metodo viene rilevato un alias, assegnato un nome.  In questo modo verranno individuati tutti gli alias nel programma.  
  
## Sintassi  
  
```cpp  
HRESULT FindAlias(  
   LPCOLESTR     pcstrName,  
   IDebugAlias** ppAlias  
);  
```  
  
```c#  
int FindAlias(  
   string          pcstrName,  
   out IDebugAlias ppAlias  
);  
```  
  
#### Parametri  
 `pcstrName`  
 \[in\]  Nome dell'alias da cercare.  
  
 `ppAlias`  
 \[out\]  L'alias carattere \(se presenti\) rappresentato [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) dall'interfaccia.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` \(se l'alias non viene trovato\) o un codice di errore.  
  
## Note  
 Questo metodo inizializza l'oggetto di destinazione a null prima di chiamare, si verifica in seguito per un valore null per determinare se un alias è stato trovato.  
  
## Vedere anche  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)   
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)