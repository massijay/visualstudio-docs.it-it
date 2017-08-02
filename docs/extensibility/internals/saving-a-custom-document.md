---
title: "Salvare un documento personalizzato | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "persistenza, il salvataggio di documenti personalizzati"
  - "progetti [Visual Studio SDK], salvataggio di documenti personalizzati"
  - "editor [Visual Studio SDK], salvataggio di documenti personalizzati"
ms.assetid: 040b36d6-1f0a-4579-971c-40fbb46ade1d
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Salvare un documento personalizzato
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

L'handle di ambiente **Save**, **Save As**e controlli di **Save All** .  Quando un utente fa clic su **Salvare**, **Salva con nome**, **o salvare tutti** il menu File o chiude la soluzione, con conseguente salva tutti, il seguente processo si verifica.  
  
 ![Salvataggio editor customer](~/extensibility/internals/media/private.gif "Private")  
Salvare, salva con nome e salvare qualsiasi gestione di comando per un editor personalizzato  
  
 Questo processo è in dettaglio i passaggi seguenti:  
  
1.  Per i controlli di **Salva con nome** e di **Salvare** , l'ambiente viene utilizzato il servizio di <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> per determinare la finestra di documento attivo e quindi gli elementi che devono essere salvati.  Una volta che la finestra di documento attivo è noto, l'ambiente viene trovato l'identificatore del puntatore e dell'elemento della gerarchia \(ID voce\) per il documento nella tabella in esecuzione il documento.  Per ulteriori informazioni, vedere [Tabella Document in esecuzione](../../extensibility/internals/running-document-table.md).  
  
     Di salvataggio qualsiasi comando, l'ambiente utilizza le informazioni nella tabella in esecuzione di documento per compilare l'elenco di tutti gli elementi da salvare.  
  
2.  Quando la soluzione riceve una chiamata di <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> , scorre il set di elementi selezionati ossia le selezioni esposte dal servizio di <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> \).  
  
3.  In ogni elemento nella selezione, la soluzione utilizza il puntatore della gerarchia per chiamare il metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> per determinare se il comando di menu di salvataggio deve essere abilitato.  Se uno o più elementi vengono modificati, il comando salva è abilitato.  Se la gerarchia utilizza un editor standard, la gerarchia delega eseguire una query sullo stato cambiato l'editor chiamando il metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A> .  
  
4.  In ogni elemento selezionato è stato modificato, la soluzione utilizza il puntatore della gerarchia per chiamare il metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> sulle gerarchie appropriate.  
  
     Nel caso di un editor personalizzato, la comunicazione tra l'oggetto dati del documento e il progetto è privata.  Pertanto, tutte le problematiche particolari di persistenza vengono mantenute tra questi due oggetti.  
  
    > [!NOTE]
    >  Se si distribuisce della persistenza, è necessario assicurarsi di chiamare il metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> per risparmiare tempo.  Controlli di questo metodo per assicurarsi che sia protetto salvare il file, il file non sia in sola lettura\).  
  
## Vedere anche  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [Apertura e salvataggio di elementi di progetto](../../extensibility/internals/opening-and-saving-project-items.md)