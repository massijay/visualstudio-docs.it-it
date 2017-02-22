---
title: "GETNAME_TYPE | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "GETNAME_TYPE"
helpviewer_keywords: 
  - "Enumerazione GETNAME_TYPE"
ms.assetid: 2f9f1679-e9e8-4c9c-ac90-aa07bfe69914
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# GETNAME_TYPE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

specifica il tipo di nome di file per recuperare.  
  
## Sintassi  
  
```cpp#  
enum enum_GETNAME_TYPE {   
   GN_NAME         = 0,  
   GN_FILENAME     = 1,  
   GN_BASENAME     = 2,  
   GN_MONIKERNAME  = 3,  
   GN_URL          = 4,  
   GN_TITLE        = 5,  
   GN_STARTPAGEURL = 6  
};  
typedef DWORD GETNAME_TYPE;  
```  
  
```c#  
public enum enum_GETNAME_TYPE {   
   GN_NAME         = 0,  
   GN_FILENAME     = 1,  
   GN_BASENAME     = 2,  
   GN_MONIKERNAME  = 3,  
   GN_URL          = 4,  
   GN_TITLE        = 5,  
   GN_STARTPAGEURL = 6  
};  
```  
  
## Membri  
 GN\_NAME  
 Specifica un nome descrittivo del documento o del contesto.  
  
 GN\_FILENAME  
 Specifica il percorso completo del documento o del contesto.  
  
 GN\_BASENAME  
 Specifica un nome di file di base anziché un percorso completo del documento o del contesto.  
  
 GN\_MONIKERNAME  
 Specifica un nome univoco del documento o del contesto sotto forma di moniker.  
  
 GN\_URL  
 Specifica il nome dell'URL del documento o del contesto.  
  
 GN\_TITLE  
 Specifica il titolo del documento, se presente.  
  
 GN\_STARTPAGEURL  
 Ottiene la pagina iniziale URL per i processi.  
  
## Note  
 Questi valori vengono passati come parametri [GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md), [GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)i [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md) metodi e per specificare il tipo di nome restituire.  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)   
 [GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)   
 [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)