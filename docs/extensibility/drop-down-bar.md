---
title: "Barra dei menu a discesa | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "legacy [Visual Studio SDK], Editor - menu a discesa della barra"
ms.assetid: 4bb621bd-72f5-43d5-916f-9f66617da049
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Barra dei menu a discesa
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La barra a discesa viene fornita la parte superiore della finestra del codice e contiene due elenchi a discesa.  
  
## Interfacce a discesa della barra  
 In [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)], ad esempio, la barra a discesa contiene gli elenchi per le funzioni membro degli elementi di [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] e gli elementi di [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] , come mostrato nell'immagine seguente.  
  
 ![Barre a discesa](~/extensibility/media/vsdropdown_bar.gif "vsDropdown\_bar")  
barra a discesa  
  
 Quando si implementa una barra a discesa, esistono quattro interfacce di importanza primaria:  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarClient>  
  
     Implementare questa interfaccia per inserire il contenuto della barra a discesa.  Ogni combinazione a discesa può contenere testo normale o il testo effettuato \(grassetto, sottolineatura, o corsivo\), è possibile che la colorazione di carattere del testo della finestra o colorazione in grigio di carattere e facoltativamente può fornire una piccola bitmap accanto all'elemento a discesa.  Simile all'interfaccia di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> , immagini bitmap vengono forniti gli elenchi di immagini.  Ogni combinazione a discesa può avere un elenco immagini diverso; tuttavia, ogni elenco immagini deve contenere immagini della stessa altezza.  Inoltre, utilizzando il metodo di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarClient.GetComboTipText%2A> , è possibile fornire una descrizione comandi per ogni combinazione.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager>  
  
     Chiamare questa interfaccia per creare o elimina la barra a discesa per una finestra del codice.  Tale interfaccia può essere utilizzata anche per determinare se una barra a discesa è già associate a una finestra del codice chiamando il metodo di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.GetDropdownBar%2A> .  chiamata <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> per <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager> da <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar>  
  
     chiamare questa interfaccia per comunicare direttamente con la barra a discesa.  È possibile utilizzare questa interfaccia per forzare l'aggiornamento del contenuto a discesa della barra o modificare la selezione in una delle caselle di riepilogo.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManagerEvents>  
  
     Se è stato registrato `ShowDropdownBarOption` nella chiave del Registro di sistema del servizio di linguaggio, quindi gestione finestre del codice deve monitorare l'evento per sincronizzare con le preferenze utente per quanto riguarda se la barra a discesa deve essere visualizzato.  Se non si registra questa opzione nella chiave del servizio di linguaggio, quindi l'opzione per visualizzare o nascondere la barra a discesa è disabilitata nel menu di **opzioni** .  
  
## Connettere una barra a discesa a una finestra del codice  
 Per connettere una barra a discesa nella finestra del codice quando viene creata, un servizio di linguaggio deve associare alla barra a discesa quando il metodo di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A> viene chiamato.  If a call to the <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.GetDropdownBar%2A> method indicates that a drop\-down bar does not already exist, then call <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.AddDropdownBar%2A>.  Per accedere all'interfaccia di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager> , la chiamata <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> il puntatore di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> ha restituito all'implementazione di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> è stata collegata.  
  
## Vedere anche  
 [Personalizzazione di Windows di codice tramite l'API Legacy](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)   
 [Supporto per la barra di spostamento in un servizio di linguaggio Legacy](../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)