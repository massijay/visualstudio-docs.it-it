---
title: "Interfaccia IDebugProperty | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "Interfaccia IDebugProperty"
ms.assetid: 7e8f5341-23ef-4029-814d-f5c2307b9203
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Interfaccia IDebugProperty
Utilizzato per descrivere una proprietà gerarchica di entità che viene eseguito il debug con un nome, un tipo e un valore.  In genere, `IDebugProperty` viene utilizzato per descrivere il risultato della valutazione di un'espressione, valutazione dell'istruzione, o valutazione di log.  
  
## Metodi nell'ordine Vtable  
 Nella tabella seguente sono elencati i metodi di interfaccia `IDebugProperty`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDebugProperty::GetPropertyInfo](../../winscript/reference/idebugproperty-getpropertyinfo.md)|Ottenere `DebugPropertyInfo` che descrive il `IDebugProperty``.`|  
|[IDebugProperty::GetExtendedInfo](../../winscript/reference/idebugproperty-getextendedinfo.md)|Ottiene le informazioni estese di una proprietà.|  
|[IDebugProperty::SetValueAsString](../../winscript/reference/idebugproperty-setvalueasstring.md)|Imposta il valore di una proprietà in una stringa.|  
|[IDebugProperty::EnumMembers](../../winscript/reference/idebugproperty-enummembers.md)|Enumera i membri di una proprietà.|  
|[IDebugProperty::GetParent](../../winscript/reference/idebugproperty-getparent.md)|Ottiene il padre di una proprietà.|  
  
## Requisiti  
 Intestazione: dbgprop.h