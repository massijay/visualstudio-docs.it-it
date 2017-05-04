---
title: "Enumerazione SCRIPTLANGUAGEVERSION | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 58aa904a-e3ed-41c6-82d6-e91c8279a792
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Enumerazione SCRIPTLANGUAGEVERSION
Specifica le versioni possibili di script.  
  
## Sintassi  
  
```cpp  
typedef enum tagSCRIPTLANGUAGEVERSION  
{  
    SCRIPTLANGUAGEVERSION_DEFAULT = 0,  
    SCRIPTLANGUAGEVERSION_5_7  = 1,  
    SCRIPTLANGUAGEVERSION_5_8  = 2,  
    SCRIPTLANGUAGEVERSION_MAX  = 255  
} SCRIPTLANGUAGEVERSION ;  
  
```  
  
## Valori di enumerazione  
  
|||  
|-|-|  
|SCRIPTLANGUAGEVERSION\_DEFAULT|Versione predefinita.  Il valore Integer è 0.|  
|SCRIPTLANGUAGEVERSION\_5\_7|Versione 5,7 di script windows.  Il valore Integer è 1.|  
|SCRIPTLANGUAGEVERSION\_5\_8|Versione 5,8 di script windows.  Il valore Integer è 2.|  
|SCRIPTLANGUAGEVERSION\_MAX|La versione massima.  Il valore Integer è 255.|  
  
## Vedere anche  
 [Costanti, enumerazioni e codici di errore dello script ActiveX](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)