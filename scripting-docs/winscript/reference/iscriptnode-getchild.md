---
title: "IScriptNode::GetChild | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptNode.GetChild
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptNode::GetChild"
ms.assetid: 8cb3f8b0-958b-40bb-a91a-49a788661861
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IScriptNode::GetChild
Restituisce l'elemento figlio dall'indice specificato nel nodo.  
  
## Sintassi  
  
```  
HRESULT GetChild(  
   ULONG              isn,  
   IScriptNode        **ppsn  
);  
```  
  
#### Parametri  
 `isn`  
 \[in\] indirizzo figlio nel padre.  
  
 `ppsn`  
 \[out\] l'indirizzo di una variabile che riceve un puntatore a un'interfaccia `IScriptNode` di istanze figlio.  
  
 Per gli oggetti `IScriptNode` che rappresentano una pagina Web, completamento del parametro un oggetto che contiene un blocco di script.  
  
 Per gli oggetti `IScriptEntry` che specificano un blocco di script, completamento del parametro un oggetto che specifica una funzione.  
  
## Valore restituito  
 Oggetto `HRESULT`.  I valori possibili sono, ma non sono limitati a, quelli nella tabella seguente.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## Note  
 Per gli oggetti `IScriptEntry` che specificano un oggetto funzione e per gli oggetti `IScriptScriptlet`, non riuscire di questo metodo poiché non sono presenti voci figlio.  
  
## Vedere anche  
 [Interfaccia IScriptNode](../../winscript/reference/iscriptnode-interface.md)