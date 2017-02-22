---
title: "IDebugProperty2::SetValueAsString | Microsoft Docs"
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
  - "IDebugProperty2::SetValueAsString"
helpviewer_keywords: 
  - "IDebugProperty2::SetValueAsString"
ms.assetid: 9e6a5054-41b7-4223-b509-b93689d366a5
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProperty2::SetValueAsString
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Imposta il valore di una proprietà da una stringa specificata.  
  
## Sintassi  
  
```cpp#  
HRESULT SetValueAsString (   
   LPCOLESTR pszValue,  
   UINT      nRadix,  
   DWORD     dwTimeout  
);  
```  
  
```c#  
int SetValueAsString (   
   string pszValue,  
   uint   nRadix,  
   uint   dwTimeout  
);  
```  
  
#### Parametri  
 `pszValue`  
 \[in\]  Stringa contenente il valore da impostare.  
  
 `nRadix`  
 \[in\]  Una radice da utilizzare nell'interpretazione delle informazioni numerica.  Può trattarsi 0 per tentare di determinare la radice automaticamente.  
  
 `dwTimeout`  
 \[in\]  Specifica il tempo massimo, in millisecondi, di attendere prima di uscire da questo metodo.  Utilizzo `INFINITE` attendere infinito.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario restituisce il codice di errore.  Nella tabella seguente vengono illustrati altri valori possibili.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|`E_SETVALUE_VALUE_CANNOT_BE_SET`|La stringa non può essere convertito in un valore della proprietà, o il valore della proprietà potrebbe non essere impostato.|  
|`E_SETVALUE_VALUE_IS_READONLY`|La proprietà è in sola lettura.|  
  
## Vedere anche  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)