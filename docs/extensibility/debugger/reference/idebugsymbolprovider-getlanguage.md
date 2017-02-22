---
title: "IDebugSymbolProvider::GetLanguage | Microsoft Docs"
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
  - "IDebugSymbolProvider::GetLanguage"
helpviewer_keywords: 
  - "Metodo IDebugSymbolProvider::GetLanguage"
ms.assetid: e4142183-3d8b-418f-907f-4ee4c753d8ce
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugSymbolProvider::GetLanguage
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questo metodo ottiene il linguaggio utilizzato per compilare il codice all'indirizzo di debug.  
  
## Sintassi  
  
```cpp#  
HRESULT GetLanguage(   
   IDebugAddress* pAddress,  
   GUID*          pguidLanguage,  
   GUID*          pguidLanguageVendor  
);  
```  
  
```c#  
int GetLanguage(  
   IDebugAddress pAddress,   
   out Guid      pguidLanguage,   
   out Guid      pguidLanguageVendor  
);  
```  
  
#### Parametri  
 `pAddress`  
 \[in\]  un oggetto di indirizzo rappresentato [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) da un'interfaccia.  
  
 `pguidLanguage`  
 \[out\]  restituisce `GUID` che specifica il linguaggio.  
  
 `pguidLanguageVendor`  
 \[out\]  Restituisce `GUID` che specifica il fornitore del linguaggio.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 Il motore di debug chiama questo metodo per ottenere le informazioni necessarie per selezionare l'analizzatore di espressioni corretto.  
  
## Vedere anche  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)