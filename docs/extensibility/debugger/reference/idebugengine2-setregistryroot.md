---
title: "IDebugEngine2::SetRegistryRoot | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngine2::SetRegistryRoot"
helpviewer_keywords: 
  - "IDebugEngine2::SetRegistryRoot"
ms.assetid: d0d81202-8a4a-4bc3-b297-30a047c5ec60
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugEngine2::SetRegistryRoot
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Imposta la chiave radice del Registro di sistema per il modulo \(DE\) di debug.  
  
## Sintassi  
  
```cpp#  
HRESULT SetRegistryRoot(   
   LPCOLESTR pszRegistryRoot  
);  
```  
  
```c#  
int SetRegistryRoot(   
   string pszRegistryRoot  
);  
```  
  
#### Parametri  
 `pszRegistryRoot`  
 \[in\]  La chiave radice del Registro di sistema da utilizzare.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 Questo metodo consente di [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] specificare la directory radice del Registro di sistema alternativa che il DE necessario utilizzare per ottenere le impostazioni del Registro di sistema, ad esempio, “HKEY\_LOCAL\_MACHINE \\SOFTWARE\\Microsoft\\VisualStudio\\8.0Exp„.  
  
## Vedere anche  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)