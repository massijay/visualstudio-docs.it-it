---
title: "Enumeratore di codice di comando | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "enumeratore di codice di comando"
  - "origine plug-in del controllo, enumerazione di codice di comando"
ms.assetid: 5d2c360c-59e4-4da8-bcb4-dd07c7441e40
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# Enumeratore di codice di comando
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Questo enumeratore viene utilizzato nelle opzioni per la [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) e [SccPopulateList](../extensibility/sccpopulatelist-function.md)per indicare il comando per il quale vengono specificate le opzioni.  
  
## Sintassi  
  
```  
enum SCCCOMMAND {  
   SCC_COMMAND_GET,  
   SCC_COMMAND_CHECKOUT,  
   SCC_COMMAND_CHECKIN,  
   SCC_COMMAND_UNCHECKOUT,  
   SCC_COMMAND_ADD,  
   SCC_COMMAND_REMOVE,  
   SCC_COMMAND_DIFF,  
   SCC_COMMAND_HISTORY,  
   SCC_COMMAND_RENAME,  
   SCC_COMMAND_PROPERTIES,  
   SCC_COMMAND_OPTIONS  
};  
```  
  
## Membri  
 SCC\_COMMAND\_GET  
 Corrisponde al [SccGet](../extensibility/sccget-function.md).  
  
 SCC\_COMMAND\_CHECKOUT  
 Corrisponde al [SccCheckout](../extensibility/scccheckout-function.md).  
  
 SCC\_COMMAND\_CHECKIN  
 Corrisponde al [SccCheckin](../extensibility/scccheckin-function.md).  
  
 SCC\_COMMAND\_UNCHECKOUT  
 Corrisponde al [SccUncheckout](../extensibility/sccuncheckout-function.md).  
  
 SCC\_COMMAND\_ADD  
 Corrisponde al [SccAdd](../extensibility/sccadd-function.md).  
  
 SCC\_COMMAND\_REMOVE  
 Corrisponde al [SccRemove](../extensibility/sccremove-function.md).  
  
 SCC\_COMMAND\_DIFF  
 Corrisponde al [SccDiff](../extensibility/sccdiff-function.md).  
  
 SCC\_COMMAND\_HISTORY  
 Corrisponde al [SccHistory](../extensibility/scchistory-function.md).  
  
 SCC\_COMMAND\_RENAME  
 Corrisponde al [SccRename](../extensibility/sccrename-function.md).  
  
 SCC\_COMMAND\_PROPERTIES  
 Corrisponde al [SccProperties](../extensibility/sccproperties-function.md).  
  
 SCC\_COMMAND\_OPTIONS  
 Corrisponde al [SccSetOption](../extensibility/sccsetoption-function.md).  
  
## Vedere anche  
 [Plug\-in del controllo codice sorgente](../extensibility/source-control-plug-ins.md)   
 [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)   
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)