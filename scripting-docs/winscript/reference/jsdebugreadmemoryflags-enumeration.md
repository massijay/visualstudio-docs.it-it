---
title: "Enumerazione JsDebugReadMemoryFlags | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: JsDebugReadMemoryFlags
apilocation: jscript9diag.dll
ms.assetid: 0d98d154-9cb1-49de-b2df-a2d029d343b7
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Enumerazione JsDebugReadMemoryFlags
Flag per specificare il comportamento durante la lettura della memoria.  
  
## Sintassi  
  
```  
enum JsDebugReadMemoryFlags  
{  
   None = 0,  
   JsDebugAllowPartialRead= 0x1  
} JsDebugReadMemoryFlags;  
```  
  
## Membri  
  
### Valori  
  
|Nome|Descrizione|  
|----------|-----------------|  
|`JsDebugAllowPartialRead`|Indica che il chiamante desidera che venga completata l'operazione di lettura se solo parte della memoria di lettura ha esito positivo.  Se questa proprietà è impostata, verrà generato un errore E\_JsDEBUG\_INVALID\_MEMORY\_ADDRESS solo se "Indirizzo" non è valido.  Se questo flag è cancellato, verrà generato un errore di E\_JsDEBUG\_INVALID\_MEMORY\_ADDRESS se una parte della memoria richiesta è illeggibile.|  
|`None`|Indica che il chiamante desidera il comportamento predefinito per ReadMemory.|  
  
## Requisiti  
 **Intestazione:** jscript9diag.h  
  
## Vedere anche  
 [Riferimenti interfacce Windows Script](../../winscript/reference/windows-script-interfaces-reference.md)