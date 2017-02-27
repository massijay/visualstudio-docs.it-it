---
title: "IDebugDocumentContext2::Compare | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDocumentContext2::Compare"
helpviewer_keywords: 
  - "IDebugDocumentContext2::Compare"
ms.assetid: 2327b1ba-52d0-42fb-a01e-63cb4b332d2f
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugDocumentContext2::Compare
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Confronta il contesto di documento in una matrice specificata i contesti di documento.  
  
## Sintassi  
  
```cpp#  
HRESULT Compare(   
   DOCCONTEXT_COMPARE       compare,  
   IDebugDocumentContext2** rgpDocContextSet,  
   DWORD                    dwDocContextSetLen,  
   DWORD*                   pdwDocContext  
);  
```  
  
```c#  
int Compare(   
   enum_ DOCCONTEXT_COMPARE compare,  
   IDebugDocumentContext2[] rgpDocContextSet,  
   uint                     dwDocContextSetLen,  
   out uint                 pdwDocContext  
);  
```  
  
#### Parametri  
 `compare`  
 \[in\]  Un valore [DOCCONTEXT\_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md) dell'enumerazione che specifica il tipo di confronto.  
  
 `rgpDocContextSet`  
 \[in\]  Una matrice [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) di oggetti che rappresentano i contesti di documento confrontati.  
  
 `dwDocContextSetLen`  
 \[in\]  Lunghezza della matrice dei contesti di documento da confrontare.  
  
 `pdwDocContext`  
 \[out\]  Restituisce l'indice della matrice di `rgpDocContextSet` del primo contesto del documento che soddisfa il confronto.  
  
## Valore restituito  
 Restituisce `S_OK` se una corrispondenza è stata trovata.  Restituisce `S_FALSE` se non sono state trovate corrispondenze.  In caso contrario, restituisce un codice di errore.  
  
## Note  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) Gli oggetti passati nella matrice devono essere implementate nello stesso modulo di debug che implementa l'oggetto di `IDebugDocumentContext2` che viene chiamato; in caso contrario, il confronto non è valido.  
  
## Vedere anche  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [DOCCONTEXT\_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md)