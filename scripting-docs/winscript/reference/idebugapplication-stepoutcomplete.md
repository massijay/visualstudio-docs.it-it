---
title: "IDebugApplication::StepOutComplete | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplication.StepOutComplete
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplication::StepOutComplete"
ms.assetid: 9675b214-7be5-4cf7-a63f-7865f3c54371
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplication::StepOutComplete
All'amministratore del processo di debug che un motore di linguaggio in modalità di istruzione singola sta per ritornare al relativo chiamante.  
  
## Sintassi  
  
```  
HRESULT StepOutComplete();  
```  
  
#### Parametri  
 Questo metodo non accetta parametri.  
  
## Valore restituito  
 Il metodo restituisce un tipo `HRESULT`.  I valori possibili sono, ma non sono limitati a, quelli nella tabella seguente.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## Note  
 I motori di linguaggio chiama questo metodo in modalità di istruzione singola prima che restituiscono al chiamante.  L'amministratore processo di debug utilizza questa possibilità a tutti gli altri moduli di gestione di script che devono interrompere la prima possibile.  Questa tecnica è come le modalità di più lingue di passaggio vengono implementate.  
  
## Vedere anche  
 [Interfaccia IDebugApplication](../../winscript/reference/idebugapplication-interface.md)