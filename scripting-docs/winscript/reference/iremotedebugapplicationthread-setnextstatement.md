---
title: "IRemoteDebugApplicationThread::SetNextStatement | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplicationThread.SetNextStatement
apilocation: pdm.dll
helpviewer_keywords: 
  - "IRemoteDebugApplicationThread::SetNextStatement"
ms.assetid: 356766da-f7b7-4e8d-b4f3-2ab8da0609b8
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IRemoteDebugApplicationThread::SetNextStatement
Forza esecuzione per continuare vicino possibile al contesto di codice specificato, nel contesto del frame specificato.  
  
## Sintassi  
  
```  
HRESULT SetNextStatement(  
   IDebugStackFrame*   pStackFrame,  
   IDebugCodeContext*  pCodeContext  
);  
```  
  
#### Parametri  
 `pStackFrame`  
 \[in\] l'oggetto dello stack frame.  In questo argomento può essere NULL, che implica lo stack frame corrente deve essere utilizzato.  
  
 `pCodeContext`  
 \[in\] il contesto di codice.  In questo argomento può essere NULL, che implica il contesto di codice corrente deve essere utilizzato.  
  
## Valore restituito  
 Il metodo restituisce un tipo `HRESULT`.  I valori possibili sono, ma non sono limitati a, quelli nella tabella seguente.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## Note  
 Questo metodo forza l'esecuzione di continuare vicino possibile al contesto di codice specificato da `pCodeContext`, nel contesto del frame specificato da `pStackFrame`.  Uno di questi argomenti è possibile `NULL`, che rappresenta il frame o il contesto corrente.  
  
## Vedere anche  
 [Interfaccia IRemoteDebugApplicationThread](../../winscript/reference/iremotedebugapplicationthread-interface.md)