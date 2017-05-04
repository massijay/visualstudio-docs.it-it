---
title: "IDebugExpression::Start | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugExpression.Start
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugExpression::Start"
ms.assetid: a7af3470-62b5-40f0-987d-63b6b22538b3
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugExpression::Start
Inizia la valutazione di un'espressione.  
  
## Sintassi  
  
```  
HRESULT Start(  
   IDebugExpressionCallBack*  pdecb  
);  
```  
  
#### Parametri  
 `pdecb`  
 \[in\] callback per indicare quando la valutazione di un'espressione è completa.  Se questo parametro è `NULL`, non viene generato l'evento e il client deve eseguire il polling dello stato dell'espressione utilizzando `QueryIsComplete`.  
  
## Valore restituito  
 Il metodo restituisce un tipo `HRESULT`.  I valori possibili sono, ma non sono limitati a, quelli nella tabella seguente.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## Note  
 Questo metodo avvia la valutazione di un'espressione.  
  
## Vedere anche  
 [IDebugExpression::Abort](../../winscript/reference/idebugexpression-abort.md)   
 [Interfaccia IDebugExpression](../../winscript/reference/idebugexpression-interface.md)