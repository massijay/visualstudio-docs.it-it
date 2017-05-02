---
title: "Windows Script Host | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Windows Script Host, host di implementazione"
ms.assetid: 9d5f6471-b318-40f3-be01-d9cd0b1cdd47
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Windows Script Host
Nell'implementazione dell'host di Microsoft Windows Script, è possibile creare in modo sicuro presumere che un motore di scripting chiama solo l'interfaccia di [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) nel contesto del thread di base che l'host esegue le operazioni seguenti:  
  
-   Selezionare un thread di base \(in genere il thread che contiene il ciclo di messaggi\).  
  
-   Creare un'istanza del motore di scripting nel thread di base.  
  
-   Metodi del motore di scripting di chiamate solo dal thread di base, a eccezione di quanto in particolare valido, come in caso di [IActiveScript::InterruptScriptThread](../winscript/reference/iactivescript-interruptscriptthread.md) e di [IActiveScript::Clone](../winscript/reference/iactivescript-clone.md).  
  
-   Chiama l'oggetto di invio del motore di scripting solo dal thread di base.  
  
-   Assicurarsi che il ciclo di messaggi viene eseguito nel thread di base se l'handle della finestra vengono fornite.  
  
-   Garantisce che gli oggetti in eventi di origine del modello a oggetti dell'host solo nel thread di base.  
  
 Queste regole vengono automaticamente seguite da tutti gli host a thread singolo.  Il modello finito descritto in precedenza viene intenzionalmente sufficiente separato consentire a un host arrestare uno script verrebbe chiamando [IActiveScript::InterruptScriptThread](../winscript/reference/iactivescript-interruptscriptthread.md) da un altro thread \(avviato da un gestore di CTRL\+INTERR e così via\), o possibile clonare uno script in un nuovo thread utilizzando [IActiveScript::Clone](../winscript/reference/iactivescript-clone.md).  
  
## Note  
 Nessuna di queste restrizioni applicate a un host che sceglie di applicare un'interfaccia a thread libero di [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) e un modello a oggetti a thread libero.  Tale host può utilizzare l'interfaccia di [IActiveScript](../winscript/reference/iactivescript.md) da qualsiasi thread, senza restrizioni.  
  
## Vedere anche  
 [\<PAVE OVER\> Interfacce di Microsoft Windows Script \- Introduzione](../Topic/%3CPAVE%20OVER%3E%20Microsoft%20Windows%20Script%20Interfaces%20-%20Introduction.md)