---
title: "Errore DCOM durante il tentativo di contattare il computer remoto. Accesso negato. | Microsoft Docs"
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
  - "vs.debug.remote.dcom_access_denied"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
helpviewer_keywords: 
  - "DCOM, errori di accesso"
  - "errore di accesso remoto DCOM negato"
  - "debug remoto, errore DCOM"
ms.assetid: 9d7dfc1b-9fe0-4f54-9c50-9c0e0f8358c5
caps.latest.revision: 27
caps.handback.revision: 27
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Errore DCOM durante il tentativo di contattare il computer remoto. Accesso negato.
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Il debug remoto usa DCOM per la comunicazione tra i computer locale e remoto nelle situazioni seguenti:  
  
-   Il debugger è impostato sulla **modalità di compatibilità nativa** oppure è selezionata l'opzione **Modalità di compatibilità gestita** nella pagina **Strumenti \/ Opzioni \/ Debug**  
  
-   Si esegue il debug di codice C\+\+ \(C\+\+ \/CLI\) gestito.  
  
-   In Visual Studio 2013, quando è selezionata l'opzione **Abilita Modifica e continuazione nativo** nella pagina **Strumenti \/ Opzioni \/ Debug**  
  
-   Alcuni scenari di debug di terze parti  
  
 Questo errore si verifica quando il processo di Visual Studio non è in grado di autenticarsi \(o le credenziali fornite sono ritenute insufficienti\) rispetto al processo del debugger remoto su DCOM. Una o più delle soluzioni seguenti possono risolvere il problema:  
  
-   Disattivare **Usa modalità di compatibilità nativa** e **Modalità di compatibilità gestita**.  
  
-   In Visual Studio 2013 disattivare **Abilita Modifica e continuazione nativo**.  
  
-   Riavviare entrambi i computer.  
  
-   Se il debug remoto richiede l'immissioni di credenziali, selezionare l'opzione per salvarle.  
  
## Vedere anche  
 [Errori e risoluzione dei problemi relativi al debug remoto](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Debug remoto](../debugger/remote-debugging.md)