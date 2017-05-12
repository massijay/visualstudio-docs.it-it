---
title: "Costanti TEXT_DOC_ATTR | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: TEXT_DOC_ATTR
apilocation: scrobj.dll
helpviewer_keywords: 
  - "Costanti TEXT_DOC_ATTR"
ms.assetid: fd9c53a4-8f73-4c6a-abe5-6b831ecd5b1e
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Costanti TEXT_DOC_ATTR
Descrivere gli attributi del documento.  
  
## Sintassi  
  
```  
typedef DWORD TEXT_DOC_ATTR;  
```  
  
## Costanti  
  
|Costante|Valore|Descrizione|  
|--------------|------------|-----------------|  
|TEXT\_DOC\_ATTR\_READONLY|0x00000001|Documento di sola lettura.|  
|TEXT\_DOC\_ATTR\_TYPE\_PRIMARY|0x00000002|Il documento è il file primario di questa struttura ad albero del documento.|  
|TEXT\_DOC\_ATTR\_TYPE\_WORKER|0x00000004|Il documento è un thread di lavoro.|  
|TEXT\_DOC\_ATTR\_TYPE\_SCRIPT|0x00000008|Il documento è un file script.|  
  
## Vedere anche  
 [Costanti, enumerazioni e strutture del debugger di script ActiveX](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)