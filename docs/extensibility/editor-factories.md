---
title: "Factory editor | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "editor [Visual Studio SDK], legacy - factory editor"
ms.assetid: cf4e8164-3546-441d-b465-e8a836ae7216
caps.latest.revision: 20
caps.handback.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
---
# Factory editor
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Una factory dell'editor vengono creati gli oggetti dell'editor e li inserisce in una struttura della finestra, nota come visualizzazione fisica.  Crea i dati del documento e gli oggetti visualizzazione del documento necessari per creare editor e finestre di progettazione.  Una factory dell'editor è obbligatoria per creare editor di base di Visual Studio e qualsiasi editor standard.  Un editor personalizzato può essere opportuno essere creato con una factory dell'editor.  
  
 Creare una factory dell'editor implementando l'interfaccia di <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> .  Nell'esempio seguente viene illustrato come implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> per creare una factory dell'editor:  
  
 [!code-vb[VSSDKEditorFactories#1](../extensibility/codesnippet/VisualBasic/editor-factories_1.vb)]
 [!code-cs[VSSDKEditorFactories#1](../extensibility/codesnippet/CSharp/editor-factories_1.cs)]  
  
 Un editor viene caricato la prima volta che si apre un tipo di file gestiti dall'editor.  È possibile scegliere per aprire un editor specifico o l'editor predefinito.  Se si seleziona l'editor predefinito, l'ambiente di sviluppo \(IDE\) integrato \(IDE\) determina l'editor corretto per aprire e quindi aprirlo.  Per ulteriori informazioni, vedere [Determinazione di un File in un progetto che verrà aperto l'Editor](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md).  
  
## Registrare le factory dell'editor  
 Prima di poter utilizzare un editor creato, è innanzitutto necessario registrare le informazioni, incluse le estensioni di file che può gestire.  
  
 Se il package VS è scritto in codice gestito, è possibile utilizzare il metodo gestito <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> \(MPF\) del Framework del pacchetto per registrare la factory dell'editor dopo che il package VS viene caricato.  Se il package VS è scritto in codice non gestito, è necessario registrare la factory dell'editor tramite il servizio di <xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterEditors> .  
  
### Registrando una factory dell'editor tramite codice gestito  
 È necessario registrare la factory dell'editor nel metodo di `Initialize` del package VS.  La prima chiamata `base.Initialize`quindi chiama <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> per ogni factory dell'editor  
  
 Nel codice gestito, non è necessario annullare la registrazione di una factory dell'editor, poiché il package VS gestirà questo automaticamente.  Inoltre, se la factory dell'editor implementa <xref:System.IDisposable>, verrà automaticamente eliminato quando viene annullato la registrazione.  
  
### Registrando una factory dell'editor utilizzando codice non gestito  
 Nell'implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> per il package editor, utilizzare il metodo di `QueryService` per chiamare `SVsRegisterEditors`.  Utilizzando questo restituisce un puntatore a <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors>.  Chiamare il metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> passando l'implementazione dell'interfaccia di <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> .  È necessario mplement <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> in una classe separata.  
  
## Il processo di registrazione della factory dell'editor  
 I passaggi seguenti si verificano quando un utente apre un documento facente parte di una soluzione Microsoft Office.  
  
1.  The [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] project system calls <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>.  
  
2.  Questo metodo restituisce la factory dell'editor.  Visual Studio ritarda caricare il package editor, tuttavia, finché un sistema di progetto abbia effettivamente necessario disporre dell'editor.  
  
3.  When a project system needs the editor, Visual Studio calls <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>, a specialized method that returns both the document view and the document data objects.  
  
4.  If calls by Visual Studio to your editor factory using <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> return both a document data object and a document view object, Visual Studio then creates the document window, places the document view object in it, and makes an entry into the running document table \(RDT\) for the document data object.  
  
## Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>   
 [Tabella Document in esecuzione](../extensibility/internals/running-document-table.md)