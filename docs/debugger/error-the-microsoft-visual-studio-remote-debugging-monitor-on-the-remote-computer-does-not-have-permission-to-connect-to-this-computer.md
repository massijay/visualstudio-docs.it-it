---
title: "Errore: Microsoft Visual Studio Remote Debugging Monitor sul computer remoto non dispone dell&#39;autorizzazione per connettersi al computer. | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.access_denied_oncallback"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "debug remoto, errore di versione di Windows"
ms.assetid: ba08a59b-6dbc-4bbc-9c52-379d3bf5241f
caps.latest.revision: 21
caps.handback.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Errore: Microsoft Visual Studio Remote Debugging Monitor sul computer remoto non dispone dell&#39;autorizzazione per connettersi al computer.
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Questo errore si verifica quando l'utente che tenta di eseguire Visual Studio Remote Debugging Monitor \(msvsmon\) non dispone di un account nel computer locale.  
  
### Per risolvere il problema  
  
-   Aggiungere un account utente al computer host del debugger di Visual Studio, con lo stesso nome e password dell'account utente che esegue msvsmon nel computer remoto.  
  
     \-oppure\-  
  
-   Eseguire msvsmon utilizzando un account utente che dispone dell'autorizzazione per l'invio di chiamate nel computer locale,  ovvero di un account utente configurato come utente di dominio e amministratore nel computer in cui è in esecuzione msvsmon.  L'account utente per l'esecuzione di msvsmon può essere specificato in due diversi modi:  
  
    -   Fare clic con il pulsante destro del mouse sull'icona di msvsmon e scegliere **Esegui come** dal menu di scelta rapida.  
  
     \-oppure\-  
  
    -   Al prompt dei comandi, digitare `runas.exe`.  
  
## Vedere anche  
 [Debug remoto tra i domini](../Topic/Remote%20Debugging%20Across%20Domains.md)   
 [Errori e risoluzione dei problemi relativi al debug remoto](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Debug remoto](../debugger/remote-debugging.md)