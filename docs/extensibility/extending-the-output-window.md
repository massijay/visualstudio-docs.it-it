---
title: "Estendere la finestra di Output | Microsoft Docs"
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
  - "Finestra di output sulla finestra di Output"
ms.assetid: b02fa88c-f92a-4ff6-ba5f-2eb4d48a643a
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# Estendere la finestra di Output
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Il **Output** finestra è una serie di riquadri di testo di lettura\/scrittura. Visual Studio include questi riquadri predefiniti: **compilare**, comunicare i messaggi relativi alle compilazioni, nella quale i progetti e **Generale**, in cui [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] comunica i messaggi sull'IDE di. Progetti di ottenere un riferimento a di **compilare** riquadro automaticamente tramita il <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> metodi di interfaccia e Visual Studio offre accesso diretto al **Generale** riquadro tramite il <xref:Microsoft.VisualStudio.Shell.Interop.SVsGeneralOutputWindowPane> servizio. Oltre ai riquadri predefiniti, è possibile creare e gestire i proprio riquadri personalizzati.  
  
 È possibile controllare il **Output** finestra direttamente tramita il <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> interfacce. Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> interfaccia, che viene offerto il <xref:Microsoft.VisualStudio.Shell.Interop.SVsOutputWindow> del servizio, definisce i metodi per creare, recuperare e distruzione **Output** riquadri della finestra. Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> interfaccia definisce i metodi per la visualizzazione dei riquadri, nascondere riquadri e la modifica del testo. Un modo alternativo per il controllo di **Output** finestra è tramite il <xref:EnvDTE.OutputWindow> e <xref:EnvDTE.OutputWindowPane> gli oggetti nel modello a oggetti di automazione di Visual Studio. Questi oggetti includono quasi tutte le funzionalità di <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> interfacce. Inoltre, il <xref:EnvDTE.OutputWindow> e <xref:EnvDTE.OutputWindowPane> oggetti aggiungono alcune funzionalità di livello superiore per rendere più semplice enumerare il **Output** riquadri della finestra e per recuperare il testo dai riquadri.  
  
## Creazione di un'estensione che utilizza il riquadro di Output  
 È possibile creare un'estensione che esercitano diversi aspetti del riquadro di Output.  
  
1.  Creare un progetto VSIX denominato `TestOutput` con un comando di menu denominato **TestOutput**. Per altre informazioni, vedere [Creazione di un'estensione con un comando di Menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2.  Aggiungere i riferimenti seguenti:  
  
    1.  EnvDTE  
  
    2.  EnvDTE80  
  
3.  In TestOutput.cs, aggiungere la seguente istruzione using:  
  
    ```f#  
    using EnvDTE; using EnvDTE80;  
    ```  
  
4.  In TestOutput.cs, eliminare il metodo ShowMessageBox. Aggiungere lo stub del metodo seguente:  
  
    ```c#  
    private void OutputCommandHandler(object sender, EventArgs e) { }  
    ```  
  
5.  Nel costruttore TestOutput, modificare il gestore comando per OutputCommandHandler. Questa è la parte che aggiunge i comandi:  
  
    ```c#  
    OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService; if (commandService != null) { CommandID menuCommandID = new CommandID(MenuGroup, CommandId); EventHandler eventHandler = OutputCommandHandler; MenuCommand menuItem = new MenuCommand(eventHandler, menuCommandID); commandService.AddCommand(menuItem); }  
    ```  
  
6.  Nelle sezioni seguenti sono illustrano diversi modi di affrontare il riquadro di Output diversi metodi. È possibile chiamare questi metodi al corpo del metodo OutputCommandHandler\(\). Ad esempio, il codice seguente aggiunge il metodo CreatePane\(\) descritto nella sezione successiva.  
  
    ```c#  
    private void OutputCommandHandler(object sender, EventArgs e) { CreatePane(new Guid(), "Created Pane", true, false); }  
    ```  
  
## Creazione di una finestra di Output con IVsOutputWindow  
 In questo esempio viene illustrato come creare un nuovo **Output** riquadro della finestra utilizzando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> interfaccia.  
  
```c#  
void CreatePane(Guid paneGuid, string title, bool visible, bool clearWithSolution) { IVsOutputWindow output = (IVsOutputWindow)GetService(typeof(SVsOutputWindow)); IVsOutputWindowPane pane; // Create a new pane. output.CreatePane( ref paneGuid, title, Convert.ToInt32(visible), Convert.ToInt32(clearWithSolution)); // Retrieve the new pane. output.GetPane(ref paneGuid, out pane); pane.OutputString("This is the Created Pane \n"); }  
```  
  
 Se si aggiunge questo metodo per l'estensione fornita nella sezione precedente, quando si fa clic il **richiamare TestOutput** comando verrà visualizzato il **Output** finestra con un'intestazione che indica che **Mostra output di: CreatedPane** e le parole **questo è il riquadro creato** nel riquadro stesso.  
  
## Creazione di una finestra di Output con OutputWindow  
 In questo esempio viene illustrato come creare un **Output** riquadro della finestra utilizzando il <xref:EnvDTE.OutputWindow> oggetto.  
  
```c#  
void CreatePane(string title) { DTE2 dte = (DTE2)GetService(typeof(DTE)); OutputWindowPanes panes = dte.ToolWindows.OutputWindow.OutputWindowPanes; try { // If the pane exists already, write to it. panes.Item(title); } catch (ArgumentException) { // Create a new pane and write to it. return panes.Add(title); } }  
```  
  
 Sebbene il <xref:EnvDTE.OutputWindowPanes> raccolta consente di recuperare un **Output** riquadro mediante il titolo, i titoli di riquadro non sono necessariamente essere univoco. Quando si dubito l'univocità di un titolo, utilizzare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow.GetPane%2A> per recuperare il riquadro corretto tramite il relativo GUID.  
  
 Se si aggiunge questo metodo per l'estensione fornita nella sezione precedente, quando si fa clic il **richiamare TestOutput** comando si verrà visualizzata la finestra di Output con un'intestazione che indica che **Mostra output di: DTEPane** e le parole **aggiunto riquadro DTE** nel riquadro stesso.  
  
## Eliminazione di una finestra di Output  
 In questo esempio viene illustrato come eliminare un **Output** riquadro della finestra.  
  
```c#  
void DeletePane(Guid paneGuid) { IVsOutputWindow output = (IVsOutputWindow)ServiceProvider.GetService(typeof(SVsOutputWindow)); IVsOutputWindowPane pane; output.GetPane(ref paneGuid, out pane); if (pane == null) { CreatePane(paneGuid, "New Pane\n", true, true); } else { output.DeletePane(ref paneGuid); } }  
```  
  
 Se si aggiunge questo metodo per l'estensione fornita nella sezione precedente, quando si fa clic il **richiamare TestOutput** comando si verrà visualizzata la finestra di Output con un'intestazione che indica che **Mostra output di: nuovo riquadro** e le parole **aggiunto riquadro creato** nel riquadro stesso. Se si sceglie il **richiamare TestOutput** comando nuovamente, il riquadro viene eliminato.  
  
## Ottenere il riquadro Generale della finestra di Output  
 In questo esempio viene illustrato come ottenere l'oggetto incorporato **Generale** del riquadro di **Output** finestra.  
  
```c#  
void GetGeneralPane() { return (IVsOutputWindowPane)GetService( typeof(SVsGeneralOutputWindowPane)); }  
```  
  
 Se si aggiunge questo metodo per l'estensione fornita nella sezione precedente, quando si fa clic il **richiamare TestOutput** comando verificare che il **Output** finestra vengono visualizzate le parole **riquadro trovato generale** nel riquadro.  
  
## Recupero riquadro compilazione della finestra di Output  
 In questo esempio viene illustrato come individuare il riquadro di compilazione e la scrittura. Poiché il riquadro di compilazione non è attivato per impostazione predefinita, attiva anche.  
  
```c#  
void OutputTaskItemStringExExample(string buildMessage) { EnvDTE80.DTE2 dte = (EnvDTE80.DTE2)ServiceProvider.GetService(typeof(EnvDTE.DTE)); EnvDTE.OutputWindowPanes panes = dte.ToolWindows.OutputWindow.OutputWindowPanes; foreach (EnvDTE.OutputWindowPane pane in panes) { if (pane.Name.Contains("Build")) { pane.OutputString(buildMessage + "\n"); pane.Activate(); return; } } }  
```