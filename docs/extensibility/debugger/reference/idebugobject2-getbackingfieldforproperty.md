---
title: "IDebugObject2::GetBackingFieldForProperty | Microsoft Docs"
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
  - "IDebugObject2::GetBackingFieldForProperty"
helpviewer_keywords: 
  - "Metodo IDebugObject2::GetBackingFieldForProperty"
ms.assetid: e72c6338-5573-4fad-8075-f3ade3435424
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugObject2::GetBackingFieldForProperty
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ottiene il campo o la variabile \(se presenti\) che possono supportare la proprietà rappresentata da questo oggetto.  
  
## Sintassi  
  
```cpp  
HRESULT GetBackingFieldForProperty(  
   IDebugObject2** ppObject  
);  
```  
  
```c#  
int GetBackingFieldForProperty(  
   out IDebugObject2 ppObject  
);  
```  
  
#### Parametri  
 `ppObject`  
 \[out\]  [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) un oggetto che descrive il campo sottostante.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce S\_OK, in caso contrario, restituisce un codice di errore.  
  
## Note  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) L'oggetto rappresenta una proprietà della classe di codice gestito, ovvero, un metodo con un ottenerne e\/o un accesso set.  Tali proprietà richiedono in genere una variabile di contenere il valore modificato dalla proprietà.  Questa variabile è nota come il campo sottostante.  Se non c " è un campo sottostante per l'oggetto, quindi verificare restituire un valore null: alcuni chiamanti non possono prestare attenzione al valore restituito ma avranno per verificare se un valore null è stato restituito in `ppObject`.  
  
## Vedere anche  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)