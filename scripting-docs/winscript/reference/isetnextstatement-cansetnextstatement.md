---
title: "ISetNextStatement::CanSetNextStatement | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: ISetNextStatement.CanSetNextStatement
apilocation: scrobj.dll
ms.assetid: e2a54634-31ec-4d16-84e8-2b123845d876
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# ISetNextStatement::CanSetNextStatement
Questo metodo determina se il punto di esecuzione, che determina la successiva istruzione di codice da eseguire, può essere impostato nella posizione specificata.  
  
## Sintassi  
  
```  
HRESULT CanSetNextStatement(  
   IDebugStackFrame*  pStackFrame,  
   IDebugCodeContext*  pCodeContext  
)  
```  
  
#### Parametri  
 `pStackFrame`  
 \[in\] puntatore a un oggetto stack frame.  
  
 `pCodeContext`  
 \[in\] puntatore a un oggetto di contesto di codice.  
  
## Valore restituito  
 Il metodo restituisce un tipo `HRESULT`.  I valori possibili sono, ma non sono limitati a, quelli nella tabella seguente.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|`S_OK`|L'istruzione successiva può essere aggiornato al contesto di codice specificato.|  
|`S_FALSE`|L'istruzione seguente non può essere aggiornato al contesto di codice specificato.|  
  
## Note  
  
## Vedere anche  
 [Interfaccia ISetNextStatement](../../winscript/reference/isetnextstatement-interface.md)