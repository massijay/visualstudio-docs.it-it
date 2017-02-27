---
title: "Procedura: utilizzare Modifica e continuazione (C#) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Modifica e continuazione [C#], informazioni"
ms.assetid: 40e136d8-a08c-43bd-b313-fb821c55eb3c
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# Procedura: utilizzare Modifica e continuazione (C#)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La funzionalità Modifica e continuazione per C\# consente di apportare modifiche al codice in modalità di interruzione durante il debug.  Le modifiche possono essere applicate senza terminare e riavviare la sessione di debug.  
  
 Modifica e continuazione viene richiamato automaticamente quando si apportano modifiche in modalità di interruzione e quindi si sceglie un comando di esecuzione del debugger, ad esempio **Continua**, **Esegui** o **Imposta istruzione successiva**, oppure si valuta una funzione in una finestra del debugger.  
  
> [!NOTE]
>  Modifica e Continuazione non è supportato quando si esegue il debug, Compact Framework, codice ottimizzato, codice misto nativo\/gestito o codice di integrazione di CLR \(Common Language Runtime\) in SQL Server.  Se si tenta di apportare modifiche al codice in uno di questi scenari, verrà visualizzata una finestra di dialogo per segnalare che Modifica e continuazione non è supportato.  
  
### Per richiamare automaticamente Modifica e continuazione  
  
1.  In modalità di interruzione apportare una modifica al codice sorgente.  
  
2.  Scegliere **Continua**, **Esegui** o **Imposta istruzione successiva** dal menu **Debug** oppure valutare una funzione in una finestra del debugger.  
  
     Il nuovo codice verrà compilato e il debug proseguirà con questo codice.  Alcune modifiche non sono supportate in Modifica e continuazione.  Per ulteriori informazioni, vedere [Modifiche al codice supportate \(C\#\)](../debugger/supported-code-changes-csharp.md).  
  
### Per abilitare o disabilitare Modifica e continuazione  
  
1.  Scegliere **Opzioni** dal menu **Strumenti**.  
  
2.  Nella finestra di dialogo **Opzioni** espandere il nodo **Debug** e selezionare **Modifica e continuazione**.  
  
3.  Nella pagina **Modifica e continuazione** della finestra di dialogo **Opzioni** selezionare o deselezionare la casella di controllo **Attiva Modifica e continuazione**.  
  
     Questa impostazione verrà applicata quando si riavvierà la sessione di debug.  
  
## Vedere anche  
 [Modifica e continuazione \(Visual C\#\)](../debugger/edit-and-continue-visual-csharp.md)   
 [Modifiche al codice supportate \(C\#\)](../debugger/supported-code-changes-csharp.md)   
 [Errori e avvisi di Modifica e continuazione \(C\#\)](../misc/edit-and-continue-errors-and-warnings-csharp.md)