---
title: "IActiveScriptGarbageCollector::CollectGarbage | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 75f77c49-2190-4d49-a3e0-9dcf847c502b
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IActiveScriptGarbageCollector::CollectGarbage
L'host attiva script chiama questo metodo per avviare l'operazione di Garbage Collection.  
  
## Sintassi  
  
```  
HRESULT CollectGarbage(  
        SCRIPTGCTYPE scriptgctype  
    );  
  
```  
  
#### Parametri  
 `scriptgctype`  
 \[in\] [Enumerazione SCRIPTGCTYPE](../../winscript/reference/scriptgctype-enumeration.md) che specifica se eseguire un Garbage Collection normale o approfondita.  
  
## Valore restituito  
 Restituisce un HRESULT.  
  
## Vedere anche  
 [Interfaccia IActiveScriptGarbageCollector](../../winscript/reference/iactivescriptgarbagecollector-interface.md)