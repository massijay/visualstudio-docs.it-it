---
title: "IDebugMethodField::EnumAllLocals | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugMethodField::EnumAllLocals"
helpviewer_keywords: 
  - "Metodo IDebugMethodField::EnumAllLocals"
ms.assetid: 0bc7cc13-2628-4bd8-8c06-4d2aa6755ea8
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugMethodField::EnumAllLocals
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Crea un enumeratore per tutte le variabili locali del metodo, incluse quelle generate internamente dal compilatore.  
  
## Sintassi  
  
```cpp#  
HRESULT EnumAllLocals(   
   IDebugAddress*     pAddress,  
   IEnumDebugFields** ppLocals  
);  
```  
  
```c#  
int EnumAllLocals(  
   IDebugAddress        pAddress,   
   out IEnumDebugFields ppLocals  
);  
```  
  
#### Parametri  
 `pAddress`  
 \[in\]  [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) Oggetto che rappresenta un indirizzo di debug nel metodo, puntando a un ambito o a un contesto specifico.  
  
 `ppLocals`  
 \[out\]  Restituisce [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) un oggetto che rappresenta l'elenco di tutti i locali nell'ambito specificato; in caso contrario, restituisce un valore null che non indica locali.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce S\_OK o restituisce S\_FALSE se non vi sono locali.  In caso contrario, restituisce un codice di errore.  
  
## Note  
 Solo le variabili definite all'interno del blocco contenente l'indirizzo specificato di debug vengono enumerate.  Questo metodo include tutti i locali generati dal compilatore.  Se tutti che siano necessari sono variabili locali definiti in modo esplicito nel database di origine, chiamare [EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) il metodo.  
  
 Un metodo può contenere più contesti o i blocchi di definizione.  
  
## Vedere anche  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)