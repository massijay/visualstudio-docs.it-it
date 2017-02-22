---
title: "IEEVisualizerService::GetCustomViewerCount | Microsoft Docs"
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
  - "IEEVisualizerService::GetCustomViewerCount"
helpviewer_keywords: 
  - "Metodo IEEVisualizerService::GetCustomViewerCount"
ms.assetid: f7b095c2-e538-4352-8cad-d4c6d4f6bdbc
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IEEVisualizerService::GetCustomViewerCount
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questo metodo ottiene il numero dei visualizzatori di tipi disponibili dal servizio.  
  
## Sintassi  
  
```cpp  
HRESULT GetCustomViewerCount(  
   ULONG* pcelt  
);  
```  
  
```c#  
int GetCustomViewerCount(  
   out uint pcelt  
);  
```  
  
#### Parametri  
 `pcelt`  
 \[out\]  Restituisce il numero dei visualizzatori di tipi disponibili.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 [GetCustomViewerCount](../Topic/IDebugProperty3::GetCustomViewerCount.md) passa la richiesta a questo metodo nel supporto per i visualizzatori di tipi.  
  
## Vedere anche  
 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [GetCustomViewerCount](../Topic/IDebugProperty3::GetCustomViewerCount.md)