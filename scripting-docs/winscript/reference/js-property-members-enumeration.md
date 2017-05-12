---
title: "Enumerazione JS_PROPERTY_MEMBERS | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: JS_PROPERTY_MEMBERS
apilocation: jscript9diag.dll
ms.assetid: 3b870e5c-5518-4073-8384-f0c9c1777d9e
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Enumerazione JS_PROPERTY_MEMBERS
Flag per specificare il tipo di informazioni da restituire in una richiesta per i membri di un oggetto.  
  
## Sintassi  
  
```  
enum JS_PROPERTY_MEMBERS  
{  
   JS_PROPERTY_MEMBERS_ALL = 0,  
   JS_PROPERTY_MEMBERS_ARGUMENTS = 1  
} JS_PROPERTY_MEMBERS;  
```  
  
## Membri  
  
### Valori  
  
|Nome|Descrizione|  
|----------|-----------------|  
|`JS_PROPERTY_MEMBERS_ALL`|Rappresenta una richiesta di enumerare tutti i membri.|  
|`JS_PROPERTY_MEMBERS_ARGUMENTS`|Rappresenta una richiesta di enumerare solo gli argomenti.|  
  
## Requisiti  
 **Intestazione:** jscript9diag.h  
  
## Vedere anche  
 [Riferimenti interfacce Windows Script](../../winscript/reference/windows-script-interfaces-reference.md)