---
title: "IDiaStackFrame::get_rawLVarInstanceValue | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaStackFrame::get_rawLVarInstanceValue (metodo)"
ms.assetid: ce526259-85a6-475b-9274-0b3a21d95db2
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IDiaStackFrame::get_rawLVarInstanceValue
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Questo metodo recupera il valore della variabile locale specificata come byte non elaborati.  
  
## Sintassi  
  
```cpp#  
HRESULT get_rawLVarInstanceValue(  
   IDiaLVarInstance* pInstance,  
   DWORD             cbDataMax,  
   DWORD*            pcbData,  
   BYTE*             pbData  
);  
```  
  
#### Parametri  
 `pInstance`  
 \[in\]   `IDiaLVarInstance` oggetto che rappresenta un'istanza di variabile locale per ottenere il valore per.  
  
 `cbDataMax`  
 \[in\]  Numero massimo di byte nel buffer indicato da `pbData`.  Può trattarsi di un massimo di 8 byte \(`sizeof(ULONGLONG)`\).  
  
 `pcbData`  
 \[out\]  Restituisce il numero effettivo di byte memorizzati nel buffer.  
  
 `pbData`  
 \[out\]  Un buffer in cui inserire i dati.  Non può essere `NULL`.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Vedere anche  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)