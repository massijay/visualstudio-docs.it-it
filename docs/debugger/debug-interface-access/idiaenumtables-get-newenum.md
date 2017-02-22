---
title: "IDiaEnumTables::get__NewEnum | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaEnumTables::get__NewEnum (metodo)"
ms.assetid: 7b1159c7-a5f0-4baa-861a-dc11437d8b93
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumTables::get__NewEnum
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

recupera <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> versione di questo enumeratore.  
  
## Sintassi  
  
```cpp#  
HRESULT get__NewEnum (   
   IUnknown** pRetVal  
);  
```  
  
#### Parametri  
 `pRetVal`  
 \[out\]  restituisce `IUnknown` collegare che rappresenta  <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> versione di questo enumeratore.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Vedere anche  
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)