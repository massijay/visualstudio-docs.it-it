---
title: "IDebugReference2::SetValueAsString | Microsoft Docs"
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
  - "IDebugReference2::SetValueAsString"
helpviewer_keywords: 
  - "IDebugReference2::SetValueAsString"
ms.assetid: 9a508ced-fd54-44f5-bb42-ec15c80384d7
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugReference2::SetValueAsString
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Imposta il valore di un riferimento da una stringa.  Riservato per un utilizzo futuro.  
  
## Sintassi  
  
```cpp#  
HRESULT SetValueAsString (   
   LPCOLESTR pszValue,  
   DWORD     dwRadix,  
   DWORD     dwTimeout  
);  
```  
  
```c#  
int SetValueAsString (   
   string pszValue,  
   uint   dwRadix,  
   uint   dwTimeout  
);  
```  
  
#### Parametri  
 `pszValue`  
 \[in\]  il valore come stringa.  
  
 `dwRadix`  
 \[in\]  La radice da utilizzare durante la formattazione delle informazioni numerica.  
  
 `dwTimeout`  
 \[in\]  Tempo massimo, in millisecondi, di attendere prima di uscire da questo metodo.  Utilizzo `INFINITE` attendere infinito.  
  
## Valore restituito  
 Restituisce sempre `E_NOTIMPL`.  
  
## Vedere anche  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)