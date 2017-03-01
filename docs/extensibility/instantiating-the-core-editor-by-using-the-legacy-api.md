---
title: Creazione di Editor di componenti di base tramite l&quot;API Legacy | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - instantiating editor
ms.assetid: dda23b18-96ef-43c6-b0dc-06d15cbe5cbb
caps.latest.revision: 29
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
ms.openlocfilehash: e18118d73d46aeee7612eb7dff64f778726778f0
ms.lasthandoff: 02/22/2017

---
# <a name="instantiating-the-core-editor-by-using-the-legacy-api"></a>Creazione di Editor di componenti di base tramite l'API Legacy
L'editor è responsabile per la modifica di funzioni come l'inserimento, eliminazione, copia e Incolla di testo. Combina queste funzioni con quelli forniti da servizi di linguaggio, ad esempio di colorazione di testo, il rientro e il completamento delle istruzioni IntelliSense.  
  
 È possibile creare un'istanza dell'editor di componenti di base in uno dei tre modi:  
  
-   Creare in modo esplicito un'istanza di base editor in una finestra.  
  
-   Fornire una factory editor che restituisce un'istanza dell'editor di componenti di base  
  
-   Aprire un file dalla gerarchia del progetto.  
  
 Nelle sezioni seguenti viene illustrato come utilizzare l'API legacy per creare un'istanza di editor.  
  
## <a name="explicitly-opening-a-core-editor-instance"></a>Apertura in modo esplicito un'istanza dell'Editor di base  
 Quando si ottiene in modo esplicito un'istanza dell'editor di componenti di base:  
  
-   Ottenere un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>per contenere l'oggetto dati di documento in fase di modifica.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>  
  
-   Creare una rappresentazione orientato alla riga dell'oggetto dati documento creando un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>interfaccia il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>interfaccia.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>  
  
-   Impostare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>come l'oggetto di un'istanza dell'implementazione predefinita di dati del documento di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>interfaccia, utilizzando il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow.SetBuffer%2A>(metodo).</xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow.SetBuffer%2A> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>  
  
     Host di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>dell'istanza in un <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>interfaccia utilizzando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateToolWindow%2A>(metodo).</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateToolWindow%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>  
  
 A questo punto, la visualizzazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>interfaccia fornisce una finestra che contiene un'istanza dell'editor di componenti di base.</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>  
  
 Tuttavia, questo non è un'istanza molto utile, perché non dispone di tasti di scelta rapida o accedere alle funzionalità avanzate. Per ottenere l'accesso alle funzionalità avanzate e tasti di scelta rapida:  
  
-   Utilizzare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A>metodo per associare un servizio di linguaggio e l'oggetto dati di documento che utilizza l'editor.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A>  
  
-   Creare i proprio tasti di scelta rapida oppure utilizzare l'impostazione predefinita impostando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>oggetti visualizzare le proprietà.</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> A tale scopo, chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetGuidProperty%2A>metodo con la <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>proprietà.</xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> </xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetGuidProperty%2A>  
  
     Per ottenere e utilizzare i tasti di scelta rapida non standard, generarli utilizzando il file vsct. Per ulteriori informazioni, vedere [tabella di comando Visual Studio (. File Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
## <a name="how-to-use-an-editor-factory-to-obtain-the-core-editor"></a>Procedura: utilizzare una factory Editor per ottenere l'Editor di componenti di base  
 Quando si implementa un editor di componenti di base con una factory editor mediante il <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>(metodo), tutti i passaggi descritti nella sezione precedente per ospitare in modo esplicito un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>utilizzando un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>dell'oggetto dati del documento, in un <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>oggetto.</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> </xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>  
  
 Per visualizzare il testo, ottenere un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>interfaccia il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>oggetto e chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>(metodo).</xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>  
  
 Per fornire un servizio di linguaggio nell'editor, chiamare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A>metodo all'interno di <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>(metodo).</xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A>  
  
 Per ottenere predefinito tasti di scelta rapida, a differenza della sezione precedente, utilizzare il contesto del comando restituito dal <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>metodo quando l'editor di componenti di base da ottenere il <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>(metodo).</xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>  
  
 Se il <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>metodo restituisce lo stesso GUID di comando come editor di testo, l'istanza dell'editor di componenti di base ottiene automaticamente il valore predefinito tasti di scelta rapida.</xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>  
  
 Per informazioni generali, vedere [procedura dettagliata: creazione di un Editor di componenti di base e la registrazione di un tipo di File Editor](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Nell'Editor di componenti di base](../extensibility/inside-the-core-editor.md)   
 [Apertura e salvataggio di elementi di progetto](../extensibility/internals/opening-and-saving-project-items.md)   
 [Procedura dettagliata: Creazione di un Editor di componenti di base e la registrazione di un tipo di File dell'Editor](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)
