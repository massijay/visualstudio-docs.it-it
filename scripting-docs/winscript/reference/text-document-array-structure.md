---
title: "Struttura TEXT_DOCUMENT_ARRAY | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "Struttura TEXT_DOCUMENT_ARRAY"
ms.assetid: 47c08f23-981b-4105-9240-6dfffc6cb91b
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Struttura TEXT_DOCUMENT_ARRAY
Matrice di oggetti [Interfaccia IDebugDocumentText](../../winscript/reference/idebugdocumenttext-interface.md).  I membri vengono allocati con CoTaskMemAlloc.  
  
## Sintassi  
  
```  
typedef struct tagTEXT_DOCUMENT_ARRAY  
{  
    DWORD dwCount;  
    [size_is(dwCount)] IDebugDocumentText **Members;  
} TEXT_DOCUMENT_ARRAY;  
  
```  
  
## Membri  
 `dwCount`  
 Il numero di documenti.  
  
 `Members`  
 Il set di documenti.  
  
## Vedere anche  
 [Costanti, enumerazioni e strutture del debugger di script ActiveX](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)