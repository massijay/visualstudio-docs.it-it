---
title: "IDebugAlias::Dispose | Microsoft Docs"
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
  - "IDebugAlias::Dispose"
helpviewer_keywords: 
  - "Metodo IDebugAlias::Dispose"
ms.assetid: e84909a4-d378-4f48-bf25-2c014c77c8e3
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugAlias::Dispose
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Contrassegna tale alias per la rimozione.  
  
## Sintassi  
  
```cpp  
HRESULT Dispose();  
```  
  
```c#  
int Dispose();  
```  
  
#### Parametri  
 Nessuno.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce S\_OK, in caso contrario, restituisce un codice di errore.  
  
## Note  
 Una volta che questo metodo viene chiamato, alias non è più disponibile.  
  
## Vedere anche  
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)