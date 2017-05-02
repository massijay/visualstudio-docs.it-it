---
title: "Interfaccia IScriptNode | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "Interfaccia IScriptNode"
ms.assetid: cfa76c4a-6543-48e8-a946-d212cd0bf934
caps.latest.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 21
---
# Interfaccia IScriptNode
Un oggetto che implementa l'interfaccia `IScriptNode` rappresenta una pagina Web.  
  
 Oltre ai metodi ereditati da `IUnknown`, l'interfaccia `IScriptNode` espone i metodi seguenti.  
  
## Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IScriptNode::Alive](../../winscript/reference/iscriptnode-alive.md)|Indica se un oggetto è ancora attivo.|  
|[IScriptNode:: CreateChildEntry](../../winscript/reference/iscriptnode-createchildentry.md)|Aggiunge un'istanza figlio `IScriptEntry`.|  
|[IScriptNode::CreateChildHandler](../../winscript/reference/iscriptnode-createchildhandler.md)|Aggiunge uno scriptlet come istanze figlio `IScriptNode`.|  
|[IScriptNode::Delete](../../winscript/reference/iscriptnode-delete.md)|Elimina la struttura ad albero di oggetti.|  
|[IScriptNode::GetChild](../../winscript/reference/iscriptnode-getchild.md)|Restituisce l'elemento figlio dall'indice specificato nel nodo.|  
|[IScriptNode::GetCookie](../../winscript/reference/iscriptnode-getcookie.md)|Restituisce un valore definito dall'applicazione viene utilizzato per associare uno scriptlet con l'oggetto host.|  
|[IScriptNode::GetIndexInParent](../../winscript/reference/iscriptnode-getindexinparent.md)|Restituisce l'indice di un oggetto nell'elenco figlio del padre.|  
|[IScriptNode::GetLanguage](../../winscript/reference/iscriptnode-getlanguage.md)|Restituisce il linguaggio di script che viene utilizzato dal nodo corrente dello script.|  
|[IScriptNode::GetNumberOfChildren](../../winscript/reference/iscriptnode-getnumberofchildren.md)|Restituisce il numero di nodi figlio dell'oggetto `IScriptNode`.|  
|[IScriptNode::GetParent](../../winscript/reference/iscriptnode-getparent.md)|Restituisce l'oggetto `IScriptNode` che è il padre di un oggetto.|  
  
## Vedere anche  
 [Interfacce metodo Script ActiveX](../../winscript/reference/active-script-authoring-interfaces.md)