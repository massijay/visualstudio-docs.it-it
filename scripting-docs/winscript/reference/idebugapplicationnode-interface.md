---
title: "Interfaccia IDebugApplicationNode | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "Interfaccia IDebugApplicationNode"
ms.assetid: 30be3a97-8191-45ac-8706-3f7056c163d6
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Interfaccia IDebugApplicationNode
L'interfaccia `IDebugApplicationNode` estende le funzionalità dell'interfaccia `IDebugDocumentProvider` fornendo un contesto all'interno di una struttura ad albero del progetto.  
  
 Oltre ai metodi ereditati da `IDebugDocumentProvider`, l'interfaccia `IDebugApplicationNode` espone i metodi seguenti.  
  
## Metodi nell'ordine di Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDebugApplicationNode::EnumChildren](../../winscript/reference/idebugapplicationnode-enumchildren.md)|Enumera i nodi figlio del nodo dell'applicazione.|  
|[IDebugApplicationNode::GetParent](../../winscript/reference/idebugapplicationnode-getparent.md)|Restituisce il nodo padre di questo nodo dell'applicazione.|  
|[IDebugApplicationNode::SetDocumentProvider](../../winscript/reference/idebugapplicationnode-setdocumentprovider.md)|Imposta il provider di documento per questo nodo dell'applicazione.|  
|[IDebugApplicationNode::Close](../../winscript/reference/idebugapplicationnode-close.md)|Causa questa applicazione rilasciare tutti i riferimenti e immettere stato inattivo.|  
|[IDebugApplicationNode::Attach](../../winscript/reference/idebugapplicationnode-attach.md)|Aggiunge questo nodo della struttura ad albero del progetto specificato.|  
|[IDebugApplicationNode::Detach](../../winscript/reference/idebugapplicationnode-detach.md)|Rimuove il nodo della struttura ad albero del progetto.|