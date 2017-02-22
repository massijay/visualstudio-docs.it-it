---
title: "IDebugMethodField::GetGlobalContainer | Microsoft Docs"
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
  - "IDebugMethodField::GetGlobalContainer"
helpviewer_keywords: 
  - "Metodo IDebugMethodField::GetGlobalContainer"
ms.assetid: 041ac5aa-0b80-4310-b9ae-b88f8e7e0e5f
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugMethodField::GetGlobalContainer
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ottiene il contenitore globale del metodo.  
  
## Sintassi  
  
```cpp#  
HRESULT GetGlobalContainer(  
   IDebugClassField** ppClass  
);  
```  
  
```c#  
int GetGlobalContainer(  
   out IDebugClassField ppClass  
);  
```  
  
#### Parametri  
 `ppClass`  
 \[out\]  Restituisce [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) una rappresentazione del modulo in cui questo metodo è definito.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce S\_OK, in caso contrario, restituisce un codice di errore.  
  
## Note  
 L'oggetto restituito [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) rappresenta l'intero modulo ed è un oggetto artificiale, ovvero, il modulo stesso non dispone della classe effettiva ma può essere rappresentato da un oggetto di `IDebugClassField` , consentendo i diversi elementi del modulo da enumerare e individuare.  
  
## Vedere anche  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)