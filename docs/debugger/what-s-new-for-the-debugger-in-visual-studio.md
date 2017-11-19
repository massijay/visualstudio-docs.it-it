---
title: "Novità relative al Debugger di Visual Studio 2017 | Documenti Microsoft"
ms.custom: 
ms.date: 03/07/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, what's new
- what's new [debugger]
- debugging [Visual Studio], what's new
- what's new [Visual Studio], debugging
ms.assetid: 2aed9caa-2384-4e49-8595-82d8b06cf271
caps.latest.revision: "81"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2a08c56ae60822e6d4183e5789c68cbe383b4dd5
ms.sourcegitcommit: 2c7f48ad6073a81fa927568793633f26cc1f0b15
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="whats-new-for-the-debugger-in-includevsdev15miscincludesvsdev15mdmd"></a>Novità relative al Debugger di[!include[vs_dev15](../misc/includes/vs_dev15_md.md)]

Il debugger include le nuove funzionalità:

- Novità di 15,5, il **Debugger Snapshot** un'istantanea delle applicazioni in produzione quando viene eseguito codice che si è interessati. Per indicare al debugger di eseguire uno snapshot, impostare snappoints e logpoints nel codice. Il debugger consente di vedere esattamente cosa non ha funzionato, senza alcun impatto sul traffico dell'applicazione di produzione. Il Debugger Snapshot consentono di ridurre notevolmente il tempo che necessario per risolvere i problemi che si verificano negli ambienti di produzione.

    Raccolta di snapshot è disponibile per le seguenti App web in esecuzione in Azure App Service:

    * Le applicazioni ASP.NET in esecuzione in .NET Framework 4.6.1 o versioni successive.
    * Applicazioni ASP.NET Core in esecuzione su .NET Core 2.0 o versione successiva in Windows.

    Per ulteriori informazioni, vedere [Debug in tempo reale delle App ASP.NET utilizzando il Debugger Snapshot](../debugger/debug-live-azure-applications.md).

- Novità di 15,5 solo in Visual Studio Enterprise **IntelliTrace passaggio-back** automaticamente un'istantanea dell'applicazione in ogni punto di interruzione e il debugger evento di passaggio. Gli snapshot registrati consentono di tornare indietro per i punti di interruzione precedente o passaggi e visualizzare lo stato dell'applicazione è stato in precedenza. Passaggio back IntelliTrace è possibile risparmiare tempo quando si desidera visualizzare lo stato applicazione precedente ma si desidera riavviare il debug o ricreare lo stato dell'app desiderata.

    È possibile esplorare e visualizzare gli snapshot tramite il **passo indietro** e **passo avanti** pulsanti sulla barra degli strumenti di Debug. Questi pulsanti passare gli eventi che vengono visualizzati di **eventi** nella scheda il **strumenti di diagnostica** finestra.

    ![Passo indietro e Avanti pulsanti](../debugger/media/intellitrace-step-back-icons-description.png  "pulsanti passo indietro e Avanti")

    Per ulteriori informazioni, vedere il [visualizzare snapshot tramite IntelliTrace passaggio-back](../debugger/how-to-use-intellitrace-step-back.md) pagina.

- Il **supporto eccezioni** sostituisce le informazioni sulle eccezioni e visualizzato in una finestra di dialogo non modale in cui si è verificato l'errore. Il **supporto eccezioni** fornisce un accesso più rapido per eventuali eccezioni interne, analisi aggiuntive per il debugger (se disponibile) e l'accesso immediato al **impostazioni eccezioni** per l'eccezione. L'Helper eccezioni possono anche essere trascinata in una vista mobile, se è bloccato da un elemento che si desidera visualizzare.

    Ad esempio, un **NullReferenceException** ora mostra la variabile contenente il riferimento null (informazioni aggiuntive).

    ![Supporto di eccezioni del debugger](../debugger/media/dbg-exception-helper.png "DbgExceptionHelper")

    Per altre informazioni, vedere il post del blog relativo all'[uso del nuovo supporto eccezione in Visual Studio](https://blogs.msdn.microsoft.com/visualstudioalm/2016/03/31/using-the-new-exception-helper-in-visual-studio-15-preview/).

- È ora possibile eseguire una riga di codice durante la pausa nel debugger selezionando il **esecuzione qui** icona freccia verde (l'icona visualizzata durante il passaggio del mouse su una riga di codice). In questo modo si elimina la necessità di impostare punti di interruzione temporanei.

    ![Esecuzione del debugger per fare clic su](../debugger/media/dbg-run-to-click.png "DbgRunToClick") 

- È possibile impostare le condizioni per le eccezioni nel **impostazioni eccezioni** la finestra di dialogo (è possibile farlo tramite il **modifica condizione** icona nella finestra di dialogo Impostazioni eccezioni o utilizzando il menu di scelta rapida nel eccezione). Le condizioni attualmente supportate includono i nomi di modulo da includere o escludere per l'eccezione.

    ![Le condizioni di un'eccezione](../debugger/media/dbg-conditional-exception.png "DbgConditionalException")

- Connettersi al processo, finestra di dialogo include una nuova funzionalità di ricerca che è possibile identificare più rapidamente il processo che si desidera associare a.

    ![Ricerca in Connetti a processo](../debugger/media/dbg-attach-to-process-search.png "DbgAttachToProcessSearch") 

Per ulteriori informazioni su queste nuove funzionalità, vedere il [note sulla versione per [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] ](https://www.visualstudio.com/en-us/news/releasenotes/vs2017-relnotes#debuggingdiag).
  
## <a name="see-also"></a>Vedere anche  
 [Debug in Visual Studio](../debugger/index.md)  
 [Tour delle funzionalità del debugger](../debugger/debugger-feature-tour.md)