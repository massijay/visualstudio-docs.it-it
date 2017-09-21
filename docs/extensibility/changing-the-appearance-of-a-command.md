---
title: "Modifica dell&#39;aspetto di un comando | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "comandi, modifica dell'aspetto"
  - "comandi di menu, modifica dell'aspetto"
  - "menu, modifica dell'aspetto di comando"
ms.assetid: da2474fa-f92d-4e9e-b8bf-67c61bf249c2
caps.latest.revision: 23
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 23
---
# Modifica dell&#39;aspetto di un comando
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile fornire feedback all'utente tramite la modifica dell'aspetto di un comando. Ad esempio, si consiglia un comando per un aspetto diverso quando non è disponibile. È possibile rendere i comandi disponibili o non è disponibile, nascondere o visualizzarli, o verificare o deselezionarle dal menu.  
  
 Per modificare l'aspetto di un comando, eseguire una delle azioni seguenti:  
  
-   Specifica i flag appropriati nella definizione di comando nel file tabella di comando.  
  
-   Utilizzare il <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> servizio.  
  
-   Implementare il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> l'interfaccia e modificare gli oggetti comando non elaborati.  
  
 La procedura seguente viene illustrato come trovare e aggiornare l'aspetto di un comando tramite il Framework di pacchetto gestito \(MPF\).  
  
### Per modificare l'aspetto di un comando di menu  
  
1.  Seguire le istruzioni in [Modifica del testo di un comando di Menu](../extensibility/changing-the-text-of-a-menu-command.md) per creare una voce di menu denominato `New Text`.  
  
2.  Nel file ChangeMenuText.cs, aggiungere la seguente istruzione using:  
  
    ```c#  
    using System.Security.Permissions;  
    ```  
  
3.  Nel file ChangeMenuTextPackageGuids.cs, aggiungere la riga seguente:  
  
    ```c#  
    public const string guidChangeMenuTextPackageCmdSet= "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file  
    ```  
  
4.  Nel file ChangeMenuText.cs, sostituire il codice nel metodo ShowMessageBox con il codice seguente:  
  
    ```c#  
    private void ShowMessageBox(object sender, EventArgs e)  
    {  
        var command = sender as OleMenuCommand;  
        if (command.Text == "New Text")  
            ChangeMyCommand(command.CommandID.ID, false);}  
    }  
    ```  
  
5.  Il comando che si desidera aggiornare da ottenere il <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> dell'oggetto e quindi impostare le proprietà appropriate sull'oggetto command. Il metodo seguente, ad esempio, rende il comando specificato da un comando VSPackage impostare disponibile o non disponibile. Il codice seguente effettua il voce di menu denominata `New Text` disponibile dopo che è stato fatto clic.  
  
    ```c#  
    public bool ChangeMyCommand(int cmdID, bool enableCmd)  
    {  
        bool cmdUpdated = false;  
        var mcs = this.ServiceProvider.GetService(typeof(IMenuCommandService))  
            as OleMenuCommandService;  
        var newCmdID = new CommandID(new Guid(ChangeMenuTextPackageGuids.guidChangeMenuTextPackageCmdSet), cmdID);  
        MenuCommand mc = mcs.FindCommand(newCmdID);  
        if (mc != null)  
        {  
            mc.Enabled = enableCmd;  
            cmdUpdated = true;  
        }  
        return cmdUpdated;    }  
    }  
    ```  
  
6.  Compilare il progetto e avviare il debug. L'istanza sperimentale di Visual Studio dovrebbe apparire.  
  
7.  Nel **strumenti** menu, fare clic su di **richiamare ChangeMenuText** comando. A questo punto è il nome del comando **richiamare ChangeMenuText**, in modo che il gestore del comando non chiama ChangeMyCommand\(\).  
  
8.  Nel **strumenti** menu dovrebbe **nuovo testo**. Fare clic su **nuovo testo**. Il comando dovrebbe ora essere disabilitato.  
  
## Vedere anche  
 [I comandi, menu e barre degli strumenti](../extensibility/internals/commands-menus-and-toolbars.md)   
 [Come package VS aggiungere elementi dell'interfaccia utente](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Estensione menu e comandi](../extensibility/extending-menus-and-commands.md)   
 [Tabella di comandi di Visual Studio \(. File Vsct\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)