---
title: "Decisioni di progettazione di controllo di origine | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "controllo del codice sorgente [Visual Studio SDK], decisioni di progettazione"
ms.assetid: 5f60ec1a-5a74-4362-8293-817a4dd73872
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Decisioni di progettazione di controllo di origine
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Le decisioni di progettazione devono essere considerate per i progetti per implementare il controllo del codice sorgente.  
  
## Le informazioni verranno condivisi o private?  
 La decisione di progettazione che più importante è possibile accettare è quanto le informazioni vengono ripartibili e ciò che è privato.  Ad esempio, l'elenco dei file del progetto è condiviso, ma all'interno di tale elenco di file, alcuni utenti potrebbero essere necessario disporre di file privati.  Le impostazioni del compilatore vengono condivise, ma il progetto di avvio è in genere privato.  Le impostazioni o puramente sono condivise, condiviso con un override, o puramente privato.  Da progettazione, gli elementi privati, ad esempio file delle opzioni utente della soluzione \(.suo\), non sono archiviati in [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)].  Assicurarsi di archiviare tutte le informazioni riservate in file privati del file con estensione suo, o un file che privato specifico create, ad esempio, un file csproj.user per Visual c\# o un file di vbproj.user per Visual Basic.  
  
 Questa decisione non è inclusiva e può essere eseguita elemento per elemento.  
  
## Il progetto includerà i file speciali?  
 Un altro modo per ottenere il nome e la descrizione localizzati di una proprietà è l'implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.GetLocalizedPropertyInfo%2A>.  I file speciali sono file nascosti che sono alla base dei file che sono visibili in Esplora soluzioni e nelle finestre di dialogo di archiviazione ed estrazione.  Se si utilizzano file speciali, attenersi a queste linee guida:  
  
1.  Non associare i file speciali con la radice del progetto nodo\-che è, con il file di progetto stesso.  il file di progetto deve essere un singolo file.  
  
2.  Quando i file speciali vengono aggiunti, rimossi, o vengono rinominati in un progetto, gli eventi appropriati di <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> devono essere generati con il flag impostato per indicare che i file sono file speciali.  Questi eventi vengono chiamati dall'ambiente in risposta al progetto che chiama i metodi appropriati di <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> .  
  
3.  When your project or editor calls <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> for a file, the special files associated with that file are not automatically checked out.  Passare i file speciali in con il file padre.  L'ambiente rileva la relazione tra tutti i file a cui vengono passati e in modo appropriato nascondere i file speciali nell'interfaccia utente di estrazione.  
  
## Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 [Supporto di controllo del codice sorgente](../../extensibility/internals/supporting-source-control.md)