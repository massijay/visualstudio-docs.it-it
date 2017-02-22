---
title: "IDebugPortSupplier3::CanPersistPorts | Microsoft Docs"
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
  - "IDebugPortSupplier3::CanPersistPorts"
helpviewer_keywords: 
  - "IDebugPortSupplier3::CanPersistPorts"
ms.assetid: 4127760c-e602-4e86-9232-457e382a52c7
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPortSupplier3::CanPersistPorts
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questo metodo determina se il fornitore di porte può mantenere le porte \(scrivendole su disco\) tra il debugger chiama.  
  
## Sintassi  
  
```cpp  
HRESULT CanPersistPorts();  
```  
  
```c#  
int CanPersistPorts();  
```  
  
#### Parametri  
 Nessuno.  
  
## Valore restituito  
 `S_OK` se le porte possono essere salvate in modo permanente, o `S_FALSE` per indicare che le porte non possono essere mantenute.  
  
## Note  
 Se il fornitore di porte può mantenere le porte, deve farlo quando viene eliminato e quindi ricaricarle quando viene creata un'istanza nuovamente.  
  
## Vedere anche  
 [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)