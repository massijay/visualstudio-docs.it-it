---
title: "IDebugAlias::GetICorDebugValue | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugAlias::GetICorDebugValue"
helpviewer_keywords: 
  - "Metodo IDebugAlias::GetICorDebugValue"
ms.assetid: b9eb39ee-84af-4ace-9cfe-236b3d48aff5
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugAlias::GetICorDebugValue
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Recupera un'interfaccia di codice gestito che rappresenta il valore associato a questo alias.  
  
## Sintassi  
  
```cpp  
HRESULT GetICorDebugValue(  
   IUnknown** ppUnk  
);  
```  
  
```c#  
int GetICorDebugValue(  
   out object ppUnk  
);  
```  
  
#### Parametri  
 `ppUnk`  
 \[out\] `IUnknown` interfaccia che rappresenta il valore associato a questo alias. Questa interfaccia è possibile eseguire query per il `ICorDebugValue` interfaccia.  
  
## Valore restituito  
 Se ha esito positivo, restituisce S\_OK; in caso contrario, restituisce un codice di errore.  
  
## Note  
 Questo metodo si applica solo ai valori gestiti \(il `ICorDebugValue` è disponibile in un'interfaccia di [!INCLUDE[dnprdnshort](../../../code-quality/includes/dnprdnshort_md.md)] e viene definito nel [!INCLUDE[dnprdnshort](../../../code-quality/includes/dnprdnshort_md.md)] SDK nel file Cordebug. idl\).  
  
## Vedere anche  
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)