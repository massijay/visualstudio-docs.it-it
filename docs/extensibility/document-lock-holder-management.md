---
title: Gestione titolare di un blocco di documenti | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], custom - document locking
ms.assetid: fa1ce513-eb7d-42bc-b6e8-cb2433d051d5
caps.latest.revision: 21
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
ms.openlocfilehash: a78ee74a210f544ad4f9d97a9d2457bdf9d70988
ms.lasthandoff: 02/22/2017

---
# <a name="document-lock-holder-management"></a>Gestione dei documenti blocco titolare
La tabella di documento in esecuzione (RDT) mantiene un conteggio dei documenti aperti e i blocchi di modifica che hanno. È possibile inserire un blocco di modifica su un documento di RDT quando viene modificata a livello di codice in background senza visualizzare un documento aperto in una finestra del documento. Questa funzionalità viene spesso utilizzata nelle finestre di progettazione che modificano più file tramite un'interfaccia utente grafica.  
  
## <a name="document-lock-holder-scenarios"></a>Scenari di titolare di un blocco del documento  
  
### <a name="file-a-has-a-dependence-on-file-b"></a>File di una dipendenza dal File "a" con "b"  
 Si consideri una situazione in cui si implementa un editor standard "A" per il tipo di file "a" e tutti i file di tipo "a" contiene un riferimento a (o dipendenza) un file di tipo "b". Un editor standard di "B" non esiste per i file di tipo "b". Quando viene aperto l'editor "A" file "a" it recupera il riferimento al file corrispondente, "b". File "b" non è visualizzato, ma può essere modificato editor "A". Editor "A" Ottiene un riferimento ai dati del documento del file "b" dal <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A>metodo e gestisce inoltre un blocco di modifica nel file "b".</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> Al termine dell'editor "A" modifica dei file "b" è possibile diminuire il blocco di modifica contare su file "b" chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A>(metodo).</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A> È possibile omettere questo passaggio se fosse stato chiamato il <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A>metodo con il parametro `dwRDTLockType` impostata su <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>.</xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> </xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A>  
  
### <a name="file-b-is-opened-by-a-different-editor"></a>File "b" viene aperto un Editor diverso  
 Nel caso in cui il file "b" è già aperto da editor "B" quando "A" editor tenta di aprirlo, esistono due scenari separati per gestire:  
  
-   Se il file "b" è aperto in un editor compatibile, è necessario disporre dell'editor "A" Registra un blocco di modifica del documento sull'utilizzo di file "b" il <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A>(metodo).</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A> Dopo l'editor "A" modifica il file "b", annullare la registrazione del documento Modifica blocco usando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnregisterDocumentLockHolder%2A>(metodo).</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnregisterDocumentLockHolder%2A>  
  
-   Se il file "b" è aperto in una modalità incompatibile, è possibile consentire l'apertura di file "b" tentativo dall'editor "A" hanno esito negativo oppure è possibile consentire la visualizzazione associata editor "A" parzialmente apre e visualizza un messaggio di errore appropriato. Il messaggio di errore dovrebbe indicare all'utente di chiudere il file "b" in editor non compatibile e quindi aprire nuovamente file "a" tramite editor "A". È anche possibile implementare il [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable2.QueryCloseRunningDocument%2A>per richiedere all'utente di chiudere il file "b" che viene aperto nell'editor non compatibile.</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable2.QueryCloseRunningDocument%2A> Se l'utente chiude il file "b", l'apertura del file "a" editor in "A" proseguirà normalmente.  
  
## <a name="additional-document-edit-lock-considerations"></a>Considerazioni sul blocco di modifica documenti aggiuntive  
 Per ottenere un comportamento diverso editor "A" è l'unico editor che dispone di un documento Modifica blocco sul file "b", quello che si avrebbe se editor "B" contiene inoltre un documento Modifica blocco nel file "b". In [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], **Progettazione classi** è un esempio di finestra di progettazione visiva che non dispone di un blocco di modifica del file di codice associato. Vale a dire, se l'utente ha un diagramma classi aperto in visualizzazione progettazione e aprire il file di codice associato contemporaneamente e se l'utente modifica il file di codice ma non salva le modifiche, le modifiche sono perse al file di diagramma (con estensione CD) della classe. Se il **Progettazione classi** ha il solo documento Modifica blocco per il file di codice, l'utente non viene chiesto di salvare le modifiche quando si chiude il file di codice. L'IDE chiede all'utente di salvare le modifiche solo dopo che l'utente chiude il **Progettazione classi**. Le modifiche salvate vengono riflesse in entrambi i file. Se entrambi i **Progettazione classi** e l'editor di file di codice mantenuti blocchi di modifica del documento nel file di codice, quindi l'utente viene richiesto di salvare quando si chiude il file di codice o del form. A questo punto le modifiche salvate vengono applicate sia il form e il file di codice. Per ulteriori informazioni sui diagrammi classi, vedere [utilizzo dei diagrammi classi (Progettazione classi)](../ide/working-with-class-diagrams-class-designer.md).  
  
 Si noti che se è necessario inserire un blocco di modifica per un documento per un editor diverso, è necessario implementare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder>interfaccia.</xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder>  
  
 Molte volte un progettista dell'interfaccia utente che modifica i file di codice a livello di codice apporta modifiche a più di un file. In questi casi il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell2.SaveItemsViaDlg%2A>metodo gestisce il salvataggio di uno o più documenti tramite il **si desidera salvare le modifiche apportate agli elementi seguenti?** la finestra di dialogo.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell2.SaveItemsViaDlg%2A>  
  
## <a name="see-also"></a>Vedere anche  
 [Tabella Document in esecuzione](../extensibility/internals/running-document-table.md)   
 [Persistenza e la tabella del documento in esecuzione](../extensibility/internals/persistence-and-the-running-document-table.md)
