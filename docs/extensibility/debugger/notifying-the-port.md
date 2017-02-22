---
title: "La porta di notifica | Microsoft Docs"
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
  - "porte, notifica"
ms.assetid: f9fce48e-7d4e-4627-a0fb-77b75428146a
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# La porta di notifica
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Dopo aver avviato un programma, la porta deve essere passate, come segue:  
  
1.  Quando una porta riceve un nuovo nodo del programma, invia un evento di creazione del programma di nuovo la sessione di debug.  l'evento porta con un'interfaccia che rappresenta il programma.  
  
2.  La sessione di debug eseguire una query sul programma per l'identificatore del \(DE\) modulo di debug che può connettersi.  
  
3.  I controlli della sessione di debug per verificare se il DE in elenco di DES valido per tale programma.  La sessione di debug ottiene questo elenco dalle impostazioni del programma attivo della soluzione, originariamente si passa dal package di debug.  
  
     Il DE deve essere nell'elenco valido, o il DE non verrà connesso al programma.  
  
 A livello di codice, quando una porta innanzitutto riceve un nuovo nodo del programma, crea un'interfaccia di [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) per rappresentare il programma.  
  
> [!NOTE]
>  Questa operazione non deve essere confusa con l'interfaccia di `IDebugProgram2` creata in un secondo momento nel motore di \(DE\) debug.  
  
 La porta invia un evento di creazione del programma di [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) di nuovo all'amministratore di debug della sessione \(SDM\) mediante un'interfaccia COM `IConnectionPoint` .  
  
> [!NOTE]
>  Questa operazione non deve essere confusa con l'interfaccia di `IDebugProgramCreateEvent2` , che viene inviata in un secondo momento da DE.  
  
 Con l'interfaccia eventi stessa, la porta invia rispettivamente le interfacce di [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md), di [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)e di [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) , che rappresentano la porta, il processo e il programma.  Lo SDM chiama [IDebugProgram2:: GetEngineInfo](../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md) per ottenere il GUID di DE che può eseguire il debug del programma.  Il GUID è stato originariamente ottenuto dall'interfaccia di [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) .  
  
 I controlli di SDM verifica se il DE in elenco di DES valido.  Lo SDM ottiene questo elenco dalle impostazioni del programma attivo della soluzione, originariamente si passa dal package di debug.  Il DE deve essere nell'elenco valido, o non verrà connesso al programma.  
  
 L'identità di DE è nota alla volta, lo SDM è pronta per associarlo al programma.  
  
## Vedere anche  
 [Avviare un programma](../../extensibility/debugger/launching-a-program.md)   
 [Dopo il lancio di un collegamento](../../extensibility/debugger/attaching-after-a-launch.md)   
 [Attività di debug](../../extensibility/debugger/debugging-tasks.md)