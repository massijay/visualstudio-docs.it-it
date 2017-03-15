---
title: Finestra di dialogo Progetti e soluzioni, Opzioni | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Projects and Solutions Options dialog box
- Options dialog box, Projects and Solutions
ms.assetid: 2801f24e-a138-488a-ae3c-e1f99a678ac0
caps.latest.revision: 12
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
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
translationtype: Human Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 5c6c36ca969d5ca9ca3957a886ce45597159bc5c
ms.lasthandoff: 02/22/2017

---
# <a name="projects-and-solutions-options-dialog-box"></a>Progetti e soluzioni, Opzioni (finestra di dialogo)
Imposta il percorso predefinito delle cartelle di progetto [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] e determina il comportamento predefinito della finestra **Output**, dell'**Elenco attività** e di **Esplora soluzioni** durante lo sviluppo e la compilazione dei progetti. Per accedere a questa finestra di dialogo, fare clic su **Strumenti/Opzioni**, espandere **Progetti e soluzioni** e fare clic su **Generale**.  
  
> [!NOTE]
>  Le opzioni disponibili nelle finestre di dialogo e i nomi e i percorsi dei comandi di menu visualizzati potrebbero non corrispondere a quelli descritti nella Guida a seconda dell'edizione o delle impostazioni attive. Questo argomento della Guida è stato creato tenendo presente le **Impostazioni generali per lo sviluppo**. Per visualizzare o modificare le impostazioni, scegliere **Importa/Esporta impostazioni** dal menu **Strumenti**. Per altre informazioni, vedere [Personalizzazione delle impostazioni di sviluppo in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="settings"></a>Impostazioni  
 **Percorso progetti**  
 Imposta il percorso predefinito in cui vengono create nuovi cartelle e directory di progetti e soluzioni. Anche diverse finestre di dialogo usano il percorso impostato in questa opzione come punto di partenza della cartella. Ad esempio, la finestra di dialogo Apri progetto usa questo percorso per il collegamento Progetti.  
  
 **Percorso dei modelli di progetto utente**  
 Imposta il percorso predefinito usato dalla finestra di dialogo **Nuovo progetto** per creare l'elenco **Modelli personali**. Per altre informazioni, vedere [Procedura: Individuare e organizzare modelli](../../ide/how-to-locate-and-organize-project-and-item-templates.md).  
  
 **Percorso dei modelli di elemento utente**  
 Imposta il percorso predefinito usato dalla finestra di dialogo **Aggiungi nuovo elemento** per creare l'elenco **Modelli personali**. Per altre informazioni, vedere [Procedura: Individuare e organizzare modelli](../../ide/how-to-locate-and-organize-project-and-item-templates.md).  
  
 **Mostra sempre Elenco errori se la compilazione finisce con errori**  
 Apre la finestra **Elenco errori** al completamento della compilazione, ma solo se la compilazione di un progetto non è riuscita. Vengono visualizzati gli errori che si sono verificati durante il processo di compilazione. Quando questa opzione è deselezionata, gli errori si verificano ugualmente, ma la finestra non verrà aperta una volta completata la compilazione. Questa opzione è attivata per impostazione predefinita.  
  
 **Tieni traccia degli elementi attivi in Esplora soluzioni**  
 Se selezionata, **Esplora soluzioni** viene aperto automaticamente e l'elemento attivo viene selezionato. L'elemento selezionato cambia quando si lavora con diversi file in un progetto o soluzione oppure componenti diversi in una finestra di progettazione. Quando questa opzione è deselezionata, la selezione in **Esplora soluzioni** non viene modificata automaticamente. Questa opzione è attivata per impostazione predefinita.  
  
 **Mostra configurazioni della build avanzate**  
 Se selezionata, le opzioni di configurazione di compilazione vengono visualizzate nella finestra di dialogo **Pagine delle proprietà** del progetto e nella finestra di dialogo **Pagine delle proprietà** della soluzione. Se deselezionata, le opzioni di configurazione di compilazione non vengono visualizzate nella finestra di dialogo **Pagine delle proprietà** del progetto e nella finestra di dialogo **Pagine delle proprietà** della soluzione per i progetti [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] e [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] che contengono una sola configurazione oppure le due configurazioni debug e rilascio. Se un progetto ha una configurazione definita dall'utente, verranno visualizzate le opzioni di configurazione di compilazione.  
  
 Se è deselezionata, i comandi del menu **Compila**, ad esempio **Compila soluzione**, **Ricompila soluzione** e **Pulisci soluzione**, vengono eseguiti nella configurazione Rilascio e i comandi dal menu **Debug**, ad esempio **Avvia il debug** e **Avvia senza eseguire debug**, vengono eseguiti nella configurazione Debug.  
  
 **Mostra sempre soluzione**  
 Se selezionata, la soluzione e tutti i comandi che agiscono sulle soluzioni vengono sempre visualizzati nell'IDE. Se deselezionata, tutti i progetti vengono creati come progetti autonomi e la soluzione non viene visualizzata in Esplora soluzioni o i comandi che agiscono sulle soluzioni non vengono visualizzati nell'IDE se la soluzione contiene un solo progetto.  
  
 **Salva nuovi progetti alla creazione**  
 Se selezionata, è possibile specificare un percorso per il progetto nella finestra di dialogo **Nuovo progetto**. Se deselezionata, tutti i nuovi progetti vengono creati come progetti temporanei. Quando si lavora con i progetti temporanei, è possibile creare ed effettuare prove con un progetto senza dover specificare un percorso sul disco.  
  
 **Avvisa utente quando il percorso del progetto non è attendibile**  
 Se si prova a creare un nuovo progetto o ad aprire un progetto esistente in una posizione non completamente attendibile (ad esempio, in un percorso UNC o un percorso HTTP), verrà visualizzato un messaggio. Usare questa opzione per specificare se il messaggio viene visualizzato ogni volta che si prova a creare o ad aprire un progetto in una posizione non completamente attendibile.  
  
 **Mostra finestra di output a inizio compilazione**  
 Consente di visualizzare automaticamente la finestra di Output nell'IDE all'inizio delle compilazioni della soluzione. Per altre informazioni, vedere [Procedura: Controllare la finestra di output](http://msdn.microsoft.com/Library/91aebd15-8854-4a7a-9f7d-57376fb4e858). Questa opzione è attivata per impostazione predefinita.  
  
 **Richiedi ridenominazione simbolica quando vengono rinominati i file**  
 Se selezionata, viene visualizzata una finestra di messaggio che richiede se [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] deve rinominare anche tutti i riferimenti nel progetto all'elemento di codice.  
  
## <a name="see-also"></a>Vedere anche  
 [Finestra di dialogo Opzioni, Progetti e soluzioni, Compila ed esegui](../../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md)
