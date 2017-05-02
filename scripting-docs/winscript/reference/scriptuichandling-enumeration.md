---
title: "Enumerazione SCRIPTUICHANDLING | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 5b89c6e8-064c-406f-bb14-91c77bf42daf
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Enumerazione SCRIPTUICHANDLING
Rappresenta il modo in cui il controllo dell'interfaccia utente deve essere gestito.  
  
## Sintassi  
  
```vb  
typedef enum tagSCRIPTUICHANDLING {   
    SCRIPTUICHANDLING_ALLOW = 0,   
    SCRIPTUICHANDLING_NOUIERROR = 1,   
    SCRIPTUICHANDLING_NOUIDEFAULT = 2,   
} SCRIPTUICHANDLING;  
  
```  
  
## Valore di enumerazione  
  
|||  
|-|-|  
|SCRIPTUICHANDLING\_ALLOW|Abilitare il controllo da visualizzare.|  
|SCRIPTUICHANDLING\_NOUIERROR||  
|SCRIPTUICHANDLING\_NOUIDEFAULT||