---
title: "IDebugProperty2::SetValueAsReference | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProperty2::SetValueAsReference"
helpviewer_keywords: 
  - "Metodo IDebugProperty2::SetValueAsReference"
ms.assetid: 341b1b89-4ab8-4e1c-abe2-fb955df5c6b0
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugProperty2::SetValueAsReference
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Imposta il valore di questa proprietà sul valore del riferimento specificato.  
  
## Sintassi  
  
```cpp#  
HRESULT SetValueAsReference(  
   IDebugReference2** rgpArgs,  
   DWORD              dwArgCount,  
   IDebugReference2*  pValue,  
   DWORD              dwTimeout  
);  
```  
  
```c#  
int SetValueAsReference(  
   IDebugReference2[] rgpArgs,  
   uint               dwArgCount,  
   IDebugReference2   pValue,  
   uint               dwTimeout  
);  
```  
  
#### Parametri  
 `rgpArgs`  
 \[in\]  Una matrice di argomenti da passare al metodo di impostazione delle proprietà di codice gestito.  Se il metodo di impostazione della proprietà non accetta argomenti e se questo [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) oggetto non fa riferimento a tale metodo di impostazione della proprietà, `rgpArgs` deve essere un valore null.  questo parametro è in genere un valore null.  
  
 `dwArgCount`  
 \[in\]  Il numero di argomenti nella matrice di `rgpArgs` .  
  
 `pValue`  
 \[in\]  Un riferimento, sotto forma [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) di oggetto, al valore da utilizzare l'impostazione di questa proprietà.  
  
 `dwTimeout`  
 \[in\]  Il tempo impiegato da eseguire per impostare il valore, in millisecondi.  Un valore che è `INFINITE`.  Ciò influisce sulla durata che qualsiasi valutazione possibile utilizzare.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario restituisce un codice di errore, in genere uno dei seguenti elementi:  
  
|delle modifiche a..."|Descrizione|  
|---------------------------|-----------------|  
|`E_SETVALUEASREFERENCE_NOTSUPPORTED`|impostare il valore da un riferimento non è supportato.|  
|`E_SETVALUE_VALUE_CANNOT_BE_SET`|Il valore non può essere impostato, poiché questa proprietà fa riferimento a un metodo.|  
|`E_SETVALUE_VALUE_IS_READONLY`|Il valore è di sola lettura e non può essere impostato.|  
|`E_NOTIMPL`|Il metodo non è implementato.|  
  
## Vedere anche  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)