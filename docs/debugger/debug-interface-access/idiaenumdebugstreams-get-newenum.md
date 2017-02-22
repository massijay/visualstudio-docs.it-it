---
title: "IDiaEnumDebugStreams::get__NewEnum | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
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
  - "IDiaEnumDebugStreams::get__NewEnum (metodo)"
ms.assetid: 972372ff-abfc-4987-a302-7788fab90348
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumDebugStreams::get__NewEnum
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

recupera <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> versione di questo enumeratore.  
  
## Sintassi  
  
```cpp#  
HRESULT get__NewEnum (   
   IUnknown** pRetVal  
);  
```  
  
#### Parametri  
 pRetVal  
 \[out\]  restituisce `IUnknown` collegare che rappresenta  <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> versione di questo enumeratore.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Vedere anche  
 [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)