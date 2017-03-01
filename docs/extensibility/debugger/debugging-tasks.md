---
title: "Attività di debug | Documenti di Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], tasks
ms.assetid: 5d60e9e8-305e-4a48-829f-b9440fc8af7b
caps.latest.revision: 16
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
ms.openlocfilehash: 08f6d64a86982ad7425a2e89815765ce63dbf28c
ms.lasthandoff: 02/22/2017

---
# <a name="debugging-tasks"></a>Attività di debug
Per eseguire il debug di un programma, deve essere avviata e un motore di debug (DE) deve essere collegato a esso, altrimenti il DE deve essere collegato a un programma avviato in precedenza. Una volta collegato, il DE necessario generare determinati eventi di avvio. In risposta, il pacchetto di debug tenta di associare i punti di interruzione impostati nell'IDE. Quando il programma raggiunge un punto di interruzione associato, si interrompe e attende l'input dell'utente.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Problemi di sicurezza](../../extensibility/debugger/security-issues.md)  
 Vengono illustrati i passaggi di sicurezza necessari per eseguire il debug di un programma.  
  
 [Avviare un programma](../../extensibility/debugger/launching-a-program.md)  
 Vengono fornite istruzioni dettagliate su come specificare un DE, che chiama il sistema operativo per avviare il programma.  
  
 [La connessione direttamente a un programma](../../extensibility/debugger/attaching-directly-to-a-program.md)  
 Viene descritto il processo utilizzato per eseguire il debug di un programma in un processo già in esecuzione.  
  
 [L'invio di eventi di avvio dopo il lancio di un](../../extensibility/debugger/sending-startup-events-after-a-launch.md)  
 Elenca gli eventi che si verificano una volta collegato il DE al programma, fino a quando il programma si trova il punto di ingresso principale ed è pronto per il debug.  
  
 [Controllo di esecuzione](../../extensibility/debugger/control-of-execution.md)  
 Viene illustrato come il DE invia in genere un evento punto di ingresso, un evento di completamento di carico o un evento di arresto, a seconda delle circostanze.  
  
 [Associazione dei punti di interruzione](../../extensibility/debugger/binding-breakpoints.md)  
 Viene descritto, se l'utente imposta un punto di interruzione, l'IDE in cui viene creata la richiesta e richiede la sessione di debug per creare il punto di interruzione.  
  
 [La valutazione delle espressioni](../../extensibility/debugger/evaluating-expressions.md)  
 Viene illustrato come creare espressioni e cosa accade quando viene valutata un'espressione.  
  
 [Visualizzazione e la visualizzazione dei dati](../../extensibility/debugger/visualizing-and-viewing-data.md)  
 Viene illustrato come i visualizzatori di tipo e visualizzatori personalizzati sono supportati dall'analizzatore di espressioni (EE).  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Concetti del debugger](../../extensibility/debugger/debugger-concepts.md)  
 Vengono descritti i principali concetti dell'architettura di debug.  
  
 [Componenti del debugger](../../extensibility/debugger/debugger-components.md)  
 Viene fornita una panoramica dei componenti di debug Visual Studio, che includono il DE EE e il gestore dei simboli (SH).  
  
 [Contesti di debugger](../../extensibility/debugger/debugger-contexts.md)  
 Viene illustrato come il DE opera contemporaneamente all'interno di codice, documentazione e contesti di valutazione di espressione. Viene descritto, per ognuno dei tre contesti, il percorso, posizione o valutazione pertinente a esso.  
  
## <a name="see-also"></a>Vedere anche  
 [Introduzione](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
