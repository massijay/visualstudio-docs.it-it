---
title: "IDebugBinder3::GetExceptionObjectAndType | Microsoft Docs"
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
  - "IDebugBinder3::GetExceptionObjectAndType"
helpviewer_keywords: 
  - "Metodo IDebugBinder3::GetExceptionObjectAndType"
ms.assetid: 2a313fe1-4ee1-4f01-af86-382d6c661a8f
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugBinder3::GetExceptionObjectAndType
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questo metodo recupera l'eccezione associata a un oggetto, se disponibile.  
  
## Sintassi  
  
```cpp  
HRESULT GetExceptionObjectAndType(  
   IDebugObject** ppException,  
   IDebugField**  ppField  
);  
```  
  
```c#  
int GetExceptionObjectAndType(  
   out IDebugObject ppException,  
   out IDebugField  ppField  
);  
```  
  
#### Parametri  
 `ppException`  
 \[out\]  restituisce l'oggetto che rappresenta l'eccezione.  
  
 `ppField`  
 \[out\]  Restituisce l'oggetto che rappresenta un campo specifico che può provocare un'eccezione \(ciò può essere un valore null\).  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
> [!NOTE]
>  Per verificare se vi faccia un'eccezione, controllare il valore restituito da `ppException`: se è un valore null, pertanto non esiste alcuna eccezione associata all'oggetto.  
  
## Vedere anche  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)