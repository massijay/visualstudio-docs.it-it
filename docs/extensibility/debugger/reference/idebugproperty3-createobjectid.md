---
title: "IDebugProperty3::CreateObjectID | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProperty3::CreateObjectID"
helpviewer_keywords: 
  - "IDebugProperty3::CreateObjectID"
ms.assetid: f2fa81e7-822f-456e-8729-a96a18eea771
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProperty3::CreateObjectID
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Crea un ID univoco per questa proprietà per assicurarsi che sia univoca tra tutte le altre proprietà.  
  
## Sintassi  
  
```cpp  
HRESULT CreateObjectID(  
   void  
);  
```  
  
```c#  
int CreateObjectID();  
```  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 Questo metodo viene chiamato quando l'amministratore di debug della sessione desidera assicurarsi che questa proprietà in modo univoco sia identificata da tutte le altre proprietà.  I supporti \(DE\) di motore di debug di questo metodo a meno che le proprietà che si occupa di già in modo univoco sono indicati.  se il DE non supporta questo metodo, restituisce `E_NOTIMPL`.  
  
 Qualsiasi ID univoco creato con `CreateObjectID` [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md) eliminato al metodo viene chiamato; in questo modo si segnala la fine dell'esigenza in modo univoco dell'identificazione di questa proprietà.  
  
> [!NOTE]
>  Non esiste alcun metodo per recuperare questo ID univoco, in modo da DE possibile apportare eventuali desidera gli identificatori univoci quando il metodo di `CreateObjectID` viene chiamato.  
  
## Vedere anche  
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)