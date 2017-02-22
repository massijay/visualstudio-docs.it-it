---
title: "Eseguire il debug del pacchetto | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "debug [Debugging SDK], pacchetti"
ms.assetid: 99947fd4-fb87-4c69-b26c-65634e17d285
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# Eseguire il debug del pacchetto
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Le esecuzioni del pacchetto di debug in Visual Studio sgusciano e gestire un'interfaccia utente.  Utilizza le interfacce di debug di Visual Studio e comunica con l'amministratore \(SDM\) di debug della sessione.  
  
 Arrestare gli eventi generati con lo SDM superano il debugger dalla modalità di esecuzione nella modalità di interruzione e modificano lo stato attivo al programma in cui si è verificata.  Il pacchetto di debug tiene traccia dello stack frame e il thread dalle informazioni inviate dagli eventi.  
  
 Il pacchetto di debug senza dipendenze dell'ambiente di runtime o del linguaggio.  Non è necessario distribuire o modificare il pacchetto di debug.  
  
 Il pacchetto di debug viene implementata da vsdebug.dll.  
  
## Vedere anche  
 [Gestione sessione di Debug](../../extensibility/debugger/session-debug-manager.md)   
 [Stack frame](../../extensibility/debugger/stack-frames.md)   
 [Thread](../../extensibility/debugger/threads.md)   
 [Componenti del debugger](../../extensibility/debugger/debugger-components.md)