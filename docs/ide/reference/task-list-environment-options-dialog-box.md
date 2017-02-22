---
title: "Elenco attivit&#224;, Ambiente, finestra di dialogo Opzioni | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ToolsOptionsPages.Environment.Task_List"
  - "VS.ToolsOptionsPag.Environment.Task_List"
  - "VS.ToolsOptionsPages.Environment.TaskList"
  - "VS.Environment.Task List"
helpviewer_keywords: 
  - "Elenco dei token"
  - "token"
  - "icone, Elenco attività"
  - "Elenco attività, personalizzazione dell'ambiente"
  - "Finestra di dialogo Opzioni, ambiente Elenco attività"
  - "punti esclamativi"
  - "commenti, attività di commento nell'Elenco attività"
  - "token, Elenco attività"
  - "Elenco attività, attività di commento"
ms.assetid: 88327e04-fa3e-48db-995b-ad89e0dc4ed2
caps.latest.revision: 15
caps.handback.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Elenco attivit&#224;, Ambiente, finestra di dialogo Opzioni
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Questa pagina Opzioni permette di aggiungere, eliminare e modificare i token di commento che generano promemoria di **Elenco attività**.  Per visualizzare queste impostazioni, scegliere **Opzioni** dal menu **Strumenti**, espandere la cartella **Ambiente** e quindi scegliere **Elenco attività**.  
  
## Opzioni di Elenco attività  
 Chiedi conferma prima di eliminare un'attività  
 Quando questa opzione è selezionata, viene visualizzata una finestra di messaggio ogni volta che un'attività utente viene eliminata da **Elenco attività**, in modo da poter confermare l'eliminazione.  Questa opzione è selezionata per impostazione predefinita.  
  
> [!NOTE]
>  Per eliminare il commento di un'attività, usare il collegamento per trovare il commento e quindi rimuoverlo dal codice.  
  
 Mostra solo nomi file  
 Quando questa opzione è selezionata, la colonna **File** di **Elenco attività** mostra solo i nomi dei file da modificare e non i percorsi completi.  
  
## Token  
 Quando si inserisce un commento nel codice il cui testo inizia con un token proveniente da **Elenco token**, **Elenco attività** visualizza il commento come nuova voce ogni volta che il file viene aperto per la modifica.  È possibile fare clic su questa voce di **Elenco attività** per passare direttamente alla riga del commento nel codice.  Per altre informazioni, vedere [Utilizzo dell'elenco attività](../../ide/using-the-task-list.md).  
  
 Elenco dei token  
 Visualizza un elenco di token e permette di aggiungere o rimuovere token personalizzati.  I token di commento fanno distinzione tra maiuscole e minuscole in Visual C\# e Visual C\+\+, ma non in Visual Basic.  
  
> [!NOTE]
>  Se non si digita il token desiderato esattamente come è specificato in **Elenco token**, non verrà visualizzata alcuna attività di commento in **Elenco attività**.  
  
 Priorità  
 Imposta la priorità delle attività che usano il token selezionato.  I commenti delle attività che iniziano con questo token vengono automaticamente associati alla priorità designata in **Elenco attività**.  
  
 Nome  
 Immettere la stringa del token.  Viene abilitato il pulsante **Aggiungi**.  In **Aggiungi** questa stringa viene inclusa in **Elenco token** e i commenti che iniziano con questo nome verranno visualizzati in **Elenco attività**.  
  
 Add  
 Pulsante abilitato quando si immette un nuovo nome in **Nome**.  Fare clic su questa opzione per aggiungere la stringa di un nuovo token usando i valori immessi nei campi **Nome** e **Priorità**.  
  
 Eliminare  
 Fare clic su questa opzione per eliminare il token selezionato da **Elenco token**.  Non è possibile eliminare il token di commento predefinito.  
  
 Cambia  
 Fare clic su questa opzione per apportare modifiche a un token esistente usando i valori immessi nei campi **Nome** e **Priorità**.  
  
> [!NOTE]
>  Non è possibile rinominare o eliminare il token di commento predefinito, ma è possibile modificarne il livello di priorità.  
  
## Vedere anche  
 [Utilizzo dell'elenco attività](../../ide/using-the-task-list.md)   
 [Impostazione di segnalibri nel codice](../../ide/setting-bookmarks-in-code.md)   
 [Finestra di dialogo Opzioni ambiente](../../ide/reference/environment-options-dialog-box.md)