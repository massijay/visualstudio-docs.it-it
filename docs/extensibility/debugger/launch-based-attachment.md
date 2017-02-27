---
title: "Basato su avvio allegato | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "motori di debug, l'avvio"
  - "motori di debug, connessione a programmi"
ms.assetid: 362f00ac-1909-4a3a-bacb-c0ceb5549816
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# Basato su avvio allegato
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

a allegato basato su avvio di un programma è automatico.  Quando l'hosting del programma viene avviato da SDM, a allegato basato su avvio segue un percorso simile a quello del metodo manuale degli allegati.  Per informazioni, vedere [Connettendo al programma](../../extensibility/debugger/attaching-to-the-program.md).  
  
## Il processo la connessione  
 La differenza principale è la sequenza di eventi che seguono la chiamata di **Connessione** , come segue:  
  
1.  Inviare un oggetto evento di **IDebugEngineCreateEvent2** a SDM.  Per informazioni dettagliate, vedere [L'invio di eventi](../../extensibility/debugger/sending-events.md).  
  
2.  Chiamare il metodo di `IDebugProgram2::GetProgramId` sull'interfaccia di **IDebugProgram2** passata al metodo di **Connessione** .  
  
3.  Inviare un oggetto evento di **IDebugProgramCreateEvent2** per notificare allo SDM che l'oggetto locale di **IDebugProgram2** è stato creato per rappresentare il programma a DE.  
  
4.  Inviare un oggetto evento di [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) per notificare allo SDM che viene creato un nuovo thread per il processo che ha avviato.  
  
## Vedere anche  
 [Inviare gli eventi richiesti](../../extensibility/debugger/sending-the-required-events.md)   
 [Abilitazione di un programma da sottoporre a debug](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)