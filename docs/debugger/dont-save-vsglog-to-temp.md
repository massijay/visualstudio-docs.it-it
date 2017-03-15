---
title: "DONT_SAVE_VSGLOG_TO_TEMP | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f27ab0e6-9575-4ca0-9901-37d3e5c3a2f5
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DONT_SAVE_VSGLOG_TO_TEMP
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Definisce, grazie all propria presenza, se il file di log degli elementi grafici viene salvato nella directory dei file temporanei dell'utente.  
  
## Sintassi  
  
```cpp  
#define DONT_SAVE_VSGLOG_TO_TEMP  
```  
  
## Valore  
 Un simbolo del preprocessore che grazie alla propria presenza o assenza determina se il file di log degli elementi grafici viene salvato nella directory dei file temporanei dell'utente.  Se questo simbolo viene definito, il nome del file specificato da `VSG_DEFAULT_RUN_FILENAME` è relativo alla directory corrente dell'applicazione acquisita, o è il percorso assoluto; in caso contrario, il nome del file specificato da `VSG_DEFAULT_RUN_FILENAME` è relativo alla directory dei file temporanei dell'utente e non può essere un percorso assoluto.  
  
## Note  
 A seconda dei privilegi dell'utente, il file di log degli elementi grafici potrebbe non poter essere salvato in un percorso arbitrario.  È consigliabile salvare il log degli elementi grafici nella directory dei file temporanei dell'utente, o un'altra buona posizione conosciuta, se non si è certi che l'utente possegga i permessi di scrittura per il percorso voluto.  
  
 Per evitare che il file di log degli elementi grafici venga salvato nella directory di file temporanei, è necessario definire `DONT_SAVE_VSGLOG_TO_TEMP` prima di includere `vsgcapture.h`.  
  
## Esempio  
 In questo esempio viene illustrato come salvare il file di log degli elementi grafici in un percorso assoluto del computer host.  
  
```  
// Define DONT_SAVE_VSGLOG_TO_TEMP and VSG_DEFAULT_RUN_FILENAME before including vsgcapture.h  
#define DONT_SAVE_VSGLOG_TO_TEMP  
#define VSG_DEFAULT_RUN_FILENAME L"C:\\Graphics Diagnostics Captures\\default.vsglog"  
  
#include <vsgcapture.h>  
  
```  
  
## Vedere anche  
 [VSG\_DEFAULT\_RUN\_FILENAME](../debugger/vsg-default-run-filename.md)