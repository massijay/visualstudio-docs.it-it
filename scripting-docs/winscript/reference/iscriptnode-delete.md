---
title: "IScriptNode::Delete | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptNode.Delete
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptNode::Delete"
ms.assetid: 6765ff80-a9a8-40a3-a669-7fcc284c87af
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IScriptNode::Delete
Elimina questo struttura ad albero di oggetti.  
  
## Sintassi  
  
```  
HRESULT Delete();  
```  
  
#### Parametri  
 Il metodo non accetta parametri.  
  
## Valore restituito  
 Oggetto `HRESULT`.  I valori possibili sono, ma non sono limitati a, quelli nella tabella seguente.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## Note  
 Dopo che il metodo `Delete` viene chiamato, il metodo [IScriptNode::Alive](../../winscript/reference/iscriptnode-alive.md) deve indicare che il nodo dello script non è attivo.  
  
## Vedere anche  
 [Interfaccia IScriptNode](../../winscript/reference/iscriptnode-interface.md)