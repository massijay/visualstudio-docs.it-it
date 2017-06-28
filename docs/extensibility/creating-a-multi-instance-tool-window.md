---
title: "Creazione di una finestra degli strumenti multi-istanza | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "più"
  - "finestre degli strumenti"
ms.assetid: 4a7872f1-acc9-4f43-8932-5a526b36adea
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Creazione di una finestra degli strumenti multi-istanza
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile programmare una finestra degli strumenti in modo che più istanze possono essere aperte contemporaneamente. Per impostazione predefinita, le finestre degli strumenti possono essere solo un'istanza aperto.  
  
 Quando si utilizza una finestra degli strumenti a più istanze, è possibile visualizzare diversi correlate fonti di informazioni nello stesso momento. Ad esempio, è possibile inserire una multi\-riga <xref:System.Windows.Forms.TextBox> controllare in una finestra degli strumenti multi\-istanza in modo che siano disponibili contemporaneamente diversi frammenti di codice durante una sessione di programmazione. Inoltre, ad esempio, è possibile inserire un <xref:System.Windows.Forms.DataGrid> casella controllo e un elenco a discesa in una finestra degli strumenti multi\-istanza in modo da diverse origini dati in tempo reale possono essere rilevate contemporaneamente.  
  
## Creazione di una finestra degli strumenti di base \(a istanza singola\)  
  
1.  Creare un progetto denominato **MultiInstanceToolWindow** utilizzando il modello di progetto VSIX e aggiungere un modello di elemento della finestra degli strumenti personalizzata denominato **MIToolWindow**.  
  
    > [!NOTE]
    >  Per ulteriori informazioni sulla creazione di un'estensione con una finestra degli strumenti, vedere [Creazione di un'estensione con una finestra degli strumenti](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
## Eseguendo multi\-un'istanza di strumento  
  
1.  Aprire il **MIToolWindowPackage.cs** file e individuare il `ProvideToolWindow` attributo. e `MultiInstances=true` parametro, come illustrato nell'esempio seguente.  
  
    ```c#  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
        [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About  
        [ProvideMenuResource("Menus.ctmenu", 1)]  
        [ProvideToolWindow(typeof(MultiInstanceToolWindow.MIToolWindow), MultiInstances = true)]  
        [Guid(MIToolWindowPackageGuids.PackageGuidString)]  
        public sealed class MIToolWindowPackage : Package  
    {. . .}  
    ```  
  
2.  Nel file MIToolWindowCommand.cs, individuare il metodo ShowToolWindos\(\). In questo metodo, chiamare il <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> metodo e impostare il relativo `create` flag `false` in modo che eseguirà un'iterazione istanze esistenti di finestra strumento finché non è disponibile un `id` viene trovato.  
  
3.  Per creare un'istanza dello strumento, chiamare il <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> metodo e impostare il relativo `id` su un valore disponibile e il relativo `create` flag `true`.  
  
     Per impostazione predefinita, il valore del `id` parametro il <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> metodo `0`. In questo modo una finestra degli strumenti a istanza singola. Per più di un'istanza deve essere ospitato, ogni istanza deve avere un proprio univoco `id`.  
  
4.  Chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> metodo il <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> oggetto restituito dalla <xref:Microsoft.VisualStudio.Shell.ToolWindowPane.Frame%2A> proprietà dell'istanza di finestra dello strumento.  
  
5.  Per impostazione predefinita, il `ShowToolWindow` metodo creata dal modello di elemento di finestra strumento crea una finestra degli strumenti a istanza singola. Nell'esempio seguente viene illustrato come modificare il `ShowToolWindow` metodo per creare più istanze.  
  
    ```c#  
    private void ShowToolWindow(object sender, EventArgs e)  
    {  
        for (int i = 0; i < 10; i++)  
        {  
            ToolWindowPane window = this.package.FindToolWindow(typeof(MIToolWindow), i, false);  
            if (window == null)  
            {  
                // Create the window with the first free ID.   
                window = (ToolWindowPane)this.package.FindToolWindow(typeof(MIToolWindow), i, true);  
                if ((null == window) || (null == window.Frame))  
                {  
                    throw new NotSupportedException("Cannot create tool window");  
                }  
  
            IVsWindowFrame windowFrame = (IVsWindowFrame)window.Frame;  
            Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(windowFrame.Show());  
            break;  
            }  
        }  
    }  
    ```