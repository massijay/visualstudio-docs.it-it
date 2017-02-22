---
title: "Procedura: ospitare un Editor in un altro Editor | Microsoft Docs"
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
  - "editor [Visual Studio SDK], legacy - ospitare un editor annidato"
ms.assetid: 2b0eb705-fe94-4ca8-93e0-9dbd8ce61a44
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# Procedura: ospitare un Editor in un altro Editor
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In Visual Studio è possibile ospitare l'interno di un altro editor specificando la finestra di hosting come finestra padre.  A tale scopo, impostare i parametri <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> e <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> sul frame di una finestra figlio.  
  
### Per impostare la struttura della finestra per ospitare un editor  
  
1.  Definire un editor come editor ospitato creazione di un riquadro della finestra figlio.  
  
     Questo riquadro è dove il testo dell'editor specificate.  
  
2.  Create the hosting editor using the <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> or <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A> method.  
  
3.  Impostare le proprietà di <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> e di <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> implementazione della struttura della finestra dell'editor ospitato passando queste proprietà come parametri al metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A> , rispettivamente.  
  
     Se è necessario recuperare tali parametri, passare queste proprietà al metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> .  
  
4.  chiamare il metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> per l'editor contenuto.  
  
     Verrà visualizzato l'editor nel riquadro dell'editor ospitato contenitore.  
  
## Programmazione efficiente  
 **Progettazione applicazioni** in Visual Studio Team Edition per gli architetti è un esempio di struttura della finestra editor che ospitano un altro editor.  **Progettazione applicazioni** ospitate altre finestre di progettazione nel riquadro destro.  Un pannello della finestra di progettazione \(o pagina di **Proprietà** \) per ciascuna delle finestre di progettazione contenute viene aggiunto alla struttura della finestra contenitore.