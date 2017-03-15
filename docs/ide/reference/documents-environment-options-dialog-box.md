---
title: "Documenti, Ambiente, finestra di dialogo Opzioni | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.Environment.Documents"
  - "VS.ToolsOptionsPages.Environment.Documents"
  - "VS.ToolsOptionsPag.Environment.Documents"
helpviewer_keywords: 
  - "Documenti, Ambiente, finestra di dialogo Opzioni"
  - "impostazioni predefinite, directory"
  - "messaggi di errore, personalizzazione"
  - "file [Visual Studio], opzioni predefinite"
  - "file [Visual Basic], caricamento automatico dati modificati"
  - "Windows, personalizzazione dell'ambiente"
  - "modifica in memoria"
  - "cartelle [Visual Studio], specifica del percorso del file aperto"
  - "Apri file (finestra di dialogo)"
  - "Windows, abilitazione del riutilizzo dell'elemento corrente"
  - "notifiche, file modificati"
  - "file [Visual Studio], visualizzazione in Esplora soluzioni"
  - "directory predefinite"
  - "file di sola lettura, modifica"
  - "Finestra di dialogo Opzioni, visualizzazione file esterni"
  - "directory [Visual Studio], opzioni dell'ambiente IDE"
  - "Finestra di dialogo Opzioni, pagina Documenti"
  - "avvisi, file modificati"
  - "Esplora soluzioni, visualizzazione file"
ms.assetid: 4e3ccf1b-cd68-4db6-9470-710c911b47fc
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 21
---
# Documenti, Ambiente, finestra di dialogo Opzioni
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Utilizzare questa pagina della finestra di dialogo **Opzioni** per controllare la visualizzazione dei documenti nell'ambiente di sviluppo integrato \(IDE\) e gestire le modifiche esterne apportate ai documenti e ai file.  Per visualizzare questa finestra di dialogo, scegliere **Opzioni** dal menu **Strumenti** e selezionare **Documenti** nel nodo **Ambiente**.  Se **Documenti** non è presente nell'elenco, selezionare **Mostra tutte le impostazioni** nella finestra di dialogo **Opzioni**.  
  
> [!NOTE]
>  Le opzioni disponibili nelle finestre di dialogo e i nomi e le posizioni dei comandi di menu visualizzati potrebbero non corrispondere a quelli descritti nella Guida in quanto dipendono dall'edizione o dalle impostazioni in uso.  Per modificare le impostazioni, scegliere **Importa\/esporta impostazioni** dal menu **Strumenti**.  Per ulteriori informazioni, vedere [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/it-it/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 **Riutilizza la finestra del documento corrente, se salvato**  
 Quando si seleziona questa opzione, il documento corrente viene chiuso, se è stato salvato, e viene aperto un nuovo documento nella stessa finestra.  Se il documento corrente non è stato salvato, rimane aperto e il nuovo documento viene aperto in una finestra distinta.  Quando l'opzione viene deselezionata, i nuovi documenti vengono sempre aperti in finestre distinte.  
  
 Se non si eseguono spesso operazioni con i comandi Taglia e Incolla in più documenti e si desidera ridurre al minimo il numero di finestre e documenti aperti nello spazio di lavoro, si consiglia di attivare questa opzione.  
  
 **Rileva quando il file viene modificato al di fuori dell'ambiente**  
 Quando questa opzione è selezionata, viene immediatamente visualizzato un messaggio per comunicare che sono state apportate modifiche a un file aperto utilizzando un editor al di fuori dell'IDE.  Il messaggio consente di ricaricare il file dal dispositivo in cui è memorizzato.  
  
 **Carica modifiche automaticamente, se salvate**  
 Quando la casella di controllo **Rileva quando il file viene modificato al di fuori dell'ambiente** è selezionata e un file aperto nell'IDE viene modificato al di fuori dell'IDE, per impostazione predefinita viene generato un messaggio di avviso.  Se questa opzione è attivata, non viene visualizzato alcun avviso e il documento viene ricaricato nell'IDE per rendere disponibili le modifiche esterne.  
  
 **Consenti modifica dei file in sola lettura, avvisa al tentativo di salvataggio**  
 Quando questa opzione è attivata, è possibile aprire e modificare un file in sola lettura.  Al termine, è necessario utilizzare il  **Salva con nome**comando per salvare il file con un nuovo nome se si desidera salvare un record delle modifiche.  
  
 **Apri file utilizzando directory documento attivo**  
 Quando questa opzione è selezionata, nella finestra di dialogo **Apri file** verrà visualizzata la directory del documento attivo.  Se l'opzione viene deselezionata, nella finestra di dialogo **Apri file** verrà visualizzata l'ultima directory utilizzata per aprire un file.  
  
 **Verifica coerenza terminazioni riga al caricamento**  
 Selezionare questa opzione se si desidera che l'editor analizzi le terminazioni di riga e visualizzi una finestra di messaggio nel caso in cui vengano rilevate incoerenze nella formattazione delle terminazioni.  
  
 **Visualizza avviso se l'annullamento globale avrà effetto sui file modificati**  
 Selezionare questa opzione per visualizzare una finestra di messaggio quando il comando **Annullamento globale** ripristina le modifiche di refactoring apportate nei file modificati anche dopo l'operazione di refactoring.  Il ripristino dello stato pre\-refactoring di un file può comportare l'annullamento delle modifiche successive apportate al file.  
  
 **Mostra file esterni in Esplora soluzioni**  
 Selezionare questa opzione per visualizzare il nodo **File esterni** in **Esplora soluzioni**.  I file esterni sono file non associati a una soluzione o a un progetto, ma che possono essere visualizzati in **Esplora soluzioni** per comodità.  
  
> [!NOTE]
>  Selezionare questa opzione per attivare il comando **Visualizza nel browser** nel menu **File** per i documenti Web non inclusi nell'applicazione Web attiva.  
  
 **\<** *n* **\> elementi salvati nel progetto di file vari**  
 Specifica il numero di file da rendere persistenti nella cartella **File esterni** di **Esplora soluzioni**.  Tali file vengono elencati anche se non sono più aperti in un editor.  È possibile immettere un numero intero compreso tra 0 e 256.  Il numero predefinito è 0.  
  
 Ad esempio, se questa opzione viene impostata su 5 e vi sono 10 file esterni aperti, quando tutti i 10 file vengono chiusi i primi cinque verranno ancora visualizzati nella cartella **File esterni**.  
  
 **Salva documenti come Unicode quando i dati non possono essere salvati nella tabella codici**  
 Se si seleziona questa opzione, i file contenenti informazioni non compatibili con la tabella codici selezionata verranno salvati in formato Unicode per impostazione predefinita.  
  
## Vedere anche  
 [Finestra di dialogo Opzioni ambiente](../../ide/reference/environment-options-dialog-box.md)   
 [File esterni](../../ide/reference/miscellaneous-files.md)   
 [Ricerca e sostituzione di testo](../../ide/finding-and-replacing-text.md)