---
title: "IDebugApplicationNode::EnumChildren | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplicationNode.EnumChildren
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplicationNode::EnumChildren"
ms.assetid: d79b362b-23d5-4a5e-a214-5a78618eaf71
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplicationNode::EnumChildren
Enumera i nodi figlio del nodo dell'applicazione.  
  
## Sintassi  
  
```  
HRESULT EnumChildren(  
   IEnumDebugApplicationNodes**  pperddp  
);  
```  
  
#### Parametri  
 `pperddp`  
 \[out\] l'enumerazione dei nodi figlio del nodo.  
  
## Valore restituito  
 Il metodo restituisce un tipo `HRESULT`.  I valori possibili sono, ma non sono limitati a, quelli nella tabella seguente.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## Note  
 Questo metodo enumera i nodi figlio del nodo dell'applicazione.  
  
## Vedere anche  
 [Interfaccia IDebugApplicationNode](../../winscript/reference/idebugapplicationnode-interface.md)