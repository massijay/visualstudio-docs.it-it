---
title: "Salvare un documento Standard | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "editor [Visual Studio SDK], salvataggio di documenti standard"
  - "progetti [Visual Studio SDK], salvataggio di documenti standard"
  - "persistenza, il salvataggio di documenti standard"
ms.assetid: d692fedf-b46e-4d60-84bd-578635042235
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# Salvare un documento Standard
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Gli handle dell'ambiente di salvataggio, salvataggio come e salvare tutti i controlli.  Quando un utente seleziona **Salvare**, **Salva con nome**, o **Salva tutto** dal menu File o si chiude la soluzione, con conseguente **Salva tutto**, il seguente processo si verifica.  
  
 ![Editor standard](~/docs/extensibility/internals/media/public.gif "Public")  
Salvare, salva con nome e salvare qualsiasi gestione di comando per un editor standard  
  
 Questo processo è in dettaglio i passaggi seguenti:  
  
1.  Quando i controlli di **Salva con nome** e di **Salvare** sono selezionati, l'ambiente viene utilizzato il servizio di <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> per determinare la finestra di documento attivo e quindi gli elementi che devono essere salvati.  Una volta che la finestra di documento attivo è noto, l'ambiente viene trovato l'identificatore del puntatore e dell'elemento della gerarchia \(ID voce\) per il documento nella tabella in esecuzione il documento.  Per ulteriori informazioni, vedere [Tabella Document in esecuzione](../../extensibility/internals/running-document-table.md).  
  
     Quando il comando di **Salva tutto** è selezionato, l'ambiente utilizza le informazioni nella tabella in esecuzione di documento per compilare l'elenco di tutti gli elementi da salvare.  
  
2.  Quando la soluzione riceve una chiamata di <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> , scorre il set di elementi selezionati ossia le selezioni esposte dal servizio di <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> \).  
  
3.  In ogni elemento nella selezione, la soluzione utilizza il puntatore della gerarchia per chiamare il metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> per determinare se il comando di menu di **Save** deve essere abilitato.  Se uno o più elementi vengono modificati, il comando di **Save** è abilitato.  Se la gerarchia utilizza un editor standard, la gerarchia delega eseguire una query sullo stato cambiato l'editor chiamando il metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A> .  
  
4.  In ogni elemento selezionato è stato modificato, la soluzione utilizza il puntatore della gerarchia per chiamare il metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> sulle gerarchie appropriate.  
  
     È normale che la gerarchia utilizza un editor standard per modificare il documento.  In questo caso, l'oggetto dati del documento per l'editor deve supportare l'interfaccia di <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> .  Quando riceve una chiamata al metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> , il progetto deve notificare all'editor nel documento sta salvando chiamando il metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.SaveDocData%2A> oggetto dati del documento.  L'editor può consentire che l'ambiente gestisce la finestra di dialogo di **Salva con nome** , chiamando `Query Service` per l'interfaccia di <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> .  Viene restituito un puntatore all'interfaccia di <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> .  L'editor deve chiamare il metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A> , passando un puntatore all'implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> dell'editor l'utilizzo del parametro di `pPersistFile` .  L'ambiente esegue l'operazione di salvataggio e fornisce la finestra di dialogo di **Salva con nome** per l'editor.  Le chiamate dell'ambiente quindi nuovamente all'editor con <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>.  
  
5.  Se l'utente sta tentando di salvare un documento senza titolo \(ovvero un documento in precedenza non salvati\), quindi il comando sono effettivamente eseguito.  
  
6.  Per il comando, verrà visualizzato l'ambiente della finestra di dialogo salva con nome, richiedente all'utente un nome file.  
  
     Se il nome del file è stato modificato, pertanto la gerarchia è responsabile dell'aggiornamento le informazioni memorizzate nella cache del frame del documento chiamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A>\(VSFPROPID\_MkDocument\).  
  
 Se il comando di **Salva con nome** spostare la posizione del documento e la gerarchia è riservata all'ubicazione documenti, la gerarchia è responsabile di passare dalla proprietà della finestra di documento aperto in un'altra gerarchia.  Ad esempio, viene verificato se il progetto registra se il file è un file interno o esterno \(file esterni\) in relazione al progetto.  Utilizzare la procedura riportata di seguito per modificare la proprietà di un file al progetto file esterni.  
  
## Impostare la proprietà del file  
  
#### Per modificare la proprietà del file ai file esterni progetto  
  
1.  servizio di query per l'interfaccia di <xref:Microsoft.VisualStudio.Shell.Interop.SVsExternalFilesManager> .  
  
     Un puntatore a <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2> viene restituito.  
  
2.  Chiamare il metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2.TransferDocument%2A> \(`pszMkDocumentNew`, `punkWindowFrame`\) per trasferire il documento alla nuova gerarchia.  La gerarchia che esegue il comando chiama questo metodo.  
  
## Vedere anche  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [Apertura e salvataggio di elementi di progetto](../../extensibility/internals/opening-and-saving-project-items.md)