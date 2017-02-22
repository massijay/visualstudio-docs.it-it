---
title: "Procedura: collegare visualizzazioni per tenere traccia dei dati | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "editor [Visual Studio SDK], personalizzato - collegare le visualizzazioni di dati del documento"
ms.assetid: f92c0838-45be-42b8-9c55-713e9bb8df07
caps.latest.revision: 22
caps.handback.revision: 22
ms.author: "gregvanl"
manager: "ghogen"
---
# Procedura: collegare visualizzazioni per tenere traccia dei dati
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Se si dispone di una nuova visualizzazione del documento, è possibile collegarlo a un oggetto dati documento esistente.  
  
### Per determinare se è possibile collegare una visualizzazione a un oggetto dati documento esistente  
  
1.  Implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>.  
  
2.  Nell'implementazione di `IVsEditorFactory::CreateEditorInstance`, chiamare `QueryInterface` nell'oggetto dati di documento esistente quando si chiama l'IDE di `CreateEditorInstance` implementazione.  
  
     La chiamata `QueryInterface` consente di esaminare l'oggetto dati documento esistente, specificato nel `punkDocDataExisting` parametro.  
  
     Le interfacce esatte è necessario eseguire una query, tuttavia, dipende l'editor dell'apertura del documento, come descritto nel passaggio 4.  
  
3.  Se non si trovano le interfacce appropriate nell'oggetto dati documento esistente, quindi restituire un codice di errore dell'editor che indica che l'oggetto dati documento non è compatibile con l'editor.  
  
     Nell'implementazione dell'IDE di <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>, una finestra di messaggio che informa che il documento è aperto in un altro editor e viene chiesto se si desidera per chiuderla.  
  
4.  Se si chiude il documento, Visual Studio chiama il factory editor per la seconda volta. In questa chiamata, il `DocDataExisting` parametro è uguale a NULL. L'implementazione di factory dell'editor può quindi aprire l'oggetto dati di documento in un editor personalizzato.  
  
    > [!NOTE]
    >  Per determinare se è possibile utilizzare con un oggetto dati documento esistente, è possibile utilizzare anche informazioni private dell'implementazione dell'interfaccia esegue il cast di un puntatore a effettivo [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] classe di implementazione privata. Ad esempio, tutti gli editor standard implementano `IVsPersistFileFormat`, che eredita da <xref:Microsoft.VisualStudio.OLE.Interop.IPersist>. Pertanto, è possibile chiamare `QueryInterface` per <xref:Microsoft.VisualStudio.OLE.Interop.IPersist.GetClassID%2A>, e se l'ID di classe nell'oggetto dati documento esistente corrisponde l'implementazione di un ID di classe, quindi utilizzare l'oggetto dati di documento.  
  
## Programmazione efficiente  
 Quando Visual Studio chiama l'implementazione del <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> \(metodo\), che passi di nuovo un puntatore all'oggetto dati documento esistente nel `punkDocDataExisting` parametro, se presente. Esaminare l'oggetto dati documento restituito in `punkDocDataExisting` per determinare se l'oggetto dati di documento è appropriato per l'editor come descritto nella nota nel passaggio 4 della procedura in questo argomento. Se è appropriato, quindi il factory editor deve fornire una seconda vista per i dati come descritto in [Supporta più viste di documento](../extensibility/supporting-multiple-document-views.md). In caso contrario, quindi viene visualizzato un messaggio di errore appropriato.  
  
## Vedere anche  
 [Supporta più viste di documento](../extensibility/supporting-multiple-document-views.md)   
 [Dati del documento e visualizzazione di documento nell'editor personalizzati](../extensibility/document-data-and-document-view-in-custom-editors.md)