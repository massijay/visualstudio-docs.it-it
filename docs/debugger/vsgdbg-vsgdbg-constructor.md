---
title: "VsgDbg::VsgDbg (costruttore) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 670651e6-5e79-4845-b0c2-671beb7055a8
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# VsgDbg::VsgDbg (costruttore)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Costruisce un'istanza della classe `VsgDbg` con o senza la preparazione del componente di diagnostica grafica integrato nell'applicazione per acquisire e registrare attivamente le informazioni grafiche basate, per impostazione predefinita, sul parametro booleano specificato.  
  
## Sintassi  
  
```cpp  
VsgDbg(  
  bDefaultInit  
);  
```  
  
#### Parametri  
 `bDefaultInit`  
 `true` per specificare che il componente di diagnostica grafica integrato nell'applicazione deve essere preparato ad acquisire e registrare attivamente le informazioni grafiche; `false` per specificare che per il momento l'applicazione non deve essere preparata attivamente ad acquisire e registrare le informazioni grafiche.  
  
## Note  
 Quando il costruttore viene chiamato con `bDefaultInit` impostato a `true`, il nome del file di log degli elementi grafici viene determinato dal modo in cui i simboli del preprocessore `VSG_DEFAULT_RUN_FILENAME` `DONT_SAVE_VSGLOG_TO_TEMP` sono definiti prima di includere `vsgcapture.h` nell'applicazione.  
  
 Quando il costruttore viene chiamato con `bDefaultInit` impostato a `false`, il componente di diagnostica di grafica integrato nell'applicazione può essere preparato attivamente ad acquisire e registrare le informazioni grafiche in un secondo momento chiamando la funzione `Init`.  
  
## Vedere anche  
 [VsgDbg::~VsgDbg \(distruttore\)](../debugger/vsgdbg-tilde-vsgdbg-destructor.md)   
 [Init](../debugger/init.md)   
 [DONT\_SAVE\_VSGLOG\_TO\_TEMP](../debugger/dont-save-vsglog-to-temp.md)   
 [VSG\_DEFAULT\_RUN\_FILENAME](../debugger/vsg-default-run-filename.md)