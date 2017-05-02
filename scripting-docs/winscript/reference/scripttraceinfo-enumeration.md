---
title: "Enumerazione SCRIPTTRACEINFO | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: cb8a4767-8c8e-4fa0-a735-038767a8c500
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Enumerazione SCRIPTTRACEINFO
Rappresenta l'evento di script che sta analizzando.  Utilizzato in [Metodo IActiveScriptSiteTraceInfo::SendScriptTraceInfo](../../winscript/reference/iactivescriptsitetraceinfo-sendscripttraceinfo-method.md).  
  
## Sintassi  
  
```  
typedef enum tagSCRIPTTRACEINFO {    
    SCRIPTTRACEINFO_SCRIPTSTART = 0,    
    SCRIPTTRACEINFO_SCRIPTEND   = 1,    
    SCRIPTTRACEINFO_COMCALLSTART    = 2,    
    SCRIPTTRACEINFO_COMCALLEND  = 3,    
    SCRIPTTRACEINFO_CREATEOBJSTART  = 4,    
    SCRIPTTRACEINFO_CREATEOBJEND    = 5,    
    SCRIPTTRACEINFO_GETOBJSTART = 6,    
    SCRIPTTRACEINFO_GETOBJEND   = 7,    
} SCRIPTTRACEINFO ;  
```  
  
## Valori di enumerazione  
  
|||  
|-|-|  
|SCRIPTTRACEINFO\_SCRIPTSTART|l'inizio di uno script.|  
|SCRIPTTRACEINFO\_SCRIPTEND|La fine dello script.|  
|SCRIPTTRACEINFO\_COMCALLSTART|L'inizio di una chiamata COM.|  
|SCRIPTTRACEINFO\_COMCALLEND|La fine di una chiamata COM.|  
|SCRIPTTRACEINFO\_CREATEOBJSTART|L'inizio della creazione di un oggetto.|  
|SCRIPTTRACEINFO\_CREATEOBJEND|Fine della creazione di un oggetto.|  
|SCRIPTTRACEINFO\_GETOBJSTART|L'inizio di una chiamata GetObject.|  
|SCRIPTTRACEINFO\_GETOBJEND|La fine di una chiamata GetObject.|