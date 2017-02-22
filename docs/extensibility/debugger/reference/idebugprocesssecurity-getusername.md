---
title: "IDebugProcessSecurity::GetUserName | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugProcessSecurity::GetUserName"
ms.assetid: c73c60ac-da6e-45ae-8f04-95353a24ca3e
caps.latest.revision: 4
caps.handback.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProcessSecurity::GetUserName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ottiene il nome utente dal fornitore di porte.  
  
## Sintassi  
  
```cpp#  
HRESULT GetUserName(  
    BSTR *pbstrUserName  
);  
```  
  
```c#  
int GetUserName (  
    string pbstrUserName  
);  
```  
  
#### Parametri  
 `pbstrUserName`  
 \[out\]  Stringa contenente il nome utente.  
  
## Valore restituito  
 Se il metodo ha esito positivo, restituisce `S_OK`.  In caso contrario restituisce un codice di errore.  
  
## Note  
 `GetUserName` restituisce il nome utente che verrà visualizzata nella colonna di **nome utente** della finestra di dialogo di **Connettersi da elaborare** .  Per visualizzare la finestra di dialogo di **Connettersi da elaborare** , fare clic su **Connettersi da elaborare** scegliere dal menu di **strumenti** nell'ambiente di sviluppo integrato di \(IDE\) [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] .  
  
## Vedere anche  
 [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)