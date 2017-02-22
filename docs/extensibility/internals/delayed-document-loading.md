---
title: "Documento caricamento ritardato | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fb07b8e2-a4e3-4cb0-b04f-8eb11c491f35
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# Documento caricamento ritardato
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Quando si riapre una soluzione Visual Studio, è possibile che la maggior parte dei documenti associati non vengono caricata immediatamente. La cornice della finestra documento viene creata in uno stato in attesa di inizializzazione e un documento di segnaposto \(chiamato frame stub\) viene inserito nel documento di tabella in esecuzione \(RDT\).  
  
 L'estensione potrebbe caricare inutilmente eseguendo una query di elementi nei documenti prima che vengano caricati i documenti di progetto. In questo modo migliorano il footprint di memoria globale per Visual Studio.  
  
## Caricamento di documenti  
 Il frame di stub e il documento sono completamente inizializzati quando l'utente accede al documento, ad esempio, selezionare la scheda della cornice della finestra. Il documento può anche essere inizializzato da un'estensione che richiede i dati del documento, l'accesso a RDT direttamente per acquisire i dati del documento o l'accesso indiretto il RDT effettuando una delle seguenti chiamate:  
  
-   La cornice della finestra show \(metodo\): <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>.  
  
-   La cornice della finestra metodo GetProperty <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> in qualsiasi delle seguenti proprietà:  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
 Se l'estensione utilizza il codice gestito, non è necessario chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> a meno che non si è certi che il documento non è nello stato in sospeso inizializzazione o si desidera che il documento sia completamente inizializzata... Infatti, questo metodo restituisce sempre il documento oggetto dati, creandolo se necessario. In alternativa, è necessario chiamare uno dei metodi sull'interfaccia IVsRunningDocumentTable4.  
  
 Se l'estensione utilizza C\+\+, è possibile passare `null` per i parametri non desiderate.  
  
 È possibile evitare il caricamento di documenti non necessari chiamando uno dei metodi seguenti prima che per le proprietà rilevanti: prima che per le altre proprietà.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> utilizzando <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID6>.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A>. Questo metodo restituisce un <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> oggetto che include un valore per <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> Se il documento non è ancora stato inizializzato.  
  
 È possibile scoprire quando un documento è stato caricato per la sottoscrizione all'evento RDT che viene generato quando un documento è completamente inizializzato. Esistono due possibilità:  
  
-   Se l'evento sink implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2>, è possibile sottoscrivere <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2.OnAfterAttributeChangeEx%2A>,  
  
-   In caso contrario, è possibile sottoscrivere <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterAttributeChange%2A>.  
  
 Di seguito è riportato uno scenario di accesso ai documenti ipotetico. Visual Studio estensione desidera visualizzare alcune informazioni sui documenti aperti, ad esempio la modifica è bloccare conteggio e qualcosa i dati del documento. Enumera i documenti in RDT utilizzando <xref:Microsoft.VisualStudio.Shell.Interop.IEnumRunningDocuments>, quindi chiama <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> per ogni documento per recuperare i dati di conteggio e documento di blocco modifica. Se il documento è nello stato in attesa di inizializzazione, che richiede i dati del documento rende inutilmente da inizializzare.  
  
 Un modo più efficace di procedere consiste nell'usare <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentEditLockCount%2A> per ottenere il conteggio dei blocchi di modifica e quindi utilizzare <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A> per determinare se il documento è stato inizializzato. Se non sono includono i flag <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4>, il documento è già stato inizializzato e che richiede i dati del documento con <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentData%2A> non determina le inizializzazioni non necessarie. Se si include il flag <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4>, l'estensione deve evitare di richiedere i dati del documento fino a quando non viene inizializzato il documento. Questa condizione può essere rilevata nel gestore eventi OnAfterAttributeChange\(Ex\).  
  
## Test di estensioni per vedere se forzano l'inizializzazione  
 Non esiste alcun riferimento visivo per indicare se un documento è stato inizializzato, pertanto può essere difficile scoprire se l'estensione viene forzato l'inizializzazione. È possibile impostare una chiave del Registro di sistema che facilita la verifica, poiché costringe il titolo di ogni documento che non è completamente inizializzato per contenere il testo `[Stub]` nel titolo.  
  
 In **HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\14.0\\BackgroundSolutionLoad\]**, impostare **StubTabTitleFormatString** a **{0} \[Stub\]**.