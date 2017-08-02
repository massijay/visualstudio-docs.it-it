---
title: "Modello di un servizio di linguaggio Legacy | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "servizi di linguaggio, modello"
ms.assetid: d8ae1c0c-ee3d-4937-a581-ee78d0499793
caps.latest.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 20
---
# Modello di un servizio di linguaggio Legacy
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Un servizio di linguaggio definisce gli elementi e le funzionalità per un linguaggio specifico e viene utilizzato per specificare l'editor con informazioni specifiche del linguaggio.  Ad esempio, l'editor necessario conoscere gli elementi e le parole chiave del linguaggio per supportare la colorazione della sintassi.  
  
 Il servizio di linguaggio è strettamente con il buffer di testo gestito tramite l'editor e la visualizzazione contenente l'editor.  l'opzione di Microsoft IntelliSense **informazioni rapide** è un esempio di una funzionalità fornita da un servizio di linguaggio.  
  
## Un servizio di linguaggio minimo  
 Il servizio di linguaggio più elementare contiene i seguenti due oggetti:  
  
-   *il servizio di linguaggio* implementa l'interfaccia di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> .  Un servizio di linguaggio sono disponibili informazioni sul linguaggio, inclusi il nome, estensioni di file, amministratore di finestra del codice e colorizer.  
  
-   *il colorizer* implementa l'interfaccia di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> .  
  
 Nell'area di disegno concettuale seguente viene illustrato un modello di un servizio di linguaggio di base.  
  
 ![Rappresentazione grafica di Language Service Model](~/extensibility/media/vslanguageservicemodel.gif "vsLanguageServiceModel")  
Modello di base del servizio di linguaggio  
  
 La finestra del documento contiene *il punto di vista del documento* dell'editor, in questo caso l'editor di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .  La visualizzazione del documento e il buffer di testo sono proprietà dell'editor.  Funzionamento di questi oggetti con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tramite una finestra del documento specializzata ha chiamato *una finestra del codice*.  La finestra del codice è contenuta in un oggetto di<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> creato e controllato dall'IDE.  
  
 Quando un file con un'estensione specificata viene caricato, l'editor individuare il servizio di linguaggio associato a tale estensione e passa alla finestra del codice chiamando il metodo di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> .  Il servizio di linguaggio restituisce *un amministratore di finestra del codice*, che implementa l'interfaccia di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> .  
  
 Nella tabella seguente vengono forniti i cenni preliminari sugli oggetti nel modello.  
  
|Componente|Object|Funzione|  
|----------------|------------|--------------|  
|buffer di testo|<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>|Un flusso di testo di lettura\/scrittura Unicode.  È possibile che il testo utilizza altre codifiche.|  
|Finestra del codice|<xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>|Una finestra del documento contenente uno o più visualizzazioni di testo.  Quando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] è in modalità \(MDI\) di interfaccia a documenti multipli \(MDI\), la finestra del codice è un figlio MDI.|  
|Visualizzazione di testo|<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>|Una finestra che consente di esplorare e visualizzare il testo utilizzando la tastiera e il mouse.  Una visualizzazione di testo viene visualizzata all'utente come editor.  È possibile utilizzare le visualizzazioni di testo nelle finestre dell'editor comuni, nella finestra di output e nella finestra di controllo immediato.  Inoltre, è possibile configurare una o più visualizzazioni di testo all'interno di una finestra del codice.|  
|Amministratore del testo|Gestito dal servizio di <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> , per il quale si ottiene un puntatore a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager>|Un componente che gestisce le informazioni comuni condivise da tutti i componenti descritte in precedenza.|  
|servizio di linguaggio|Dipendente di implementazione, implementa <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>|Un oggetto che fornisce l'editor con informazioni specifiche del linguaggio come l'evidenziazione, il completamento delle istruzioni e la corrispondenza di parentesi graffe di sintassi.|  
  
## Vedere anche  
 [Dati del documento e visualizzazione di documento nell'editor personalizzati](../../extensibility/document-data-and-document-view-in-custom-editors.md)