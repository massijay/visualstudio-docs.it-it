---
title: "IDebugCoreServer3::EnableAutoAttach | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCoreServer3::EnableAutoAttach"
helpviewer_keywords: 
  - "IDebugCoreServer3::EnableAutoAttach"
ms.assetid: 06aa633b-263b-4e08-8844-9a52d5120b94
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugCoreServer3::EnableAutoAttach
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Consente di associare automatico dei motori di debug specificati.  
  
## Sintassi  
  
```cpp#  
HRESULT EnableAutoAttach(  
   GUID*     rgguidSpecificEngines,  
   DWORD     celtSpecificEngines,  
   LPCOLESTR pszStartPageUrl,  
   BSTR*     pbstrSessionId  
);  
```  
  
```c#  
int EnableAutoAttach(  
   Guid[]     rgguidSpecificEngines,  
   uint       celtSpecificEngines,  
   string     pszStartPageUrl,  
   out string pbstrSessionId  
);  
```  
  
#### Parametri  
 `rgguidSpecificEngines`  
 \[in\]  Matrice dei GUID per ogni modulo di debug contrassegnino come auto\-allegando.  
  
 `celtSpecificEngines`  
 \[in\]  Il numero dei moduli specificati in `rgguidSpecificEngines`.  
  
 `pszStartPageUrl`  
 \[in\]  l'URL di avvio da utilizzare quando auto\-allegano.  
  
 `pbstrSessionID`  
 \[out\]  ID sessione che auto\-è stata collegata.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario restituisce il codice di errore.  Un codice di errore viene `E_AUTO_ATTACH_NOT_REGISTERED`, che indica che il class factory dell'auto\-attaccatura non è stato registrato.  
  
## Note  
 Quando un programma associato all'URL specificato viene avviato, i motori di debug specificati automaticamente vengono avviati e allegati.  
  
## Vedere anche  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)