---
title: "Aprire una finestra degli strumenti dinamica | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "finestre degli strumenti, dinamiche"
ms.assetid: 21547ba7-6e81-44df-9277-265bf34f877a
caps.latest.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 21
---
# Aprire una finestra degli strumenti dinamica
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Finestre degli strumenti sono in genere aperta da un comando in un menu o una combinazione di tasti equivalenti. In alcuni casi, tuttavia, potrebbe essere una finestra degli strumenti visualizzata ogni volta che si applica un contesto dell'interfaccia utente specifico e si chiude quando il contesto dell'interfaccia utente non è più valido. Finestre degli strumenti come questi vengono chiamate *dinamica* o *automatica visibili*.  
  
> [!NOTE]
>  Per un elenco dei contesti dell'interfaccia utente predefiniti, vedere <xref:Microsoft.VisualStudio.VSConstants.UIContext>. Per il  
  
 Se si desidera aprire una finestra degli strumenti dinamica all'avvio ed è possibile che la mancata creazione, è necessario implementare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx> interfaccia e testare le condizioni di errore di <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx.QueryShowTool%2A> \(metodo\). Affinché la shell di disporre di una finestra degli strumenti dinamica che deve essere aperte all'avvio, è necessario aggiungere il `SupportsDynamicToolOwner` valore \(impostato su 1\) per la registrazione del pacchetto. Il valore non fa parte dello standard <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>, pertanto è necessario creare un attributo personalizzato per aggiungerlo. Per ulteriori informazioni sugli attributi personalizzati, vedere [Uso di un attributo di registrazione personalizzato per registrare un'estensione](/visual-cpp/misc/using-a-custom-registration-attribute-to-register-an-extension).  
  
 Utilizzare <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> per aprire una finestra degli strumenti. La finestra degli strumenti viene creata in base alle esigenze.  
  
> [!NOTE]
>  Una finestra degli strumenti dinamica può essere chiusa dall'utente. Se si desidera creare un comando di menu per l'utente può essere riaperto la finestra degli strumenti, attivare il comando di menu nello stesso contesto dell'interfaccia utente che apre la finestra degli strumenti e disabilitata in caso contrario.  
  
### Per aprire una finestra degli strumenti dinamica  
  
1.  Creare un progetto VSIX denominato **DynamicToolWindow** e aggiungere un modello di elemento della finestra strumento denominato **DynamicWindowPane.cs**. Per altre informazioni, vedere [Creazione di un'estensione con una finestra degli strumenti](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
2.  Nel file DynamicWindowPanePackage.cs, individuare la dichiarazione di DynamicWindowPanePackage. Aggiungere il <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> e gli attributi T:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute per registrare la finestra degli strumenti.  
  
    ```vb  
    [[ProvideToolWindow(typeof(DynamicWindowPane)] [ProvideToolWindowVisibility(typeof(DynamicWindowPane), VSConstants.UICONTEXT.SolutionExists_string)] [PackageRegistration(UseManagedResourcesOnly = true)] [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About [ProvideMenuResource("Menus.ctmenu", 1)] [ProvideToolWindow(typeof(DynamicToolWindow.DynamicWindowPane))] [Guid(DynamicWindowPanePackageGuids.PackageGuidString)] public sealed class DynamicWindowPanePackage : Package {. . .}  
    ```  
  
     Verrà registrato la finestra degli strumenti denominata DynamicWindowPane come finestra temporanea che non è persistente quando viene chiuso e riaperto Visual Studio. Viene aperto DynamicWindowPane ogni volta che <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_string> Applica e chiuso in caso contrario.  
  
3.  Compilare il progetto e avviare il debug. L'istanza sperimentale dovrebbe apparire. È non verrà visualizzata la finestra dello strumento.  
  
4.  Aprire un progetto nell'istanza sperimentale. La finestra dello strumento.