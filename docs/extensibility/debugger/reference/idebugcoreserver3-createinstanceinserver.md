---
title: "IDebugCoreServer3::CreateInstanceInServer | Microsoft Docs"
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
  - "IDebugCoreServer3::CreateInstanceInServer"
helpviewer_keywords: 
  - "IDebugCoreServer3::CreateInstanceInServer"
ms.assetid: 76f36bae-f6ab-413c-a8a9-8808bfeba05b
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugCoreServer3::CreateInstanceInServer
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Crea un'istanza di un modulo di debug sul server.  
  
## Sintassi  
  
```cpp#  
HRESULT CreateInstanceInServer(  
   LPCWSTR  szDll,  
   WORD     wLangId,  
   REFCLSID clsidObject,  
   REFIID   riid,  
   void**   ppvObject  
);  
```  
  
```c#  
int CreateInstanceInServer(  
   string     szDll,   
   ushort     wLangID,   
   ref Guid   clsidObject,   
   ref Guid   riid,   
   out IntPtr ppvObject  
);  
```  
  
#### Parametri  
 `szDll`  
 \[in\]  Il percorso della DLL che implementa il CLSID specificato dal parametro di `clsidObject` .  Se questo è `NULL`, la funzione di `CoCreateInstance` di COM è denominata.  
  
 `wLangId`  
 \[in\]  Impostazioni locali del motore di debug.  Può trattarsi 0 se [SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md) viene chiamato il metodo.  
  
 `clsidObject`  
 \[in\]  CLSID del motore di debug da creare.  
  
 `riid`  
 \[in\]  ID dell'interfaccia specifica da recuperare dall'oggetto di classe.  
  
 `ppvObject`  
 \[out\]  interfaccia di `IUnknown` da creare un'istanza.  Eseguire il cast o il marshalling questo oggetto all'interfaccia desiderata.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Vedere anche  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)   
 [SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)