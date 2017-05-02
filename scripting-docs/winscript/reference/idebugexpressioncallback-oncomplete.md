---
title: "IDebugExpressionCallBack::onComplete | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugExpressionCallBack.onComplete
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugExpressionCallBack::onComplete"
ms.assetid: d0b89db3-38e7-44e0-93fe-60205f9149dd
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugExpressionCallBack::onComplete
Indica che la valutazione di un'espressione è completa.  
  
## Sintassi  
  
```  
HRESULT onComplete();  
```  
  
#### Parametri  
 Questo metodo non accetta parametri.  
  
## Valore restituito  
 Il metodo restituisce un tipo `HRESULT`.  I valori possibili sono, ma non sono limitati a, quelli nella tabella seguente.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## Note  
 Questo metodo viene chiamato quando la valutazione di un'espressione è completa.  Il metodo `IDebugExpression::GetResultAsString` può essere chiamato dal gestore eventi.  
  
## Vedere anche  
 [Interfaccia IDebugExpressionCallBack](../../winscript/reference/idebugexpressioncallback-interface.md)   
 [IDebugExpression::GetResultAsString](../../winscript/reference/idebugexpression-getresultasstring.md)