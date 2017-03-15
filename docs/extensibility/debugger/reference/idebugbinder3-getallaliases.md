---
title: "IDebugBinder3::GetAllAliases | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBinder3::GetAllAliases"
helpviewer_keywords: 
  - "Metodo IDebugBinder3::GetAllAliases"
ms.assetid: 1f9ab2ee-2ab3-4a61-8b99-95dd7fdf3511
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# IDebugBinder3::GetAllAliases
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questo metodo recupera un elenco degli alias dal programma.  
  
## Sintassi  
  
```cpp  
HRESULT GetAllAliases(  
   UINT          uRequest,  
   IDebugAlias** ppAliases,  
   UINT*         puFetched  
);  
```  
  
```c#  
int GetAllAliases(  
   uint          uRequest,   
   IDebugAlias[] ppAliases,   
   out uint      puFetched  
);  
```  
  
#### Parametri  
 `uRequest`  
 \[in\]  Il numero massimo di alias da restituire \(specifica la lunghezza di `ppAliases`trasformato matrice\).  
  
 `ppAliases`  
 \[in, out\]  La matrice per inserire con gli alias \(se questo è un valore null e `uRequest` è 0, il conteggio degli alias che possono essere restituiti viene restituito da `puFetched`\).  
  
 `puFetched`  
 \[out\]  Restituisce il numero di alias ottenuti.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Vedere anche  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)