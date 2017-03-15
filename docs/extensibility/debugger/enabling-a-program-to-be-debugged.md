---
title: Abilitazione di un programma da sottoporre a debug | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], enabling for programs
ms.assetid: 61d24820-0cd9-48b6-8674-6813f7493237
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 66daff038c7556a693964d5dabc4de054990d791
ms.lasthandoff: 02/22/2017

---
# <a name="enabling-a-program-to-be-debugged"></a>Abilitazione di un programma da sottoporre a debug
Prima che il motore di debug (DE) può eseguire il debug di un programma, è necessario avviare il DE o collegarlo a un programma esistente.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Recupero di una porta](../../extensibility/debugger/getting-a-port.md)  
 Viene descritto come ottenere una porta come il primo passaggio per abilitare un programma da sottoporre a debug.  
  
 [Il programma di registrazione](../../extensibility/debugger/registering-the-program.md)  
 Viene illustrato il passaggio successivo all'attivazione di un programma da sottoporre a debug: registrarlo con la porta. Una volta registrato, il programma di debug può essere eseguito tramite il processo di collegamento o il debug just-in-time (JIT).  
  
 [Collegamento al programma](../../extensibility/debugger/attaching-to-the-program.md)  
 Viene illustrato il passaggio successivo: collegare il debugger al programma.  
  
 [Basato su Avvio collegamento](../../extensibility/debugger/launch-based-attachment.md)  
 Viene descritto basato su avvio allegato a un programma, che risulta automatico all'avvio dal suo SDM.  
  
 [Inviare gli eventi richiesti](../../extensibility/debugger/sending-the-required-events.md)  
 Procedura per gli eventi richiesti durante la creazione di un motore di debug (DE) e associarla a un programma.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Creazione di un motore di Debug personalizzato](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 Definisce un motore di debug (DE) e vengono descritti i servizi implementati tramite le interfacce DE e come possono causare il debugger per la transizione tra le diverse modalità operative.
