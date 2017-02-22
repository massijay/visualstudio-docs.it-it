---
title: "Tabella Document in esecuzione | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "blocchi di lettura"
  - "tabella di documento in esecuzione (RDT), interfaccia IVsDocumentLockHolder"
  - "tabella document in esecuzione (RDT)"
  - "tabella di documento in esecuzione (RDT), blocchi di modifica"
  - "oggetti dati documento, l'esecuzione tabella document"
ms.assetid: bbec74f3-dd8e-48ad-99c1-2df503c15f5a
caps.latest.revision: 18
caps.handback.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
---
# Tabella Document in esecuzione
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

L'IDE gestisce l'elenco di tutti i documenti aperti in una struttura interna denominata tabella document \(RDT\) in esecuzione. Questo elenco include tutti i documenti aperti in memoria, indipendentemente dal fatto che questi documenti sono in corso di modifica. Un documento è un elemento in modo permanente, inclusi i file in un progetto o file di progetto principale \(ad esempio, un file con estensione vcxproj\).  
  
## Elementi della tabella Document in esecuzione  
 La tabella documento in esecuzione contiene le voci seguenti.  
  
|Elemento|Descrizione|  
|--------------|-----------------|  
|Moniker del documento|Stringa che identifica in modo univoco l'oggetto dati di documento. Ciò potrebbe essere il percorso file assoluto per un sistema di progetto che gestisce i file \(ad esempio, C:\\MyProject\\MyFile\). Questa stringa viene utilizzata anche per i progetti salvati in archivi diverso dal file System, ad esempio stored procedure in un database. In questo caso, il sistema del progetto creare una stringa univoca che può riconoscere e possibilmente analizzare per determinare come archiviare il documento.|  
|Proprietario di gerarchia|Oggetto gerarchia a cui appartiene il documento, come rappresentato da un <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> interfaccia.|  
|ID elemento|Identificatore dell'elemento di un elemento specifico all'interno della gerarchia. Questo valore è univoco tra tutti i documenti nella gerarchia proprietario di questo documento, ma questo valore non deve necessariamente essere univoco in gerarchie diverse.|  
|Oggetto dati documento|Come minimo, si tratta di un `IUnknown`<br /><br /> . L'IDE non richiede alcuna particolare interfaccia oltre il `IUnknown` interfaccia per l'oggetto dati di un editor personalizzato documento. Tuttavia, per un editor standard di implementazione dell'editor del <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> interfaccia è necessaria per gestire le chiamate di persistenza file dal progetto. Per altre informazioni, vedere [Salvare un documento Standard](../../extensibility/internals/saving-a-standard-document.md).|  
|Flag|Flag che controllano se il documento viene salvato, se viene applicato un blocco di lettura o modifica e così via, può essere specificati quando vengono aggiunte voci per il RDT. Per ulteriori informazioni, vedere il <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> enumerazione.|  
|Conteggio dei blocchi di modifica|Conteggio dei blocchi di modifica. Un blocco di modifica indica che alcuni editor presenta il documento aperto per la modifica. Quando il conteggio dei blocchi di modifica passa a zero, l'utente viene richiesto di salvare il documento, se è stato modificato. Ad esempio, ogni volta che si apre un documento in un editor utilizzando il **nuova finestra** comando, viene aggiunto un blocco di modifica per il documento nel RDT. Affinché un blocco di modifica da impostare, il documento deve disporre di una gerarchia o ID elemento|  
|Conteggio dei blocchi in lettura|Conteggio dei blocchi in lettura. Un blocco di lettura indica che viene letto il documento tramite un meccanismo, ad esempio una procedura guidata. Un blocco di lettura contiene un documento attivo nel RDT continuando a indicare che il documento non può essere modificato. È possibile impostare un blocco di lettura, anche se il documento non dispone di una gerarchia o ID elemento Questa funzionalità consente di aprire un documento in memoria e immetterlo nel RDT senza il documento da proprietà di qualsiasi gerarchia. Questa funzionalità viene utilizzata raramente.|  
|Titolare del blocco|Un'istanza di un <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> interfaccia. Il detentore del blocco viene implementato dalle funzionalità, quali procedure guidate che è possibile aprire e modificano i documenti all'esterno di un editor. Un proprietario di blocco consente la funzionalità aggiungere un blocco di modifica al documento per impedire che il documento viene chiuso mentre è in corso di modifica. In genere, modificare i blocchi vengono aggiunti solo per le finestre di documento \(ovvero, Editor\).|  
  
 Ogni voce di RDT dispone di una gerarchia univoca o ID dell'elemento associato, che corrisponde in genere a un nodo del progetto. Tutti i documenti disponibili per la modifica in genere sono di proprietà da una gerarchia. Voci di RDT controllano il progetto, o, in modo più accurato, quale gerarchia appartiene l'oggetto dati di documento in fase di modifica. Utilizzando le informazioni di RDT, l'IDE può impedire un documento viene aperto da più progetti contemporaneamente.  
  
 La gerarchia inoltre controlla la persistenza dei dati e utilizza le informazioni di RDT per aggiornare il **salvare** e **Salva con nome** le finestre di dialogo. Quando l'utente modifica un documento e quindi scegliere il **uscita** comando il **File** menu, l'IDE richiesto con il **Save Changes** la finestra di dialogo per visualizzare tutti i progetti e gli elementi del progetto attualmente vengono modificati. Ciò consente agli utenti di scegliere quali i documenti da salvare. L'elenco dei documenti per salvare \(vale a dire i documenti che contengono modifiche\) viene generato dal RDT. Tutti gli elementi che si prevedono di vedere il **Save Changes** la finestra di dialogo dopo l'uscita dell'applicazione deve avere i record nel RDT. Il RDT coordina i documenti vengono salvati e se viene chiesto all'utente su un salvataggio operazione utilizzando i valori specificati nella voce del flag per ogni documento. Per ulteriori informazioni sui flag di RDT, vedere il <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> enumerazione.  
  
## Blocchi di modifica e blocchi di lettura  
 Blocchi di modifica e blocchi di lettura si trovano nel RDT. Di incrementi di finestra di documento e decrementa bloccare la modifica. Pertanto, quando un utente apre una nuova finestra del documento, il blocco di modifica conteggio incrementa di uno. Quando il numero di blocchi di modifica raggiunge lo zero, la gerarchia viene segnalata di rendere persistente o salvare i dati per il documento associato. La gerarchia può quindi rendere persistenti i dati in qualsiasi modo, compresi il salvataggio come file o come un elemento in un repository. È possibile utilizzare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.LockDocument%2A> metodo nel <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> interfaccia per aggiungere blocchi di modifica e i blocchi di lettura e la <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A> per rimuovere tali blocchi.  
  
 In genere, quando viene creata un'istanza di finestra del documento per un editor, la cornice della finestra vengono automaticamente aggiunti un blocco di modifica per il documento di RDT. Tuttavia, se si crea una visualizzazione personalizzata di un documento che non utilizza una finestra del documento standard \(ovvero, non implementa il <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> interfaccia\), quindi è necessario impostare il proprio blocco di modifica. Ad esempio, in una procedura guidata, il documento viene modificato senza venire aperto in un editor. Affinché blocchi del documento deve essere aperto da procedure guidate e le entità simili, è necessario implementare queste entità di <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> interfaccia. Per registrare il detentore del blocco del documento, chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A> metodo e passare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> implementazione. In questo modo aggiunge il RDT il detentore del blocco del documento. Un altro scenario per l'implementazione di un contenitore di blocco del documento è se si apre un documento tramite una finestra degli strumenti speciali. In questo caso, non si riesce a chiudere il documento di finestra degli strumenti. Tuttavia, la registrazione come proprietario di blocco un documento nel RDT, l'IDE può chiamare l'implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder.CloseDocumentHolder%2A> metodo per richiedere una chiusura del documento.  
  
## Altri usi della tabella Document in esecuzione  
 Altre entità nell'IDE di utilizzare il RDT per ottenere informazioni sui documenti. Ad esempio, il gestore di controllo di origine utilizza il RDT per comunicare al sistema per ricaricare un documento nell'editor, dopo aver ottenuto la versione più recente del file. A tale scopo, il gestore di controllo di origine cerca i file in RDT per verificare se uno di essi sono aperto. Se sono, quindi il gestore di controllo di origine verifica innanzitutto che implementa la gerarchia di <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> metodo. Se il progetto non implementa il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> \(metodo\), quindi l'origine controllare gestione controlli per l'implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> metodo sull'oggetto document di dati direttamente.  
  
 L'IDE utilizza inoltre il RDT per resurface \(portare in primo piano\) un documento aperto, se un utente richiede che il documento. Per altre informazioni, vedere [Visualizzazione di file utilizzando il comando Apri File](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md). Per determinare se un file viene aperto nel RDT, effettuare una delle seguenti.  
  
-   Query per il moniker del documento \(ovvero, il percorso del documento completo\) scoprire se l'elemento è aperto.  
  
-   Utilizzare l'ID di gerarchia o un elemento chiede al sistema di progetto per il percorso completo dei documenti e quindi cercare l'elemento nel RDT.  
  
## Vedere anche  
 [Utilizzo di RDT\_ReadLock](../../extensibility/internals/rdt-readlock-usage.md)   
 [Persistenza e la tabella del documento in esecuzione](../../extensibility/internals/persistence-and-the-running-document-table.md)