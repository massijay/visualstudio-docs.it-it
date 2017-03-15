---
title: "VSG_DEFAULT_RUN_FILENAME | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ea549d2f-c857-458c-93c7-bc5a2d11d15d
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# VSG_DEFAULT_RUN_FILENAME
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Definisce il nome predefinito del file di log degli elementi grafici.  
  
## Sintassi  
  
```cpp  
#define VSG_DEFAULT_FILENAME filename  
```  
  
#### Parametri  
 `filename`  
 Il nome predefinito del file di log degli elementi grafici quando le informazioni grafiche vengono acquisite a livello di codice.  
  
## Valore  
 Un valore letterale stringa che rappresenta il nome del file di log degli elementi grafici.  Per impostazione predefinita, L"default.vsglog".  
  
```cpp  
#define VSG_DEFAULT_FILENAME L"default.vsglog"  
```  
  
## Note  
 Se viene definito il simbolo `DONT_SAVE_VSGLOG_TO_TEMP` del preprocessore, il nome del file è relativo alla directory corrente dell'applicazione acquisita, o ad un percorso assoluto; in caso contrario, è relativo alla directory dei file temporanei dell'utente e non può essere un percorso assoluto.  
  
 Per modificare il nome del file specificato, è necessario ridefinirlo prima di includere `vsgcapture.h` nel programma.  
  
## Esempio  
 In questo esempio viene illustrato come modificare il nome predefinito del file di acquisizione:  
  
```cpp  
// Redefine the default capture filename before including vsgcapture.h  
#define VSG_DEFAULT_FILENAME L"capture.vsglog"  
  
#include <vsgcapture.h>  
```  
  
## Vedere anche  
 [DONT\_SAVE\_VSGLOG\_TO\_TEMP](../debugger/dont-save-vsglog-to-temp.md)