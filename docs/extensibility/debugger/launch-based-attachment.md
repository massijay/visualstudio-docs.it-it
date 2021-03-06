---
title: Attacco basato su avvio | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debug engines, launching
- debug engines, attaching to programs
ms.assetid: 362f00ac-1909-4a3a-bacb-c0ceb5549816
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2aa9787ad432e402375680c4e27e433236b13249
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="launch-based-attachment"></a>Basato su avvio allegato
Basato su avvio allegato a un programma è automatica. Quando il processo che ospita il programma viene avviato dal suo SDM, basato su avvio allegato segue un percorso simile a quella del metodo allegato manuale. Per informazioni, vedere [collegamento al programma](../../extensibility/debugger/attaching-to-the-program.md).  
  
## <a name="the-attaching-process"></a>Il processo di collegamento  
 La differenza principale è la sequenza di eventi dopo il **collegamento** chiamare, come indicato di seguito:  
  
1.  Inviare un **IDebugEngineCreateEvent2** oggetto evento per il SDM. Per informazioni dettagliate, vedere [l'invio di eventi](../../extensibility/debugger/sending-events.md).  
  
2.  Chiamare il `IDebugProgram2::GetProgramId` metodo il **IDebugProgram2** interfaccia passata al **Connetti** metodo.  
  
3.  Inviare un **IDebugProgramCreateEvent2** oggetto evento per notificare il SDM che locale **IDebugProgram2** oggetto è stato creato per rappresentare il programma per la Germania.  
  
4.  Inviare un [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) oggetto evento per notificare il SDM che viene creato un nuovo thread per il processo che ha avviato.  
  
## <a name="see-also"></a>Vedere anche  
 [Inviare gli eventi richiesti](../../extensibility/debugger/sending-the-required-events.md)   
 [Abilitazione di un programma da sottoporre a debug](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)