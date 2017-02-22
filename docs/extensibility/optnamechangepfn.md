---
title: "OPTNAMECHANGEPFN | Microsoft Docs"
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
  - "OPTNAMECHANGEPFN"
helpviewer_keywords: 
  - "Funzione di callback OPTNAMECHANGEPFN"
ms.assetid: 147303f3-c7f1-438a-81b7-db891ea3d076
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# OPTNAMECHANGEPFN
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Si tratta di una funzione di callback specificata in una chiamata al [SccSetOption](../extensibility/sccsetoption-function.md) \(tramite opzione `SCC_OPT_NAMECHANGEPFN`\) e viene utilizzato per comunicare nome modifiche per il controllo del codice sorgente del plug\-in dell'IDE di.  
  
## Signature  
  
```cpp#  
typedef void (*OPTNAMECHANGEPFN)( LPVOID pvCallerData, LPCSTR pszOldName, LPCSTR pszNewName );  
```  
  
## Parametri  
 pvCallerData  
 \[in\] Valore dell'utente specificato in una precedente chiamata al [SccSetOption](../extensibility/sccsetoption-function.md) \(tramite opzione `SCC_OPT_USERDATA`\).  
  
 pszOldName  
 \[in\] Il nome originale del file.  
  
 pszNewName  
 \[in\] Il nome del file è stato rinominato.  
  
## Valore restituito  
 Nessuno.  
  
## Note  
 Se un file viene rinominato durante un'operazione di controllo di origine, il plug\-in del controllo del codice sorgente può notificare l'IDE di modifica del nome tramite questo callback.  
  
 Se l'IDE non supporta questo callback, non chiami il [SccSetOption](../extensibility/sccsetoption-function.md) specificarlo. Se il plug\-in non supporta questo callback, restituirà `SCC_E_OPNOTSUPPORTED` dal `SccSetOption` funzione quando l'IDE tenta di impostare il callback.  
  
## Vedere anche  
 [Funzioni di callback implementate dall'IDE](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [SccSetOption](../extensibility/sccsetoption-function.md)