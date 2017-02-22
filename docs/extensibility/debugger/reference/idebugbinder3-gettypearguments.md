---
title: "IDebugBinder3::GetTypeArguments | Microsoft Docs"
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
  - "IDebugBinder3::GetTypeArguments"
helpviewer_keywords: 
  - "Metodo IDebugBinder3::GetTypeArguments"
ms.assetid: fa0c37a7-327f-463e-9a9d-bb3f534584cb
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugBinder3::GetTypeArguments
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questo metodo recupera un elenco di tipi di argomento associati all'oggetto.  
  
## Sintassi  
  
```cpp  
HRESULT GetTypeArguments(  
   UINT          skip,  
   UINT          count,  
   IDebugField** ppFields,  
   UINT*         pFetched  
);  
```  
  
```c#  
int GetTypeArguments(  
   uint          skip,  
   uint          count,  
   IDebugField[] ppFields,  
   out uint      pFetched  
);  
```  
  
#### Parametri  
 `skip`  
 \[in\]Numero di campi da ignorare prima di ottenere i tipi di argomento.  
  
 `count`  
 \[in\]  Il numero di sistema per restituire \(anche specifica la dimensione della matrice di `ppFields` \).  
  
 `ppFields`  
 \[in, out\]  Una matrice di campi che verranno riempiti da restituire di questo metodo.  
  
 `pFetched`  
 \[out\]  \(facoltativo\) il numero di campi del tipo di argomento effettivamente restituiti.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 Il numero di tipi di argomento può essere ottenuto in anticipo con [GetTypeArgumentCount](../Topic/IDebugBinder3::GetTypeArgumentCount.md).  
  
## Vedere anche  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)   
 [GetTypeArgumentCount](../Topic/IDebugBinder3::GetTypeArgumentCount.md)